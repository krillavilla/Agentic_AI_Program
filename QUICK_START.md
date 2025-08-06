# 🚀 Quick-Start Guide: Agentic AI Program

## One-command setup for the complete multi-agent systems portfolio

## 📋 Prerequisites

- **Git** 2.0+
- **Python** 3.7+ (3.11+ recommended for optimal compatibility)
- **API Keys**: OpenAI API key (required for all projects)

## ⚡ Quick Start (5 Minutes)

### 1. Clone the Monorepo

```bash
# Clone the main repository with all submodules
git clone --recursive https://github.com/krillavilla/Agentic_AI_Program.git
cd Agentic_AI_Program

# If you already cloned without --recursive, initialize submodules:
git submodule update --init --recursive
```

### 2. Create Monorepo-Level Virtual Environment

```bash
# Create unified virtual environment for all projects
python3 -m venv agentic-ai-env

# Activate virtual environment
# macOS/Linux:
source agentic-ai-env/bin/activate

# Windows:
agentic-ai-env\Scripts\activate
```

### 3. Install All Dependencies

```bash
# Install all project dependencies in one command
pip install --upgrade pip
pip install openai==1.78.1 python-dotenv==1.1.0 pandas==2.3.0 numpy==2.3.1
pip install chromadb==1.0.4 tavily-python==0.5.4 pydantic==2.11.7 
pip install SQLAlchemy==2.0.40 smolagents jupyter==1.0.0 ipython==8.12.0
pip install json-repair==0.47.1 httpx tqdm distro
```

### 4. Configure API Keys

Create a `.env` file in the root directory:

```bash
# Create environment file
cat > .env << 'EOF'
# OpenAI API Configuration (Required for all projects)
OPENAI_API_KEY=your_openai_api_key_here
UDACITY_OPENAI_API_KEY=your_openai_api_key_here

# ChromaDB Configuration (UdaPlay AI Agent)
CHROMA_OPENAI_API_KEY=your_openai_api_key_here

# Tavily API Configuration (UdaPlay AI Agent - Web Search)
TAVILY_API_KEY=your_tavily_api_key_here
EOF
```

