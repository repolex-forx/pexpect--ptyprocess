# Repolex Knowledge Graph of pexpect/ptyprocess

RDF knowledge graph data for [pexpect/ptyprocess](https://github.com/pexpect/ptyprocess), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download pexpect/ptyprocess
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   ├── 5436e55d81d114edef254e79e3478306a1489da1
│   │   │   └── chunk-001.nq.gz
│   │   └── ee54ae2ee6bdd1e9f040dac79d799ae5b178e8fe
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   ├── 5436e55d81d114edef254e79e3478306a1489da1.nq.gz
│   │   └── ee54ae2ee6bdd1e9f040dac79d799ae5b178e8fe.nq.gz
│   └── repolex
│       ├── 5436e55d81d114edef254e79e3478306a1489da1
│       │   └── chunk-001.nq.gz
│       └── ee54ae2ee6bdd1e9f040dac79d799ae5b178e8fe
│           └── chunk-001.nq.gz
├── blob
│   ├── 05f7f90005016efc1102fc5d810b7e24aad9304f.nq.gz
│   ├── 265a1a432081d05398a5d9e04e41dcbe11d2a68e.nq.gz
│   ├── 29b4e43b569f3b78d6cfb316edee21583660bcc7.nq.gz
│   ├── 2d4c4570e0cbc17f1e61664f239aabe61957a092.nq.gz
│   ├── 34b391808af3e0c7772da90e30192d677d1521fb.nq.gz
│   ├── 393b2dd67d8b44e0eabae7dedd831bd7439fdd3e.nq.gz
│   ├── 3a5e13a6ca04231c12799e71e6e6346aabb68038.nq.gz
│   ├── 3a6268e8a6d26c2ff6c5e695d39402cfc5f34584.nq.gz
│   ├── 457f376337dc5b66f8b699f2fb005006318a6e62.nq.gz
│   ├── 4b46c269a4c299ae5d35e9e43eb35e9ffc82d4bb.nq.gz
│   ├── 522853464cba94a8d65dcae0c9350e4e0388895c.nq.gz
│   ├── 696e12621bfc1d000b50dd5957da0c7391affde4.nq.gz
│   ├── 6cc096a2dc33cd08aa8a1ad5f6865fb33fca92eb.nq.gz
│   ├── 78d19fdf8fd840c0debff6da7ad2440928c760a5.nq.gz
│   ├── 7d2b0e241dd9a4dc5a475f954b9ff56cb7957563.nq.gz
│   ├── 881c1bae897dcc1f3c570ef9f0b4ce64fc0c1c9d.nq.gz
│   ├── 8b77f690a1bb7b915e79f40209834ddff164b029.nq.gz
│   ├── 9c772742de96e441674e7ee221058d369c5d7976.nq.gz
│   ├── a8d05fe5a3d1a7ea2159a9a4fabb805966245a75.nq.gz
│   ├── aadbd62c801dc98425c2297cc4c6f12639bc2d5e.nq.gz
│   ├── ae73700373682bf2c761bc034ce91d3966b94beb.nq.gz
│   ├── b928e8608d1ad35b7fc9cb8e1476e8d25615869c.nq.gz
│   ├── cf280981b8088aea403567bc7aba8450e3d31514.nq.gz
│   ├── d69548d11600e857743a4838a02c73beb320b658.nq.gz
│   ├── d78f8a3e14a9975ceeb97d4290352cdb281d8ebf.nq.gz
│   ├── e633d0cddacdf1bfcdfe96bdd79f0c4cbfaa0e06.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── ed2df27da7225c9d642ce6a03a4c887b0e93aeaa.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   ├── 5436e55d81d114edef254e79e3478306a1489da1.nq.gz
│   └── ee54ae2ee6bdd1e9f040dac79d799ae5b178e8fe.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

16 directories, 41 files
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

## Source repository

[pexpect/ptyprocess](https://github.com/pexpect/ptyprocess)

---
*Parsed on 2026-09-20 by [repolex](https://repolex.ai)*
