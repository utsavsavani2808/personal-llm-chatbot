# Personal LLM Chatbot — RAG + Memory

A modular Python prototype for a personal chatbot using retrieval-augmented generation (RAG), embeddings and lightweight conversation memory. Includes API/UI components, ingestion and indexing scripts, evaluation cases, Docker assets and a GitHub Actions workflow.

## Features
- LLM integration configured through environment variables
- Document chunking and embedding/index-building workflow
- Retrieval-augmented responses
- SQLite-backed conversation memory
- Evaluation scripts and test cases
- Docker and CI workflow scaffolding

## Setup

```bash
python -m venv .venv
# Windows: .venv\\Scripts\\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
```

Set `OPENAI_API_KEY` in your local environment. Optional settings include `OPENAI_MODEL`, `OPENAI_EMBED_MODEL`, `RAG_TOP_K` and `MEMORY_MAX_TURNS`. Do not commit credentials or `.env` files.

Run the ingestion and indexing scripts in order:

```bash
python scripts/01_ingest_docs.py
python scripts/02_build_index.py
python scripts/03_run_eval.py
```

Use the entry point and configuration supported by the current code to launch the service or UI. Review the code and deployment configuration before publishing a live demo.

## Repository layout

```text
app/       API, chat engine, LLM client, RAG, memory and prompts
scripts/   ingestion, indexing and evaluation
ui/        UI code
data/raw/  sample source document
docker/    container configuration
.github/   CI workflow
```

## Security and privacy
Do not commit API keys, `.env` files, credentials, real conversation histories, runtime databases or generated indexes. The repository is a learning/portfolio project, not a production-ready service; review the implementation and evaluation method before making performance claims.

## Attribution
This repository is a curated portfolio version of a project archive. Review dependencies, third-party model licenses and source attribution before redistribution or commercial use.
