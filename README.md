# 👁️ Agentic Vision System: Multi-Step Visual Reasoning with MCP

[![Author](https://img.shields.io/badge/Author-Ayan-blue.svg)](https://github.com/ayanc5813-coder)
[![Python Version](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![Framework](https://img.shields.io/badge/LangGraph-Enabled-orange)](https://python.langchain.com/docs/langgraph)
[![Protocol](https://img.shields.io/badge/Protocol-MCP-green)](https://modelcontextprotocol.io/)

A research-grade AI system that moves beyond standard image captioning. Instead of a passive **Image → Answer** pipeline, this project implements an active **Think → Act → Observe** agentic reasoning loop. By integrating Vision-Language Models (VLMs) with the Model Context Protocol (MCP), the agent can analyze an image, realize what context it is missing, dynamically call external tools (databases, rulebooks, APIs), and synthesize a final, highly accurate report.

## 🚀 Key Features

* **Agentic Reasoning (ReAct):** The model plans its steps, executes tools, and revises its understanding as new evidence arrives.
* **Standardized Tooling (MCP):** Utilizes `FastMCP` to standardize how the vision agent interacts with external systems, eliminating the need for bespoke API integrations.
* **External Memory & RAG:** Integrates ChromaDB to retrieve enterprise rules (e.g., OSHA regulations, company handbooks) to evaluate visual scenes against strict criteria.
* **Interactive UI:** A Gradio frontend designed for Google Colab, allowing users to upload images and watch the agent's internal thought process in real-time.

## 🏗️ Architecture Stack

| Component | Technology | Purpose |
| :--- | :--- | :--- |
| **Vision Model (The Eyes)** | Qwen2.5-VL / Gemma 3 | Performs initial visual inference and scene understanding (via OpenRouter). |
| **Orchestrator (The Brain)** | LangGraph | Manages the cyclical graph of reasoning, tool selection, and evaluation. |
| **Tool Interface (The Hands)**| FastMCP | Exposes local Python functions (SQL, Web Search, OCR) as standard MCP tools. |
| **Memory (The Hippocampus)** | ChromaDB | Local vector store for document retrieval (Enterprise Knowledge Base). |
| **Frontend UI** | Gradio | Web interface optimized for Google Colab deployment. |

## 🛠️ Installation & Setup

This project is optimized to run in **Google Colab** using a free T4 GPU instance.

1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/ayanc5813-coder/agentic-vision-system.git](https://github.com/ayanc5813-coder/agentic-vision-system.git)
   cd agentic-vision-system
   ```

2. **Install Dependencies:**
Ensure you are in a Colab environment or a local virtual environment.
```bash
pip install langchain langchain-openai langchain-core langgraph fastmcp chromadb gradio python-dotenv

```


3. **Configure API Keys:**
You will need an OpenRouter API key to access the vision models. Set it in your environment:
```python
import os
os.environ["OPENROUTER_API_KEY"] = "your-openrouter-api-key-here"

```


4. **Run the System:**
Execute the cells in the provided Jupyter/Colab notebook to initialize the ChromaDB memory, start the MCP server, and launch the Gradio UI.

## 🧪 Example Workflows

To see the agentic loop in action, try these queries in the Gradio UI:

### Scenario 1: Industrial Safety Compliance

* **Image:** A factory floor or construction site.
* **Prompt:** *"Look at the workers on the floor. Are they wearing the proper protective headgear required in machine zones according to our corporate OSHA guidelines?"*
* **Agent Flow:** Detects workers $\rightarrow$ Calls Knowledge Base for OSHA rules $\rightarrow$ Compares image to rules $\rightarrow$ Reports violations.

### Scenario 2: Inventory & Quality Assurance

* **Image:** A retail shelf or warehouse aisle.
* **Prompt:** *"Identify the item on the shelf that appears damaged. Look up its current status in our inventory database and check if we need to flag it."*
* **Agent Flow:** Detects damaged product $\rightarrow$ Calls SQL tool for product status $\rightarrow$ Formats a restock/flagging report.

## 👤 Author

Developed by **Ayan** ([@ayanc5813-coder](https://www.google.com/url?sa=E&source=gmail&q=https://github.com/ayanc5813-coder)).

