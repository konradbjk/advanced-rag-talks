# Repository Guidelines

## Project Structure & Module Organization
- This repo is talk-first and notebook-driven. Code is copied into Jupyter notebooks from scripts in `talks/`.
- `talks/parent-document-retriever.py` is the main script used for the Parent Document Retriever demo.
- `docs/` contains design notes and reference material (see `docs/parent-document-retriever.md`).
- `pyproject.toml` defines project metadata and runtime dependencies.
- `uv.lock` is the lockfile for reproducible installs.

If you add new scripts, keep them in `talks/` and write them to be easy to copy into notebooks (straight-line code, minimal helpers). Avoid “clever” helpers or over-engineered abstractions.

## Build, Test, and Development Commands
- There is no single runtime entry point; notebooks are the primary execution path.
- `uv sync` installs dependencies from `pyproject.toml` and `uv.lock` (preferred if you use `uv`).
- `python -m pip install -e .` installs the project in editable mode if you are not using `uv`.
- Add dependencies with `uv add <package>` (do not edit `pyproject.toml` or `uv.lock` by hand).

There is no build step yet; add one only if you introduce packaging or compiled assets.

## Coding Style & Naming Conventions
- Indentation: 4 spaces, no tabs (PEP 8).
- Naming: `snake_case` for functions and variables, `PascalCase` for classes, `UPPER_SNAKE_CASE` for constants.
- Keep modules small and purpose-specific; prefer clear, descriptive names over abbreviations.

No formatter or linter is configured yet. If you add one (e.g., Ruff or Black), document the exact commands here.

## Live-Coding Focus
- This repository supports live-coding segments for Konrad Bujak’s public speaking appearances.
- Demos run in Jupyter notebooks; scripts in `talks/` should be copy-paste friendly.
- Avoid adding tests or test frameworks; keep the project lightweight and fast to run on stage.
- Prioritize clarity and minimal setup over completeness.

## Commit & Pull Request Guidelines
- There is no commit history yet, so no established commit message convention.
- When you start committing, use short, imperative summaries (e.g., “Add retriever pipeline draft”).
- Pull requests should include a clear summary, relevant context, and links to related issues or docs.

## Configuration Notes
- Python version requirement is `>=3.14` per `pyproject.toml`. Keep this in mind when adding tooling or CI.
- Dependencies are managed in `pyproject.toml` via `uv add`; this updates `uv.lock`.

## Talk Constraints
- Demos assume local services via Docker Compose (Qdrant at `http://localhost:6333`, Postgres locally).
- Use Azure OpenAI for embeddings and chat; no placeholder or fallback embedding implementations.
- Keep data loading explicit and simple (no glob-heavy loaders or extra abstraction layers).
- Parent Document Retriever should return full parent documents (no parent chunking).
