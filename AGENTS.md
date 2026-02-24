# Repository Guidelines

## Project Structure & Module Organization
- `main.py` is the current entry point and the only Python module in the repo.
- `docs/` contains design notes and reference material (see `docs/parent-document-retriever.md`).
- `pyproject.toml` defines project metadata and runtime dependencies.
- `uv.lock` is the lockfile for reproducible installs.

If you add new modules, keep top-level runtime code in `main.py` and place supporting modules in a new package directory (e.g., `src/advanced_rag/`). Update `pyproject.toml` accordingly.

## Build, Test, and Development Commands
- `python main.py` runs the current entry point.
- `uv sync` installs dependencies from `pyproject.toml` and `uv.lock` (preferred if you use `uv`).
- `python -m pip install -e .` installs the project in editable mode if you are not using `uv`.

There is no build step yet; add one only if you introduce packaging or compiled assets.

## Coding Style & Naming Conventions
- Indentation: 4 spaces, no tabs (PEP 8).
- Naming: `snake_case` for functions and variables, `PascalCase` for classes, `UPPER_SNAKE_CASE` for constants.
- Keep modules small and purpose-specific; prefer clear, descriptive names over abbreviations.

No formatter or linter is configured yet. If you add one (e.g., Ruff or Black), document the exact commands here.

## Live-Coding Focus
- This repository supports live-coding segments for Konrad Bujak’s public speaking appearances.
- Avoid adding tests or test frameworks; keep the project lightweight and fast to run on stage.
- Prioritize clarity and minimal setup over completeness.

## Commit & Pull Request Guidelines
- There is no commit history yet, so no established commit message convention.
- When you start committing, use short, imperative summaries (e.g., “Add retriever pipeline draft”).
- Pull requests should include a clear summary, relevant context, and links to related issues or docs.

## Configuration Notes
- Python version requirement is `>=3.14` per `pyproject.toml`. Keep this in mind when adding tooling or CI.
- Dependencies are managed in `pyproject.toml`; update `uv.lock` when adding or upgrading packages.
