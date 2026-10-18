# Personal LLM Chatbot — RAG + Memory

A Python prototype for a personal chatbot using retrieval-augmented generation (RAG), OpenAI embeddings, FAISS vector search, SQLite-backed conversation memory, a FastAPI backend, and a Streamlit UI.

> **Project status: In progress**
>
> Current priorities include validating the document ingestion and FAISS retrieval pipeline, testing the FastAPI and Streamlit integration, and improving evaluation and error handling. End-to-end testing is still pending.

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

## Current Status & Roadmap

- [x] Prepare portfolio README and setup guidance
- [x] Add a lightweight GitHub Actions Python syntax check
- [ ] Validate document ingestion and vector-index generation end to end
- [ ] Test retrieval, API responses, and Streamlit integration
- [ ] Review error handling and evaluation results
- [ ] Capture screenshots from the running application

## Project Notes

I maintain this repository as part of my technical portfolio. I am continuing to review, test, and document the implementation. The roadmap reflects current priorities and will be updated as work progresses. Third-party packages, models, and other included materials remain subject to their respective licenses.
