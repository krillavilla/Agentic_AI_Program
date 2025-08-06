# Agentic AI Program - Project Audit Notes

## 1. Agentic-Workflows

### Purpose
• Python project implementing agentic workflows for automated task processing using OpenAI's GPT models
• Demonstrates building blocks for agentic systems and complete workflow for product specification email routing

### Key Features
• **Phase 1**: Seven reusable agent classes serving as building blocks
• **Phase 2**: Complete agentic workflow for routing product specification emails to appropriate team members
• Agent types: DirectPromptAgent, AugmentedPromptAgent, KnowledgeAugmentedPromptAgent, RAGKnowledgePromptAgent, EvaluationAgent, RoutingAgent, ActionPlanningAgent
• Routes emails to Product Manager, Program Manager, or Development Engineer
• Generates specialized responses for each role with quality evaluation

### Tech Stack
• **Language**: Python 3.7+
• **Core Dependencies**: 
  - openai==1.78.1
  - python-dotenv==1.1.0
  - numpy==1.26.4
  - httpx>=0.24.1
  - tqdm>=4.66.1
  - distro>=1.8.0
• **APIs**: OpenAI GPT models

### Notable Results
• **Sample Output**: Direct prompt agent explaining recursion in 3 sentences
• Workflow processes three example emails through routing → response generation → evaluation pipeline
• Demonstrates automated task routing with confidence scoring (0.95 confidence in product manager routing example)

### Setup Commands
```bash
git clone https://github.com/yourusername/Agentic-Workflows.git
cd Agentic-Workflows
pip install openai python-dotenv
```

### Sample Outputs
• **Direct Prompt Response**: "Recursion in programming is a technique where a function calls itself in order to solve a problem..."
• **Workflow Output**: Shows processing steps with routing results, response generation, and evaluation feedback
• **Test Files**: 24 output files demonstrating each agent's capabilities across different scenarios

---

## 2. AgentsVille Trip Planner

### Purpose
• AI-powered system for planning personalized vacations to fictional city "AgentsVille"
• Demonstrates advanced LLM reasoning techniques for travel planning

### Key Features
• **Personalized Itineraries**: Creates travel plans based on traveler interests and preferences
• **Weather-Aware Planning**: Avoids outdoor activities during bad weather
• **Budget Management**: Ensures total cost stays within specified budget
• **Activity Recommendations**: Matches activities to traveler interests
• **Itinerary Revision**: Refines plans based on feedback and evaluation
• **Narrative Summary**: Creates story-like trip descriptions

### Tech Stack
• **Language**: Python 3.8+
• **Format**: Jupyter Notebook implementation
• **Core Dependencies**:
  - openai==1.74.0
  - pandas==2.3.0
  - pydantic==2.11.7
  - json-repair==0.47.1
  - python-dotenv==1.1.0
  - jupyter==1.0.0
• **APIs**: OpenAI API

### Notable Results
• **LLM Techniques Demonstrated**:
  - Role-Based Prompting (agents as specialized travel planners)
  - Chain-of-Thought Reasoning (step-by-step itinerary planning)
  - ReAct Prompting (Thought → Action → Observation cycles)
  - Feedback Loops (self-evaluation and improvement)

### Setup Commands
```bash
git clone https://github.com/krillavilla/AgentsVille-Trip-Planner.git
cd AgentsVille-Trip-Planner
pip install -r requirements.txt
# Add OPENAI_API_KEY to .env file
jupyter notebook project_starter.ipynb
```

### Sample Outputs
• **Process Flow**: Vacation definition → weather/activity data → initial itinerary → evaluation → revision → narrative summary
• **Helper Library**: ChatAgent class with conversation memory, Interest enum for activity matching
• **Mock APIs**: Simulated weather and activity data for AgentsVille

---

## 3. Multi-Agent PaperSolution (Beaver's Choice Paper Company)

### Purpose
• Multi-agent system for streamlining quoting and inventory management at fictional paper company
• Automates customer inquiries, quote generation, and sales processing

### Key Features
• **Multi-Agent Architecture**: Up to 5 agents working in coordination
• **Inventory Management**: Stock tracking and supplier delivery estimation
• **Smart Quote Generation**: Historical data analysis with bulk discount logic
• **Sales Processing**: Transaction handling and inventory updates
• **Financial Reporting**: Cash balance and top-selling product reports
• **Orchestrator System**: Coordinates agent actions for customer requests

### Tech Stack
• **Language**: Python 3.8+
• **Framework**: smolagents
• **Core Dependencies**:
  - pandas==2.2.3
  - openai==1.76.0
  - SQLAlchemy==2.0.40
  - python-dotenv==1.1.0
  - smolagents
• **Database**: SQLite for data persistence

### Notable Results
• **Business Metrics**:
  - Total Orders Processed: 19
  - Total Revenue Generated: $392.50
  - Final Cash Balance: $45,059.70
• **Top Selling Items**:
  - Cardstock: 8 orders, 800 units
  - Glossy paper: 5 orders, 1000 units
  - A4 paper: 4 orders, 1050 units

### Setup Commands
```bash
python3 -m venv venv-paper-solution
source venv-paper-solution/bin/activate
pip install -r requirements.txt
# Create .env with UDACITY_OPENAI_API_KEY
python project_starter.py
```

