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
| File            | Description                                                                                                                      |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `lib/agents.py` | Core agent logic. Prepares prompts, runs the LLM, detects tool calls, executes tools, manages memory, and returns final answers. |


#### State Machine
| File                   | Description                                                                                                                    |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| `lib/state_machine.py` | Custom state machine engine. Manages step transitions, executes workflow stages, stores snapshots, and handles reasoning runs. |

#### Tooling Layer
| File             | Description                                                                                                            |
| ---------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `lib/tooling.py` | Defines the `@tool` decorator and the Tool class. Converts Python functions into LLM-callable tools with JSON schemas. |

#### Memory System
| File            | Description                                                                                                                      |
| --------------- | -------------------------------------------------------------------------------------------------------------------------------- |
| `lib/memory.py` | Implements **Short-Term Memory** for multi-turn conversation. Stores run history by `session_id` and retrieves previous context. |

#### Documents & Retrieval
| File               | Description                                                               |
| ------------------ | ------------------------------------------------------------------------- |
| `lib/documents.py` | Defines the `Document` and `Corpus` structures for managing textual data. |
| `lib/loaders.py`   | Utilities for loading and parsing documents (e.g., PDF loader).           |

#### Vector Database (RAG)
| File               | Description                                                                                                           |
| ------------------ | --------------------------------------------------------------------------------------------------------------------- |
| `lib/vector_db.py` | Interface to ChromaDB. Handles vector store creation, document embedding, similarity queries, and metadata retrieval. |

#### Parsing & Evaluation
| File                | Description                                                                                        |
| ------------------- | -------------------------------------------------------------------------------------------------- |
| `lib/parsers.py`    | Structured parsing utilities using Pydantic. Useful for tools that must return structured answers. |
| `lib/evaluation.py` | Logic for evaluating retrieval quality or ranking game documents.                                  |

#### Juypter notebooks
| Notebook                           | Purpose                                                                         |
| ---------------------------------- | ------------------------------------------------------------------------------- |
| `Udaplay_01_starter_project.ipynb` | Loads game data, builds the vector store, demonstrates retrieval.               |
| `Udaplay_02_starter_project.ipynb` | Full agent demo: multi-turn conversation, memory, RAG pipeline, tool execution. |
