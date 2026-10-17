---
# catalog-derived-begin
title: "vshulcz/deja-vu"
type: "repo-intel"
status: "active"
active: true
source_identity: "vshulcz/deja-vu"
source: "https://github.com/vshulcz/deja-vu"
source_categories: [["Design Primitives","Memory & State"]]
source_occurrences: [["Design Primitives","Memory & State"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 85
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "b80ef79d9a9b893be71914fbac3c3227baaa8e94"
readme_path: "README.md"
readme_url: "https://github.com/vshulcz/deja-vu/blob/b80ef79d9a9b893be71914fbac3c3227baaa8e94/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/vshulcz/deja-vu/blob/b80ef79d9a9b893be71914fbac3c3227baaa8e94/LICENSE"
---
# vshulcz/deja-vu
## Quick take
A local cross-agent memory index that starts from existing session histories and injects relevant prior work through MCP, skills, and lifecycle hooks.
## Score
**85/100**
- **Harness relevance — 20/30:** Cross-session recall and action-time retrieval are substantial memory components for coding harnesses.
- **Practical pattern value — 25/25:** Retroactive parsers, cross-agent indexing, hook-time recall, rejection state, redaction, and handoff are directly transferable.
- **Evidence and maturity — 18/20:** Active metadata, releases, CI, reproducible benchmarks, broad harness support, and detailed docs provide strong evidence.
- **Novelty — 13/15:** Bootstrapping memory from existing local histories across many agents is a distinctive approach.
- **Risk-adjusted accessibility — 9/10:** MIT licensing and one local binary ease evaluation, though installation writes multiple agent integrations.
## Why it matters
- Avoids the cold-start problem by parsing histories already written by many coding agents.
- Adds action-time and failure-time recall while preserving rejection markers, provenance, and redaction.
## Caveat
Automatic installation writes MCP, hook, skill, or guidance configuration across detected agents, so preview and backup behavior should be reviewed.
## Sources
[Repository](https://github.com/vshulcz/deja-vu) · [README](https://github.com/vshulcz/deja-vu/blob/b80ef79d9a9b893be71914fbac3c3227baaa8e94/README.md) · [License](https://github.com/vshulcz/deja-vu/blob/b80ef79d9a9b893be71914fbac3c3227baaa8e94/LICENSE)
