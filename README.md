# Personal LLM Chatbot — RAG + Memory

A Python prototype for a personal chatbot using retrieval-augmented generation (RAG), OpenAI embeddings, FAISS vector search, SQLite-backed conversation memory, a FastAPI backend, and a Streamlit UI.

## Features
- Document ingestion and chunking
- OpenAI embedding generation and FAISS retrieval
- LLM-based response generation with retrieved context
- Conversation memory stored locally in SQLite
- API health and chat endpoints
- Evaluation scaffold and Docker/CI configuration

## Setup

Use Python 3.11. Create and activate a virtual environment, then install dependencies:

```bash
python -m venv .venv
# Windows PowerShell: .venv\\Scripts\\Activate.ps1
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
```

Set `OPENAI_API_KEY` in your local environment. Optional settings include `OPENAI_MODEL`, `OPENAI_EMBED_MODEL`, `RAG_TOP_K`, and `MEMORY_MAX_TURNS`. Do not commit credentials or `.env` files.

Build data chunks and the vector index from the repository root:

```bash
python scripts/01_ingest_docs.py
python scripts/02_build_index.py
```

Start the FastAPI backend in one terminal:

```bash
uvicorn app.api:app --host 0.0.0.0 --port 8000
```

In a second terminal, launch the Streamlit UI:

```bash
streamlit run ui/app.py
```

The UI defaults to `http://127.0.0.1:8000/chat`; set `CHAT_API_URL` to override it. Run the evaluation scaffold after the index is built:

```bash
python scripts/03_run_eval.py
```

## Security and limitations

Generated vector indexes, processed chunks, caches, local databases and real conversation histories are runtime data and should remain local. The included source document is only a small sample. The evaluation script is a starter scaffold, not an independently validated benchmark. This is a learning/portfolio prototype, not production-ready software; review authentication, privacy, error handling and deployment security before public deployment.

## Attribution

This is a curated portfolio copy of a supplied project archive. Review third-party package and model licenses before redistribution or commercial use.
