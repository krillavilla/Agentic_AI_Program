# AgentsVille Trip Planner - Advanced AI Architecture

## Chain-of-Thought & ReAct Processing Flow

```mermaid
graph TB
    subgraph "Input Layer"
        USER_PROFILE[Traveler Profile]
        BUDGET[Budget Constraints]
        DURATION[Trip Duration]
        PREFERENCES[Personal Preferences]
    end
    
    subgraph "Data Integration Layer"
        WEATHER_API[Mock Weather Service]
        ACTIVITY_DB[Activity Database]
        INTEREST_ENGINE[Interest Matching]
        
        WEATHER_API --> WEATHER_DATA[Weather Forecasts]
        ACTIVITY_DB --> ACTIVITY_DATA[Available Activities]
        INTEREST_ENGINE --> MATCH_DATA[Interest Scores]
    end
    
    subgraph "Chain-of-Thought Engine"
        direction TB
        COT_STEP1[Step 1: Weather Analysis]
        COT_STEP2[Step 2: Activity Matching]
        COT_STEP3[Step 3: Budget Optimization]
        COT_STEP4[Step 4: Itinerary Generation]
        
        COT_STEP1 --> COT_STEP2
        COT_STEP2 --> COT_STEP3
        COT_STEP3 --> COT_STEP4
    end
    
    subgraph "ReAct Feedback Loop"
        direction LR
        THOUGHT[Thought Process]
        ACTION[Take Action]
        OBSERVATION[Observe Results]
        REVISION[Revise Plan]
        
        THOUGHT --> ACTION
        ACTION --> OBSERVATION
        OBSERVATION --> REVISION
        REVISION --> THOUGHT
    end
    
    subgraph "Output Generation"
        ITINERARY[Structured Itinerary]
        NARRATIVE[Engaging Narrative]
        VALIDATION[Budget Validation]
        RECOMMENDATIONS[Activity Recommendations]
    end
    
    USER_PROFILE --> COT_STEP1
    BUDGET --> COT_STEP3
    DURATION --> COT_STEP4
    PREFERENCES --> COT_STEP2
    
    WEATHER_DATA --> COT_STEP1
    ACTIVITY_DATA --> COT_STEP2
    MATCH_DATA --> COT_STEP2
    
    COT_STEP4 --> THOUGHT
    REVISION --> ITINERARY
    
    ITINERARY --> NARRATIVE
    ITINERARY --> VALIDATION
    ITINERARY --> RECOMMENDATIONS
    
    style COT_STEP1 fill:#e3f2fd
    style COT_STEP2 fill:#f3e5f5
    style COT_STEP3 fill:#e8f5e8
    style COT_STEP4 fill:#fff3e0
    style THOUGHT fill:#ffeb3b
    style ACTION fill:#ff9800
    style OBSERVATION fill:#4caf50
    style REVISION fill:#9c27b0
```

## Intelligent Planning Algorithm

