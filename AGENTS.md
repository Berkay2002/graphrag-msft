# AGENTS.md

## Project Overview

GraphRAG is a modular graph-based Retrieval-Augmented Generation (RAG) system developed by Microsoft. It uses LLMs to extract structured data from unstructured text, creating a knowledge graph that can be queried for more comprehensive and context-aware answers.

- **Key Technologies**: Python (3.10-3.12), `uv` (package management), `poethepoet` (task management), `ruff` (linting/formatting), `pyright` (type checking), `pytest` (testing).
- **Architecture**: Modular design with factories for cache, callbacks, config, index, logger, storage, and vector stores.

## Setup Commands

- **Install dependencies**: `uv sync`
- **Initialize project**: `uv run poe init`
- **Start Azurite (for tests)**: `./scripts/start-azurite.sh`

## Development Workflow

- **Run Indexing**: `uv run poe index --root <path> [args]`
- **Run Query**: `uv run poe query --root <path> --method <global|local|drift> --query "<question>"`
- **Run Prompt Tuning**: `uv run poe prompt_tune --root <path> [args]`
- **Update Index**: `uv run poe update --root <path> [args]`
- **Format Code**: `uv run poe format`
- **Fix Linting/Formatting**: `uv run poe fix` or `uv run poe fix_unsafe`
- **Static Checks (Lint/Type/Format)**: `uv run poe check`

## Testing Instructions

- **Run all tests**: `uv run poe test`
- **Unit tests**: `uv run poe test_unit`
- **Integration tests**: `uv run poe test_integration`
- **Smoke tests**: `uv run poe test_smoke`
- **Notebook tests**: `uv run poe test_notebook`
- **Verbs tests**: `uv run poe test_verbs`
- **Run specific tests**: `uv run poe test_only <pattern>`
- **Coverage report**: `uv run poe coverage_report`

## Code Style

- **Linter/Formatter**: `ruff`
- **Type Checker**: `pyright`
- **Conventions**: Follows NumPy docstring convention.
- **Configuration**: See `pyproject.toml` for specific `ruff` and `pyright` rules.

## Build and Deployment

- **Build package**: `uv build`
- **Build documentation**: `uv run poe build_docs`
- **Serve documentation**: `uv run poe serve_docs`

## Pull Request Guidelines

- **Versioning**: Uses `semversioner`. Every PR must include a change file.
- **Add change file**: `uv run semversioner add-change -t <major|minor|patch> -d "<description>"`
- **Pre-commit checks**: Always run `uv run poe check` and `uv run poe test` before submitting.

## Unified Search App (Subproject)

Located in `unified-search-app/`.

- **Setup**: `cd unified-search-app && uv sync`
- **Run App**: `uv run poe start` (uses Streamlit)
- **Configuration**: Requires `DATA_ROOT` or `BLOB_ACCOUNT_NAME` environment variables.
- **Data Format**: Requires a `listing.json` file in the data root.

## Thesis Project (Subproject)

Located in `agentic-graphrag-thesis/`.

- **Topic**: "Agentic RAG & Knowledge Graphs for Test Scope Analysis"
- **Institution**: Linköping University (Master's Thesis in Computer Science)
- **External Partner**: Ericsson
- **Setup**: `cd agentic-graphrag-thesis && uv sync`
- **Documentation**: See `agentic-graphrag-thesis/AGENTS.md` and `agentic-graphrag-thesis/thesis-paper/` for detailed thesis content
- **Purpose**: Research implementation of agent-orchestrated GraphRAG systems for automated test case recommendation in enterprise software development

## Additional Notes

- **Config Migration**: Run `graphrag init --root [path] --force` between minor version bumps.
- **Expensive Operations**: Indexing can be costly; start with small datasets.
- **Environment Variables**: Use a `.env` file at the root or in the project directory.
