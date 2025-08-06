# UdaPlay AI Agent - Hybrid RAG Architecture

## Intelligent Knowledge Routing System

```mermaid
graph TB
    subgraph "User Interface"
        USER[User Query]
        RESPONSE[Structured Response]
    end
    
    subgraph "State Machine Core"
        ENTRY[Entry State]
        MSG_PREP[Message Preparation]
        LLM_PROC[LLM Processing]
        TOOL_EXEC[Tool Execution]
        END_STATE[End State]
        
        ENTRY --> MSG_PREP
        MSG_PREP --> LLM_PROC
        LLM_PROC --> TOOL_EXEC
        TOOL_EXEC --> END_STATE
        TOOL_EXEC --> MSG_PREP
    end
    
    subgraph "Intelligence Layer"
        ROUTER[Query Router]
        CONTEXT[Context Manager]
        MEMORY[Conversation Memory]
        
        ROUTER --> CONTEXT
        CONTEXT --> MEMORY
    end
    
    subgraph "Knowledge Sources"
        direction LR
        
        subgraph "Local RAG System"
            CHROMA[(ChromaDB)]
            EMBEDDINGS[Vector Embeddings]
            SEMANTIC[Semantic Search]
            
            CHROMA --> EMBEDDINGS
            EMBEDDINGS --> SEMANTIC
        end
        
        subgraph "Web Search System"
            TAVILY[Tavily API]
            WEB_SEARCH[Real-time Search]
            LIVE_DATA[Live Information]
            
            TAVILY --> WEB_SEARCH
            WEB_SEARCH --> LIVE_DATA
        end
    end
    
    subgraph "Data Sources"
        GAME_DB[15 Game Files]
        JSON_META[JSON Metadata]
        GAME_INFO[Game Information]
        
        GAME_DB --> JSON_META
        JSON_META --> GAME_INFO
    end
    
    USER --> ENTRY
    LLM_PROC --> ROUTER
    
    ROUTER --> SEMANTIC: Local Knowledge
    ROUTER --> WEB_SEARCH: External Info
    
    GAME_INFO --> CHROMA
    SEMANTIC --> CONTEXT
    LIVE_DATA --> CONTEXT
    
    CONTEXT --> RESPONSE
    END_STATE --> RESPONSE
    RESPONSE --> USER
    
    style ROUTER fill:#ff9800
    style SEMANTIC fill:#2196f3
    style WEB_SEARCH fill:#4caf50
    style CHROMA fill:#9c27b0
    style TAVILY fill:#f44336
```

## Query Processing Decision Tree

```mermaid
flowchart TD
    START([User Query]) --> ANALYZE{Analyze Query Type}
    
    ANALYZE -->|Gaming Database| LOCAL[Local RAG Search]
    ANALYZE -->|Current Events| WEB[Web Search]
    ANALYZE -->|Complex/Hybrid| HYBRID[Hybrid Search]
    
    LOCAL --> CHROMA_SEARCH[ChromaDB Vector Search]
    CHROMA_SEARCH --> EMBED[Generate Embeddings]
    EMBED --> SIMILARITY[Calculate Similarity]
    SIMILARITY --> LOCAL_RESULTS[Return Local Results]
    
    WEB --> TAVILY_API[Tavily API Call]
    TAVILY_API --> WEB_QUERY[Execute Web Search]
    WEB_QUERY --> WEB_RESULTS[Return Web Results]
    
    HYBRID --> BOTH[Execute Both Searches]
    BOTH --> MERGE[Merge Results]
    MERGE --> RANK[Rank by Relevance]
    RANK --> HYBRID_RESULTS[Return Hybrid Results]
    
    LOCAL_RESULTS --> SYNTHESIZE[Synthesize Response]
    WEB_RESULTS --> SYNTHESIZE
    HYBRID_RESULTS --> SYNTHESIZE
    
    SYNTHESIZE --> JSON_FORMAT[Format as JSON]
    JSON_FORMAT --> MEMORY_UPDATE[Update Conversation Memory]
    MEMORY_UPDATE --> FINAL([Final Response])
    
    style ANALYZE fill:#ffeb3b
    style LOCAL fill:#e3f2fd
    style WEB fill:#e8f5e8
    style HYBRID fill:#fff3e0
```

## State Machine Workflow

```mermaid
stateDiagram-v2
    [*] --> Entry
    Entry --> MessagePreparation: Initialize
    
    state MessagePreparation {
        [*] --> ValidateInput
        ValidateInput --> PrepareContext
        PrepareContext --> [*]
    }
    
    MessagePreparation --> LLMProcessing: Context Ready
    
    state LLMProcessing {
        [*] --> RouteQuery
        RouteQuery --> LocalSearch: Gaming Question
        RouteQuery --> WebSearch: Current Events
        RouteQuery --> HybridSearch: Complex Query
        
        LocalSearch --> [*]
        WebSearch --> [*]
        HybridSearch --> [*]
    }
    
    LLMProcessing --> ToolExecution: Search Route Determined
    
    state ToolExecution {
        [*] --> ExecuteSearch
        ExecuteSearch --> ProcessResults
        ProcessResults --> UpdateMemory
        UpdateMemory --> [*]
    }
    
    ToolExecution --> End: Results Ready
    ToolExecution --> MessagePreparation: Need More Info
    
    End --> [*]
    
    note right of RouteQuery
        Intelligence routing based on
        query content and context
    end note
    
    note right of UpdateMemory
        Persistent conversation
        memory across sessions
    end note
```
