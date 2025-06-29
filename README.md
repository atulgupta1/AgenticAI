AgenticAI
AgenticAI is a modular framework and reference implementation for building intelligent AI agents that combine Large Language Models (LLMs) with multi-tool orchestration, human-in-the-loop assistance, and stateful conversation management. Powered by LangChain, LangGraph, and Groq’s ChatGroq model, AgenticAI enables flexible, interactive AI workflows for research, experimentation, and production prototyping.

Features
Multi-tool integration: Seamlessly use search tools (e.g., TavilySearch), human assistance, and custom logic within a single agent.

Stateful conversation graphs: Manage complex conversations with state machines via LangGraph’s StateGraph abstractions.

Human-in-the-loop: Pause agent workflows to request human input with interrupt-driven tools.

Scalable LLM backend: Utilizes Groq’s ChatGroq (Llama3 8B) for high-performance language understanding and generation.

Extensible architecture: Easily add new tools, custom functions, or external APIs.

Streamed and async responses: Supports real-time streaming and asynchronous interaction models.

Memory & checkpointing: Save and resume conversation state with persistent memory layers.

Getting Started
Prerequisites
Python 3.9+

pip package manager

API keys:

Groq API key (GROQ_API_KEY)

Tavily API access (if using TavilySearch tool)

Installation

git clone https://github.com/atulgupta1/AgenticAI.git
cd AgenticAI
python -m venv .venv
source .venv/bin/activate  # On Windows use: .venv\Scripts\activate
pip install -r requirements.txt
Configuration
Create a .env file with your API keys:


GROQ_API_KEY=your_groq_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here
Load environment variables in your Python code with:


from dotenv import load_dotenv
load_dotenv()
Usage
A simple example to initialize the agent and run a query:

python
Copy
Edit
from langchain_groq import ChatGroq
from langchain_tavily import TavilySearch
from your_agenticai_module import build_agent_graph  # your graph-building function

llm = ChatGroq(model="llama3-8b-8192", api_key=os.getenv("GROQ_API_KEY"))
search_tool = TavilySearch(max_search=2)

tools = [search_tool, human_assistance]  # human_assistance is a tool to request human input
agent = build_agent_graph(llm, tools)

response = agent.invoke({
    "messages": [{"role": "user", "content": "What is the latest in AI research?"}]
})

print(response["messages"][-1].content)
Architecture Overview
LangGraph StateGraph: Defines states and transitions in conversation flow.

LangChain Chat Models: ChatGroq LLM integration for language generation.

Tools: Custom functions, search tools, and human assistance decorators.

MemorySaver: Checkpointing and persistence layer for conversation continuity.

Contributing
Contributions welcome! Please open issues or PRs for bug fixes, features, or improvements.
For major changes, please open an issue first to discuss your ideas.

License
This project is licensed under the MIT License.

Contact
Atul Gupta – atul.svnit11@gmail.com
GitHub: https://github.com/atulgupta1
