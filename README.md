# Repolex Knowledge Graph of deepset-ai/hacknight

RDF knowledge graph data for [deepset-ai/hacknight](https://github.com/deepset-ai/hacknight), parsed by [repolex](https://repolex.ai).

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
rlex download deepset-ai/hacknight
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── f4f62a2ecc9e37fc583e44409b42485b75c1b449
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── f4f62a2ecc9e37fc583e44409b42485b75c1b449
│           └── chunk-001.nq.gz
├── blob
│   ├── 23da26f7dbe359750315439afb4fe74c2e908667.nq.gz
│   ├── 3c5621dca282916cf90991e9e781184eb5511690.nq.gz
│   ├── 3d8637192ba0442d34b5e2181c1a921ec4c78bc8.nq.gz
│   ├── 5525668e1b687502a789c45814173addd98b41e2.nq.gz
│   ├── 64a9896cd3f02e07d0c12a4f1edd2d9fba4af9f3.nq.gz
│   ├── 6d322b9ea8351d41bdf00a9cc7267a9481fa43d9.nq.gz
│   ├── 6d8de7ce82f90c711221d7c151e2d1013c78a310.nq.gz
│   ├── bc51aaf614038fdb042dc27a5622d59161cb9648.nq.gz
│   ├── e63c139fee92f1a7b59e0a28df64002f3991adcc.nq.gz
│   └── eb3fa9c1cbae0f056362c572dafb124902b7952b.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── f4f62a2ecc9e37fc583e44409b42485b75c1b449.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 17 files
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

[deepset-ai/hacknight](https://github.com/deepset-ai/hacknight)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