```mermaid
flowchart TD
    START([Trip Request]) --> VALIDATE{Validate Input}
    
    VALIDATE -->|Valid| WEATHER_CHECK[Check Weather Forecast]
    VALIDATE -->|Invalid| ERROR[Return Error]
    
    WEATHER_CHECK --> OUTDOOR_FILTER{Filter Activities}
    OUTDOOR_FILTER -->|Good Weather| INCLUDE_OUTDOOR[Include Outdoor Activities]
    OUTDOOR_FILTER -->|Bad Weather| EXCLUDE_OUTDOOR[Exclude Outdoor Activities]
    
    INCLUDE_OUTDOOR --> INTEREST_MATCH[Match User Interests]
    EXCLUDE_OUTDOOR --> INTEREST_MATCH
    
    INTEREST_MATCH --> SCORE_ACTIVITIES[Score Activity Relevance]
    SCORE_ACTIVITIES --> BUDGET_CHECK{Within Budget?}
    
    BUDGET_CHECK -->|Yes| ADD_ACTIVITY[Add to Itinerary]
    BUDGET_CHECK -->|No| FIND_ALTERNATIVE[Find Cheaper Alternative]
    
    FIND_ALTERNATIVE --> ALTERNATIVE_CHECK{Alternative Found?}
    ALTERNATIVE_CHECK -->|Yes| ADD_ACTIVITY
    ALTERNATIVE_CHECK -->|No| SKIP_ACTIVITY[Skip Activity]
    
    ADD_ACTIVITY --> MORE_ACTIVITIES{More Time/Budget?}
    SKIP_ACTIVITY --> MORE_ACTIVITIES
    
    MORE_ACTIVITIES -->|Yes| INTEREST_MATCH
    MORE_ACTIVITIES -->|No| GENERATE_ITINERARY[Generate Final Itinerary]
    
    GENERATE_ITINERARY --> NARRATIVE_CREATE[Create Narrative Summary]
    NARRATIVE_CREATE --> SELF_EVALUATE[Self-Evaluation]
    
    SELF_EVALUATE --> QUALITY_CHECK{Quality Acceptable?}
    QUALITY_CHECK -->|No| REVISE_PLAN[Revise Plan]
    QUALITY_CHECK -->|Yes| FINAL_OUTPUT[Return Complete Plan]
    
    REVISE_PLAN --> WEATHER_CHECK
    FINAL_OUTPUT --> END([End])
    
    style WEATHER_CHECK fill:#e3f2fd
    style INTEREST_MATCH fill:#f3e5f5
    style BUDGET_CHECK fill:#e8f5e8
    style SELF_EVALUATE fill:#fff3e0
    style QUALITY_CHECK fill:#ffeb3b
```

## Pydantic Data Validation Flow

```mermaid
classDiagram
    class TravelerProfile {
        +list~str~ interests
        +int budget
        +int duration
        +str weather_preference
        +validate_interests()
        +validate_budget()
    }
    
    class Activity {
        +str name
        +str category
        +float cost
        +bool outdoor
        +list~str~ required_interests
        +calculate_relevance_score()
    }
    
    class Itinerary {
        +str day
        +list~Activity~ activities
        +float total_cost
        +str weather_condition
        +validate_budget_compliance()
        +check_weather_appropriateness()
    }
    
    class TripPlan {
        +TravelerProfile traveler
        +list~Itinerary~ daily_plans
        +str narrative_summary
        +float total_cost
        +dict evaluation_metrics
        +generate_narrative()
        +evaluate_quality()
    }
    
    TravelerProfile --> Activity : matches_interests
    Activity --> Itinerary : included_in
    Itinerary --> TripPlan : part_of
    TripPlan --> TravelerProfile : created_for
```

## ReAct Pattern Implementation

```mermaid
sequenceDiagram
    participant TP as Trip Planner
    participant COT as Chain-of-Thought
    participant WA as Weather API
    participant AD as Activity DB
    participant EVAL as Self Evaluator
    
    TP->>COT: Initialize Planning
    COT->>COT: THOUGHT: Analyze user preferences
    COT->>WA: ACTION: Get weather forecast
    WA->>COT: OBSERVATION: Weather data received
    
    COT->>COT: THOUGHT: Filter weather-inappropriate activities
    COT->>AD: ACTION: Query matching activities
    AD->>COT: OBSERVATION: Activity list retrieved
    
    COT->>COT: THOUGHT: Calculate budget allocation
    COT->>COT: ACTION: Generate initial itinerary
    COT->>EVAL: OBSERVATION: Request quality evaluation
    
    EVAL->>EVAL: Evaluate completeness, budget, weather appropriateness
    EVAL->>COT: Quality feedback with suggestions
    
    alt Quality Acceptable
        COT->>TP: THOUGHT: Plan is satisfactory
        COT->>TP: ACTION: Finalize itinerary
        TP->>TP: OBSERVATION: Generate narrative summary
    else Quality Issues Found
        COT->>COT: THOUGHT: Revision needed
        COT->>AD: ACTION: Find alternative activities
        AD->>COT: OBSERVATION: New options provided
        COT->>EVAL: Request re-evaluation
    end
```