**Replace placeholder values with your actual API keys:**
- **OpenAI API**: Get from [OpenAI Platform](https://platform.openai.com/api-keys)
- **Tavily API**: Get from [Tavily Dashboard](https://tavily.com/) (free tier available)

### 5. Quick Verification

Test your setup by running a simple project:

```bash
cd Agentic-Workflows/phase_1
python direct_prompt_agent_test.py
```

**Expected output**: A response from the DirectPromptAgent demonstrating successful OpenAI API connection.

---

## 📊 Environment Matrix

| **Component** | **Minimum Version** | **Recommended** | **Used In Projects** |
|---------------|-------------------|-----------------|---------------------|
| **Python** | 3.7+ | 3.11+ | All Projects |
| **OpenAI** | 1.73.0 | 1.78.1 | All Projects |
| **pandas** | 2.2.3 | 2.3.0 | Trip Planner, PaperSolution, Classroom |
| **ChromaDB** | 1.0.4 | 1.0.4 | UdaPlay AI Agent |
| **SQLAlchemy** | 2.0.40 | 2.0.40 | Multi-Agent PaperSolution |
| **smolagents** | latest | latest | Multi-Agent PaperSolution |
| **jupyter** | 1.0.0 | 1.0.0 | AgentsVille Trip Planner |
| **pydantic** | 2.11.3 | 2.11.7 | Trip Planner, UdaPlay Agent |
| **tavily-python** | 0.5.4 | 0.5.4 | UdaPlay AI Agent |
| **python-dotenv** | 1.1.0 | 1.1.0 | All Projects |
| **numpy** | 1.26.4 | 2.3.1 | Workflows, Trip Planner |

### 🔧 Core Dependencies Summary

**Essential for all projects:**
- `openai` (LLM integration)
- `python-dotenv` (environment management)

**Data & Analytics:**
- `pandas` (data processing)
- `numpy` (numerical computing)
- `pydantic` (data validation)

**AI & ML Frameworks:**
- `chromadb` (vector database)
- `smolagents` (multi-agent orchestration)
- `tavily-python` (web search)

**Development & Visualization:**
- `jupyter` (interactive notebooks)
- `SQLAlchemy` (database ORM)

---

## 🎯 Project-Specific Setup

After completing the quick start above, you can dive deeper into individual projects:

### 🏗️ 1. Agentic Workflows - Customer Support Hub
**Path**: `Agentic-Workflows/`  
**Setup**: [Detailed README](Agentic-Workflows/README.md)  
**Features**: 7 agent classes, email routing, quality evaluation  
**Run**: `python phase_2/agentic_workflow.py`

### 🧠 2. AgentsVille Trip Planner - AI Travel Platform  
**Path**: `AgentsVille-Trip-Planner/`  
**Setup**: [Detailed README](AgentsVille-Trip-Planner/README.md)  
**Features**: Weather-aware planning, chain-of-thought reasoning  
**Run**: `jupyter notebook project_starter.ipynb`

### 💼 3. Multi-Agent PaperSolution - B2B Automation
**Path**: `Multi-Agent-PaperSolution/`  
**Setup**: [Detailed README](Multi-Agent-PaperSolution/README.md)  
**Features**: 5-agent coordination, real financial tracking  
**Run**: `python project_starter.py`

### 🎮 4. UdaPlay AI Agent - Knowledge Management
**Path**: `udaplay-ai-agent/`  
**Setup**: [Detailed README](udaplay-ai-agent/README.md)  
**Features**: Hybrid RAG+web search, state machine architecture  
**Run**: `jupyter notebook Udaplay_01_starter_project.ipynb`

### 📚 5. Classroom Materials - Enterprise Training
**Path**: `cd14525-agentic-workflows-classroom/`  
**Setup**: [Detailed README](cd14525-agentic-workflows-classroom/README.md)  
**Features**: 10-lesson curriculum, framework comparisons  
**Run**: Follow lesson progression 1-10

---

## 🔧 Advanced Configuration

### Individual Project Virtual Environments

If you prefer isolated environments per project:

```bash
# Example: AgentsVille Trip Planner
cd AgentsVille-Trip-Planner
python3 -m venv AgentsVille-Trip-env
source AgentsVille-Trip-env/bin/activate  # or AgentsVille-Trip-env\Scripts\activate on Windows
pip install -r requirements.txt
```

### API Key Management

**Per-project `.env` files**: Some projects may require their own `.env` file. Copy the root `.env`:

```bash
# Copy to specific project directories as needed
cp .env Agentic-Workflows/phase_2/.env
cp .env AgentsVille-Trip-Planner/.env
cp .env Multi-Agent-PaperSolution/.env
cp .env udaplay-ai-agent/.env
```

### Troubleshooting

**Common Issues:**

1. **Import Errors**: Ensure virtual environment is activated and dependencies installed
2. **API Key Errors**: Verify `.env` file exists and contains valid keys
3. **Python Version**: Use Python 3.7+ (3.11+ recommended)
4. **Git Submodules**: Run `git submodule update --init --recursive` if projects are missing

**Getting Help:**
- Check individual project READMEs linked above
- Verify API key validity at respective provider dashboards
- Ensure sufficient API credits for OpenAI/Tavily accounts

---

## 🎯 Next Steps

1. **Start with Agentic Workflows** for foundational agent concepts
2. **Try AgentsVille Trip Planner** for advanced LLM techniques  
3. **Explore Multi-Agent PaperSolution** for production systems
4. **Dive into UdaPlay AI Agent** for hybrid knowledge systems
5. **Use Classroom Materials** for comprehensive learning

**Total Setup Time**: ~5 minutes | **Total Learning Path**: 40+ hours of hands-on AI agent development

---

*This quick-start guide gets you running immediately. For production deployments, detailed architecture explanations, and advanced configurations, see the individual project READMEs linked above.*
