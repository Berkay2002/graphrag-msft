# AGENTS.md

## Project Overview

This is a thesis project exploring Agentic GraphRAG - an extension of Microsoft's GraphRAG system that integrates agentic AI frameworks for enhanced reasoning and autonomous query handling.

- **Key Technologies**: Python (3.10-3.12), `uv` (package management), GraphRAG (parent project), PyAutoGen, LangChain.
- **Purpose**: Research and development of agent-based approaches to graph-based retrieval-augmented generation.
- **Architecture**: Built on top of the GraphRAG library with additional agent orchestration capabilities.

## Setup Commands

- **Install dependencies**: `uv sync` (from the `agentic-graphrag-thesis/` directory)
- **Activate environment**: `source .venv/bin/activate` (if needed)

## Project Structure

```
agentic-graphrag-thesis/
├── pyproject.toml         # Project configuration and dependencies
├── src/
│   └── agentic_graphrag/  # Main package directory
│       └── __init__.py
├── thesis-paper/          # Master's thesis paper (LaTeX)
│   ├── thesis.tex         # Main thesis document
│   ├── intro.md           # Introduction chapter
│   ├── theory.tex         # Theory chapter
│   ├── method.tex         # Methodology chapter
│   ├── references.bib     # Bibliography
│   ├── settings.tex       # LaTeX settings
│   └── figures/           # TikZ diagrams and figures
└── AGENTS.md              # This file
```

## Development Workflow

This thesis project depends on the parent GraphRAG library (installed as an editable dependency).

### Working with GraphRAG

Since GraphRAG is installed as an editable dependency, you can:
- Modify the parent GraphRAG library and changes will be reflected immediately
- Use all GraphRAG functionality from this thesis project
- Extend GraphRAG with agent-based capabilities

### Running GraphRAG Commands

From the thesis directory, you can run GraphRAG commands:
- **Run Indexing**: `uv run graphrag index --root <path> [args]`
- **Run Query**: `uv run graphrag query --root <path> --method <global|local|drift> --query "<question>"`

### Development Best Practices

- Keep thesis-specific code in `src/agentic_graphrag/`
- Document experiments and findings in separate markdown files
- Use version control to track progress
- MaintainPaper

### Title
**"Agentic RAG & Knowledge Graphs for Test Scope Analysis"**  
Master's Thesis in Computer Science, Linköping University (LiU)

### Author
Berkay Orhan

### Supervisors
- **Internal**: TBD (Linköping University)
- **External**: Dimitris Rentas, Ericsson AI Technology Leader

### Research Focus

The thesis addresses the problem of **test scope analysis** in large-scale enterprise software development, specifically at Ericsson. Key research areas include:

1. **Knowledge Graph Ontology Design**: Modeling semantic dependencies between unstructured requirements and structured test artifacts
2. **Agent-Orchestrated GraphRAG**: Combining vector-based semantic retrieval with graph-based structural reasoning
3. **Autonomous Test Recommendation**: Using agentic AI architectures to automate test case retrieval and coverage gap identification
4. **Explainable AI for Software Engineering**: Providing transparent rationales for automated test scope recommendations

### Research Questions

- **RQ1**: What ontology design is required to model semantic dependencies between requirements and test artifacts in a Knowledge Graph?
- **RQ2**: How does agent-orchestrated GraphRAG improve retrieval accuracy compared to keyword-based and vector-only RAG methods?
- **RQ3**: How do Ericsson software practitioners perceive the accuracy and utility of automated test recommendations?

### Key Technologies in Thesis

- **Large Language Models (LLMs)**: For semantic understanding of requirements and test cases
- **Retrieval-Augmented Generation (RAG)**: Enhancing LLMs with external knowledge retrieval
- **Knowledge Graphs**: Structured representation of software artifacts and their relationships
- **Agentic AI Architecture**: Autonomous agents orchestrating multi-step reasoning and tool execution
- **Microsoft GraphRAG**: Foundation for implementing hybrid retrieval systems

### LaTeX Build Commands

From the `thesis-paper/` directory:
- **Compile thesis**: `xelatex thesis.tex` or `pdflatex thesis.tex`
- **Process bibliography**: `biber thesis`
- **Full build**: `make` (if Makefile is configured)
- **Watch mode**: `make watch` (auto-compile on changes)

### Figures

The thesis includes TikZ diagrams illustrating:
- Agent architecture (`agent_architecture.tikz`)
- RAG pipeline (`rag_pipeline.tikz`)
- Knowledge graph ontology (`kg_ontology.tikz`)
- Semantic chunking (`semantic_chunking.tikz`)
- Embeddings and cosine similarity (`embeddings_cosine.tikz`)
- HNSW graph structure (`hnsw_graph.tikz`)
- Hybrid search architecture (`hybrid_search.tikz`)

Track your experiments and results:
- Experiment 1: [Description]
- Experiment 2: [Description]

### References

List relevant papers and resources for your thesis work.

## Additional Notes

- This project is Python 3.10-3.12 compatible
- Uses `uv` for fast, reliable dependency management
- Inherits GraphRAG's configuration and testing frameworks
- See parent `AGENTS.md` for GraphRAG-specific commands and workflows
