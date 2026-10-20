# Repolex Knowledge Graph of simonw/llm-tools-datasette

RDF knowledge graph data for [simonw/llm-tools-datasette](https://github.com/simonw/llm-tools-datasette), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download simonw/llm-tools-datasette
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 3223970dd1d82e30c72f7fbcf692d63aa34b0cc0
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 3223970dd1d82e30c72f7fbcf692d63aa34b0cc0
│           └── chunk-001.nq.gz
├── blob
│   ├── 1a0816b204c92867a0b2ce71d6b72096c4247113.nq.gz
│   ├── 261eeb9e9f8b2b4b0d119366dda99c6fd7d35c64.nq.gz
│   ├── 4ba6e475df1d0706dfb2df2a859ecaaa6244ef67.nq.gz
│   ├── ab2a75886990f5f2829a527280b9031361e0fcfb.nq.gz
│   ├── d6decb0e75d7773b2568c58d69ca76d1a7e5fd22.nq.gz
│   ├── d7b2eacc7d31a30c2e87874d1059e359a68fa500.nq.gz
│   ├── ed238f90a640dfb484bece035dcaa0462628fd38.nq.gz
│   └── ee37c6eec4b9a881b95a996aea2840d1656ca986.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 3223970dd1d82e30c72f7fbcf692d63aa34b0cc0.nq.gz
├── issue
│   └── issue.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 15 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[simonw/llm-tools-datasette](https://github.com/simonw/llm-tools-datasette)

---
*Parsed on 2026-10-20 by [repolex](https://repolex.ai)*
