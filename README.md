# Advanced RAG Talks

This repo contains live-coding material for Konrad Bujak’s talks on advanced RAG patterns. The demos are run in Jupyter notebooks, with code copied from the talk scripts.

Primary talk scripts:
- `talks/parent-document-retriever.py`

The scripts are written to be copy-pasted into notebooks during demos. They expect local infrastructure services (Qdrant + Postgres) running on your machine.

## Local Services (Docker Compose)

I usually host services locally during talks, so this repo includes a `docker-compose.yml` to bring them up quickly:

- Qdrant (vector store): `http://localhost:6333` with dashboard at `http://localhost:6333/dashboard`
- Postgres 18 (doc store)

Start services:

```bash
docker compose up -d
```

Stop services:

```bash
docker compose down
```

## Environment

Copy `.env.template` to `.env` and fill in Azure OpenAI details.

Required:

- `AZURE_OPENAI_ENDPOINT`
- `AZURE_OPENAI_API_KEY`
- `AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT`
- `AZURE_OPENAI_CHAT_DEPLOYMENT`
- `POSTGRES_URL`
- `QDRANT_URL` (defaults to `http://localhost:6333` if unset in the script)

## Data

Articles live in:

- `data/articles`

Each article is a Markdown file with YAML frontmatter. Metadata is preserved on chunked documents for the demo.

## Notebook Usage

Open a Jupyter notebook and copy the sections you need from `talks/parent-document-retriever.py`.
This follows the 6-step flow described in `docs/parent-document-retriever.md`, from naive chunking to Parent Document Retriever with Qdrant + Postgres.

## Data Sources and Scrapers

If you need to re-download or rebuild the article data, I reference the scrapers in my other repositories:

- `https://github.com/konradbjk/graham-essay-downloader`
- `https://github.com/konradbjk/smartbear-articles-downloader`

Those repos are for learning and data acquisition. This repo focuses on the talk flow and local RAG infrastructure.
