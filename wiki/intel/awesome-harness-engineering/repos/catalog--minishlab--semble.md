---
# catalog-derived-begin
title: "MinishLab/semble"
type: "repo-intel"
status: "active"
active: true
source_identity: "MinishLab/semble"
source: "https://github.com/MinishLab/semble"
source_categories: [["Design Primitives","Context Delivery & Compaction"]]
source_occurrences: [["Design Primitives","Context Delivery & Compaction"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "8e52ea7fa67ed86650707715b6b18d3dac1835d5"
readme_path: "README.md"
readme_url: "https://github.com/MinishLab/semble/blob/8e52ea7fa67ed86650707715b6b18d3dac1835d5/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/MinishLab/semble/blob/8e52ea7fa67ed86650707715b6b18d3dac1835d5/LICENSE"
---
# MinishLab/semble
## Quick take
A local CPU code-search layer that returns narrow agent-ready snippets through CLI, MCP, or a dedicated subagent.
## Score
**81/100**
- **Harness relevance — 21/30:** Supplies token-efficient code retrieval to agents through MCP, CLI instructions, or a search subagent.
- **Practical pattern value — 23/25:** Code-aware chunking, hybrid semantic and lexical retrieval, result reranking, and narrow snippets are reusable.
- **Evidence and maturity — 16/20:** The active MIT project documents installation, benchmarks across repositories and languages, multiple interfaces, and methodology.
- **Novelty — 12/15:** A compact CPU-only embedding and BM25 fusion tuned for agent code search is a distinctive combination.
- **Risk-adjusted accessibility — 9/10:** No API key or GPU is required, though first use downloads and caches an embedding model.
## Why it matters
- Combines tree-sitter chunking, compact code embeddings, BM25, reciprocal-rank fusion, and code-aware reranking.
- Its integration installer can add MCP, instruction-file, or subagent access for several coding clients.
## Caveat
The speed, quality, and token-savings figures come from the project's own benchmark, and initial use requires a model download.
## Sources
[Repository](https://github.com/MinishLab/semble) · [README](https://github.com/MinishLab/semble/blob/8e52ea7fa67ed86650707715b6b18d3dac1835d5/README.md) · [License](https://github.com/MinishLab/semble/blob/8e52ea7fa67ed86650707715b6b18d3dac1835d5/LICENSE)
