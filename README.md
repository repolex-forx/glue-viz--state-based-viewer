# Repolex Knowledge Graph of glue-viz/state-based-viewer

RDF knowledge graph data for [glue-viz/state-based-viewer](https://github.com/glue-viz/state-based-viewer), parsed by [repolex](https://repolex.ai).

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
rlex download glue-viz/state-based-viewer
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 4a38f6190388f07bfd1f88bcdda5d782e9c60139
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 4a38f6190388f07bfd1f88bcdda5d782e9c60139
│           └── chunk-001.nq.gz
├── blob
│   ├── 41afcb18715aef01e191d64fca5b9adb51a8165a.nq.gz
│   ├── 544a6af62fba15d41efba06a73fcf3ad902bd2b3.nq.gz
│   ├── 6358a6aa261c691b70d1dfb72ba53ac19e759fc4.nq.gz
│   ├── 751f0870663c1c8c46c7618d074e9656e286bac6.nq.gz
│   ├── 8934d34b800163cf81ee219ea0fb7eba788c7ec6.nq.gz
│   ├── a10ea59a21fe6932f0db99bdaefde8f138ab0b98.nq.gz
│   ├── bd935fe03fd536f4f9a8da4e4473790df743a1eb.nq.gz
│   ├── ce0292efec61e77cf6c0883bbd91b520caece282.nq.gz
│   ├── d753ee0bc22de6c5bae0431d11c7aba2a3f72792.nq.gz
│   └── ef3cb0e9e7456e496639badfdfdccf223d7807a8.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 4a38f6190388f07bfd1f88bcdda5d782e9c60139.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 16 files
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

[glue-viz/state-based-viewer](https://github.com/glue-viz/state-based-viewer)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
