# bedrock-astradb-rag
# ⚡ Amazon Bedrock Agent: (Astra DB RAG)

This repository contains the configuration and core code for the `youtube-agent`, an advanced conversational agent built on **Amazon Bedrock**.

This agent demonstrates sophisticated LLM orchestration by integrating a custom persona, a **Lambda Action Group**, and a **Knowledge Base powered by Astra DB** for Retrieval-Augmented Generation (RAG).

---

## ⚙️ Project Components

| Component | Description | Integration |
| :--- | :--- | :--- |
| **Bedrock Agent** | The core orchestrator. Configured with the **Harry Potter** persona and Nova Pro 1.0 model. | AWS Bedrock |
| **Lambda Function** | The custom **Action Group Handler** (`lambda_function.py`). Used for business logic beyond simple RAG. | AWS Lambda |
| **Astra DB** | The external vector database serving as the **Knowledge Base** (KB) for RAG retrieval. | `POST_read_from_astra_searchVectorContent` |

---

## 🚀 Deployment & Configuration

### 1. Lambda Action Group (`lambda_function.py`)

This Python file serves as the Action Group Handler for search operations. It connects to Astra DB using secure environment variables.

```python
# Snippet from lambda_function.py
def lambda_handler(event, context):
    # ... Input validation for 'search_term' ...
    
    # Read configuration from environment variables
    astra_token = os.environ.get('astra_token') 
    astra_endpoint = os.environ.get('astra_endpoint')
    keyspace = os.environ.get('keyspace', 'default keyspace') 
    
    # ... Logic to connect to Astra DB and perform action ...
    # ... Returns response to Bedrock agent ...
