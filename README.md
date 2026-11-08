# Repolex Knowledge Graph of UKPLab/M4FC

RDF knowledge graph data for [UKPLab/M4FC](https://github.com/UKPLab/M4FC), parsed by [repolex](https://repolex.ai).

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
rlex download UKPLab/M4FC
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 185dcd9c589eb25e2b5ebd3afa58c1492f55746f
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 185dcd9c589eb25e2b5ebd3afa58c1492f55746f
│           └── chunk-001.nq.gz
├── blob
│   ├── 19cff15231eae87275375516fdb914566fb7b295.nq.gz
│   ├── 1c80fcfc8e6f0720c79e90872ae6f02993ea607b.nq.gz
│   ├── 229edba242bb190698662cdce6bdacde9f0769fe.nq.gz
│   ├── 296767e0ce42b364c4b45e5b0c144a5af5740559.nq.gz
│   ├── 2ca9edf5dc8abd33bf10fe723239522915b45144.nq.gz
│   ├── 2d10b3a080b100518ddc97afde18e021a15cebef.nq.gz
│   ├── 6390989892153e2bc8e7f66b79dd03b92f7ba76f.nq.gz
│   ├── 64798fabf465bc397df88f0756de1047a5f25d4e.nq.gz
│   ├── 66db7a6c9e64f32ad3022c443c8b78ab4b9b4c66.nq.gz
│   ├── 6877876a6523562b3db8ea11d00d7aaf48751a79.nq.gz
│   ├── 692e87ba8c31953bae1c073e4f71c9789e7c6bf5.nq.gz
│   ├── 6caa20d9f9e7866490c2f9039e8c313a15967389.nq.gz
│   ├── 732ef928cdd420bc36146193878e4da74b9751d9.nq.gz
│   ├── 7c3039212dcd2e1cd004ac7290998a9b843c6fcf.nq.gz
│   ├── 7d4f96c54aa155a17387e64501c50b6a0469932c.nq.gz
│   ├── 859902f137250979c8b53230a3b975adc28386a8.nq.gz
│   ├── 8b137891791fe96927ad78e64b0aad7bded08bdc.nq.gz
│   ├── 91ed5f6902216a58379fffc2eb974c17027d239d.nq.gz
│   ├── 922dd718d5f46e4be2e6e5567cc2b84bf08855df.nq.gz
│   ├── 9b3703a912d40f58fb0fb57d20742e53d9fe7671.nq.gz
│   ├── a574d155b5186edc7f506d4acdb559063b54d7b2.nq.gz
│   ├── b159b455e95b6a1efd79e56b8ffb7f2690f92a07.nq.gz
│   ├── b9fb35d5c5661385dd69a54d4270a308a3faafb5.nq.gz
│   ├── c08a79032592be8f5e7318991b0242323389469d.nq.gz
│   ├── c6718de5c5ae59d2c22141a147f5afba41af9cbb.nq.gz
│   ├── d62fc66df4b9acdd5381753fde4173a5775b1ddf.nq.gz
│   ├── d8fb6777790fba37f10716b90cfdc4ca9f1d37ed.nq.gz
│   ├── dc9928772cfa77a170c5a3cfb198482ce7eff25a.nq.gz
│   ├── de65a4e70563471efee8c443482dd59179e2abd6.nq.gz
│   ├── e181a7029d39ef49be7f1d2a54db8e4f09d7619f.nq.gz
│   ├── e581f3402ab7f98e7fd64c08c15e08ad4e1e0479.nq.gz
│   ├── ea5af82b715f37daa4f707db6966972036da33e6.nq.gz
│   ├── ea6d05ea8f9d193059c6b06318dbcc5229e7b33a.nq.gz
│   ├── ed3a9d377ba3c30e6eb8b2a35e08e8dc814a0725.nq.gz
│   ├── f02e92ceddc131f0150d1cf15191b5d3d7cc6384.nq.gz
│   ├── f080a586ba30795abf47ef0c2794ba9f709c4ba9.nq.gz
│   ├── f133c0c250df14a59780ca4a16f24ef1de867fdf.nq.gz
│   └── f979498bd15c2f3f64d42ce12ca1edcecec05407.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 185dcd9c589eb25e2b5ebd3afa58c1492f55746f.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

12 directories, 45 files
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

[UKPLab/M4FC](https://github.com/UKPLab/M4FC)

---
*Parsed on 2026-11-08 by [repolex](https://repolex.ai)*