### Sample Outputs
• **Order Confirmations**: "Order confirmed! We've successfully processed your order for 200 units of Glossy paper for a total of $40.00"
• **CSV Results**: Complete transaction log with request IDs, dates, cash balances, and responses
• **Financial Reports**: Comprehensive business performance summaries

---

## 4. UdaPlay AI Agent

### Purpose
• AI-powered research agent for video game industry
• Two-part system: offline RAG (Retrieval-Augmented Generation) + intelligent agent with web search capabilities

### Key Features
• **Part 1 - Offline RAG**: ChromaDB vector database for game information storage and retrieval
• **Part 2 - AI Agent**: Combines local knowledge with web search capabilities
• **Tool System**: 3 specialized tools (retrieve_game, evaluate_retrieval, game_web_search)
• **State Machine Workflow**: Entry Point → Message Prep → LLM Processing → Tool Execution → Termination
• **Memory Management**: Short-term memory, session management, state persistence
• **Multi-Modal Search**: Local semantic search + web fallback via Tavily API

### Tech Stack
• **Language**: Python 3.11+
• **Vector Database**: ChromaDB
• **Core Dependencies**:
  - chromadb==1.0.4
  - openai==1.73.0
  - tavily-python==0.5.4
  - pydantic==2.11.3
  - python-dotenv==1.1.0
• **APIs**: OpenAI API, Tavily API for web search
• **Game Data**: 15 JSON files with game metadata

### Notable Results
• **Game Database**: Name, Platform, Genre, Publisher, Description, Year of Release for each game
• **Intelligent Routing**: LLM evaluates if local knowledge is sufficient, falls back to web search when needed
• **Conversation Memory**: Maintains context across multiple interactions
• **Structured Outputs**: JSON-formatted responses with metadata

### Setup Commands
```bash
python3 -m venv udaplay-env
source udaplay-env/bin/activate
pip install -r requirements.txt
# Create .env with OPENAI_API_KEY, CHROMA_OPENAI_API_KEY, TAVILY_API_KEY
jupyter notebook
# Complete Udaplay_01_starter_project.ipynb then Udaplay_02_starter_project.ipynb
```

### Sample Outputs
• **Test Queries**: 
  - "When was Pokémon Gold and Silver released?"
  - "Which one was the first 3D platformer Mario game?"
  - "Was Mortal Kombat X released for PlayStation 5?"
• **Tool Responses**: JSON-formatted game metadata and search results
• **Agent Architecture**: Complete lib/ directory with specialized modules for agents, memory, tools, etc.

---

## 5. Classroom Materials (cd14525-agentic-workflows-classroom)

### Purpose
• Course content repository for agentic workflows education
• Template and source of truth for course projects and exercises
• Structured learning materials for content development

### Key Features
• **10 Lesson Structure**: From introduction to advanced orchestrator-worker patterns
• **Exercise Framework**: Starter code, solutions, and comprehensive README templates
• **Project Template**: Phase 1 (agent library) + Phase 2 (workflow implementation)
• **Multiple Workflow Patterns**: Prompt chaining, routing, parallelization, evaluation-optimization
• **Framework Demonstrations**: AutoGPT, AutoGen, CrewAI examples

### Tech Stack
• **Language**: Python
• **Framework Examples**: AutoGPT, AutoGen (Conversational & Nested), CrewAI
• **Educational Tools**: Mermaid diagram generation, demo orchestrators
• **Dependencies**: Listed in project/requirements.txt

### Notable Results
• **Course Structure**:
  - Lesson 1: Introduction to Agentic Workflows
  - Lesson 2: Understanding Agentic Workflows  
  - Lesson 3: Agentic Workflow Modeling
  - Lesson 4: Implementation
  - Lessons 5-8: Workflow Patterns (Chaining, Routing, Parallelization, Evaluation)
  - Lesson 9: Orchestrator-Workers Pattern
  - Lesson 10: Lesson Overview

### Setup Commands
```bash
# Course materials are templates - specific setup varies by lesson
# General structure for project work:
cd cd14525-agentic-workflows-classroom/project/starter
pip install -r requirements.txt
```

### Sample Outputs
• **Project Goal**: "AI-Powered Agentic Workflow for Project Management (Pilot: Email Router)"
• **Target Deliverables**: 
  - Phase 1: 7 reusable agent classes with individual tests
  - Phase 2: Orchestrated workflow for technical project management
• **Audience**: Technical Project Managers and leadership at "InnovateNext Solutions"

---

## Quick Reference Summary

### Project Complexity Levels
• **Beginner**: AgentsVille Trip Planner (Jupyter notebook, single workflow)
• **Intermediate**: Agentic-Workflows (multi-agent library + workflow), Multi-Agent PaperSolution (business automation)
• **Advanced**: UdaPlay AI Agent (RAG + state machine + web search), Classroom Materials (comprehensive course structure)

### Common Tech Stack Elements
• **Universal**: Python, OpenAI API, python-dotenv
• **Data Processing**: pandas (3/5 projects), pydantic (3/5 projects)
• **Specialized**: ChromaDB (vector database), smolagents (multi-agent framework), SQLAlchemy (database ORM)

### Setup Pattern Consistency
• All projects use virtual environments
• All require OpenAI API key in .env file
• Most use requirements.txt for dependency management
• Jupyter notebooks for interactive development (2/5 projects)

### Output Patterns
• **Text-based responses** for conversational agents
• **CSV files** for business transaction logs
• **JSON structures** for structured data exchange
• **Terminal outputs** with formatted logging and progress tracking
