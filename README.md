# 🧠 AgenticAI

**AgenticAI** is a modular framework and reference implementation for building intelligent AI agents that combine Large Language Models (LLMs) with:

- 🔧 Multi-tool orchestration  
- 🧑‍💻 Human-in-the-loop assistance  
- 🔄 Stateful conversation management  

Built using **LangChain**, **LangGraph**, and **Groq’s ChatGroq (LLaMA3 8B)**, this framework is ideal for AI research, agent experimentation, and production-grade prototypes.

---

## 🚀 Features

- **🛠️ Multi-tool Integration**  
  Use search tools (e.g., `TavilySearch`), custom Python functions, and human guidance seamlessly.

- **🧭 Stateful Conversation Graphs**  
  Manage conversation flows using `LangGraph`’s `StateGraph`.

- **🧑 Human-in-the-Loop**  
  Interrupt execution to request manual inputs or approvals.

- **⚡ Scalable LLM Backend**  
  Powered by Groq’s `ChatGroq` running LLaMA3-8B for ultra-fast response times.

- **🔌 Extensible Architecture**  
  Easily plug in new tools, APIs, or logic layers.

- **📡 Real-time Streaming Support**  
  Stream assistant responses live via LangGraph’s `astream_events`.

- **💾 Memory & Checkpointing**  
  Use `MemorySaver` to persist state across interactions.

---

## 🛠️ Getting Started

### ✅ Prerequisites

- Python 3.9+
- `pip` (Python package manager)
- API keys:
  - `GROQ_API_KEY` (for ChatGroq)
  - `TAVILY_API_KEY` (optional, for web search)

### 📦 Installation

```bash
git clone https://github.com/atulgupta1/AgenticAI.git
cd AgenticAI
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt


GROQ_API_KEY=your_groq_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here


from dotenv import load_dotenv
load_dotenv()


from langchain_groq import ChatGroq
from langchain_tavily import TavilySearch
from your_agenticai_module import build_agent_graph  # your LangGraph builder

llm = ChatGroq(model="llama3-8b-8192", api_key=os.getenv("GROQ_API_KEY"))
search_tool = TavilySearch(max_search=2)

tools = [search_tool, human_assistance]  # Define all tools
agent = build_agent_graph(llm, tools)

response = agent.invoke({
    "messages": [{"role": "user", "content": "What is the latest in AI research?"}]
})

print(response["messages"][-1].content)

### Architecture Overview
Component	Description
LangGraph StateGraph	Defines node logic, transitions, and message reducers
LangChain Chat Models	Uses Groq’s ChatGroq (LLaMA3-8B) for chat completion
Tools	Includes search tools, human interrupts, and custom functions
MemorySaver	Checkpoints state and conversation history

### 🤝 Contributing
Contributions are welcome!
If you have suggestions, bug reports, or improvements:

Open an issue

Submit a pull request

Or start a discussion on how to extend the framework

### 📄 License
This project is licensed under the MIT License.

### 📬 Contact
Atul Gupta
📧 Email: atul.svnit11@gmail.com
🔗 GitHub: https://github.com/atulgupta1

