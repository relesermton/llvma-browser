# LLVMA 🔍

**LLVMA** is an open-source, privacy-first search engine powered by integrated conversational AI. It combines dense vector retrieval, traditional keyword indexing, and local or remote LLMs to deliver accurate, real-time web and document search results.

---

## ✨ Features

- **Hybrid Search Engine**: Combines lexical ranking (BM25) with vector embeddings for high-precision semantic search.
- **Built-in Assistant (LLVMA AI)**: Direct answers, summaries, and synthesis generated directly from search results.
- **Privacy by Design**: No telemetry, no query logging, and 100% self-hostable.
- **Extensible Crawlers & Connectors**: Index the open web, local document repositories (PDF, Markdown, HTML), or internal databases.
- **Pluggable LLM Backends**: Works out-of-the-box with local inference (Ollama, vLLM, llama.cpp) or external APIs (OpenAI, Anthropic, Groq).
- **Modern Web UI & Clean API**: Fast, responsive frontend interface alongside a fully documented REST and WebSocket API.

---

## 🏗️ Architecture

                   ┌──────────────────────┐
                   │     LLVMA Web UI     │
                   └──────────┬───────────┘
                              │ HTTP / WS
                              ▼
┌─────────────────────────────────────────────────────────────┐ │ LLVMA Core │ │ │ │ ┌──────────────┐ ┌──────────────┐ ┌───────────┐ │ │ │ Query Parser │ ──▶ │ Hybrid Index │ ──▶ │ Reranker │ │ │ └──────────────┘ └──────┬───────┘ └─────┬─────┘ │ └───────────────────────────────┼───────────────────┼─────────┘ │ ▼ ┌──────────────┴────────┐ ┌───────────┐ │ Vector DB + Full-Text │ │ LLVMA AI │ │ (Qdrant / Tantivy) │ │ Engine │ └───────────────────────┘ └───────────┘


---

## 🚀 Quick Start (Docker)

The fastest way to spin up an instance of LLVMA with default settings:

### 1. Clone the repository

```bash
git clone https://github.com/relesermton/llvma.git
cd llvma
2. Configure Environment
Copy the example configuration file:

cp .env.example .env
Set your LLM backend in .env (default is configured for local Ollama):

LLM_PROVIDER=ollama
OLLAMA_BASE_URL=http://localhost:11434
LLM_MODEL=llama3:8b
EMBEDDING_MODEL=nomic-embed-text
3. Launch Services
docker compose up -d
Open your browser and navigate to:

http://localhost:8080
🛠️ Manual Installation & Development
Prerequisites
Node.js >= 20.x
Python >= 3.11 (or Go / Rust depending on your core service)
Vector Store (e.g., Qdrant, Milvus, or embedded Tantivy)
1. Backend Service
cd backend
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate
pip install -r requirements.txt
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
2. Frontend Interface
cd frontend
npm install
npm run dev
The frontend will run on http://localhost:3000 and proxy search queries to the backend on port 8000.

🔌 API Usage
LLVMA exposes a simple REST API for querying both the index and the AI assistant.

Search Query
curl -X POST http://localhost:8000/api/v1/search \
  -H "Content-Type: application/json" \
  -d '{
    "query": "open source search engines architecture",
    "limit": 5,
    "ai_assist": true
  }'
Response Example
{
  "query": "open source search engines architecture",
  "answer": "Modern open-source search engines typically use a hybrid architecture combining...",
  "results": [
    {
      "title": "Search Engine Design Notes",
      "url": "https://example.com/docs/search",
      "score": 0.89,
      "snippet": "Details on inverted indexes and vector reranking..."
    }
  ]
}
⚙️ Configuration Variables
| Variable | Default | Description | | :--- | :--- | :--- | | PORT | 8080 | Web UI and API entry port | | LLM_PROVIDER | ollama | Provider: ollama, openai, or custom | | OPENAI_API_KEY | "" | Required if using OpenAI-compatible backends | | VECTOR_STORE | qdrant | Storage backend for embeddings (qdrant, chroma, builtin) | | INDEX_STORAGE_PATH| ./data/index | Directory path for local document storage |

🤝 Contributing
We welcome community contributions!

Fork the repo.
Create a feature branch: git checkout -b feature/my-feature.
Commit your changes: git commit -m 'Add new feature'.
Push to the branch: git push origin feature/my-feature.
Open a Pull Request.
Please read our CONTRIBUTING.md for code style guidelines and testing practices.

📄 License
LLVMA is released under the MIT licence.
