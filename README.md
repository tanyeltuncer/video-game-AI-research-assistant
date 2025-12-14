# Video game AI-research assistant
### Description
This repository implements a Video Game AI Research Assistant, an intelligent multi-agent system designed to answer questions about video games using a combination of:

- Retrieval-Augmented Generation (RAG)
- Vector database search
- Tool-calling agents
- Multi-turn conversational memory
- Web search (optional)

The assistant takes user queries about games, retrieves relevant documents from a vector database, analyzes the relevance of retrieved results, and produces clear, research-style answers.
It also supports short-term memory, allowing multi-turn conversations where context is preserved.

The system is built using a modular architecture with:
- a custom state machine that orchestrates agent reasoning,
- a tooling layer for function-calling,
- an LLM wrapper,
- a memory subsystem,
- vector DB integration via ChromaDB, and
- a clean notebook-based workflow.

This project demonstrates a fully functioning multi-agent research assistant specialized for the video game domain, but the architecture is generalizable to any RAG or tool-calling AI system.

### Respository structure
#### LLM & Messaging 
| File              | Description                                                                                                                   |
| ----------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `lib/llm.py`      | Wrapper around the OpenAI API. Handles chat messages, tool calls, structured outputs, and token usage.                        |
| `lib/messages.py` | Defines message types (`UserMessage`, `SystemMessage`, `AssistantMessage`, `ToolMessage`). Ensures consistent message schema. |


#### Agent System
