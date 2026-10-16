## 🏗️ System Architecture

```mermaid
flowchart TB
    User[👤 User] -->|1. Uploads PDF File| System[ RAG Ingestion Engine]
    System -->|2. Embed Data & Store Vectors| Pinecone[ VectorDB Pinecone]
    System -->|3. Triggers Orchestration| LangChain[🔗 LangChain Orchestrator]
    
    LangChain -->|4. Request Context| Pinecone
    Pinecone -->|5. Return Relevant Chunks| LangChain
    LangChain -->|6. Context + Prompt| LLM[ LLM Model]
    LLM -->|7. Response Context| User

    LangSmith[🛠️ LangSmith] -.->|Trace & Monitor| LangChain