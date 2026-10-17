---
# catalog-derived-begin
title: "neosigmaai/auto-harness"
type: "repo-intel"
status: "active"
active: true
source_identity: "neosigmaai/auto-harness"
source: "https://github.com/neosigmaai/auto-harness"
source_categories: [["Reference Implementations","Generators & Meta-Harnesses"]]
source_occurrences: [["Reference Implementations","Generators & Meta-Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "d1e3260bc43d8b4e2decdf6a41789ae1587c9e80"
readme_path: "README.md"
readme_url: "https://github.com/neosigmaai/auto-harness/blob/d1e3260bc43d8b4e2decdf6a41789ae1587c9e80/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/neosigmaai/auto-harness/blob/d1e3260bc43d8b4e2decdf6a41789ae1587c9e80/LICENSE"
---
# neosigmaai/auto-harness
## Quick take
A benchmark-driven loop that lets a coding agent modify an agent implementation, mine failures, maintain regressions, and gate improvements.
## Score
**89/100**
- **Harness relevance — 30/30:** The repository implements an automated harness-optimization loop around agents and benchmarks.
- **Practical pattern value — 25/25:** Failure mining, held-out gates, suite promotion, trace isolation, and iteration records are directly transferable.
- **Evidence and maturity — 14/20:** README documents several benchmark integrations and measured examples, but the project is young and lightly institutionalized.
- **Novelty — 14/15:** Letting a coding agent evolve another agent under self-maintained regression gates is highly differentiated.
- **Risk-adjusted accessibility — 6/10:** MIT licensing helps, while full benchmark runs, sandboxes, datasets, and model credentials impose substantial setup.
## Why it matters
- Makes train/test trace separation and multi-stage regression gating explicit in an autonomous improvement loop.
- Keeps iteration results and learnings in simple inspectable workspace artifacts.
## Caveat
Meaningful evaluation can require large benchmark suites, external datasets, containers or sandbox providers, and model credentials.
## Sources
[Repository](https://github.com/neosigmaai/auto-harness) · [README](https://github.com/neosigmaai/auto-harness/blob/d1e3260bc43d8b4e2decdf6a41789ae1587c9e80/README.md) · [License](https://github.com/neosigmaai/auto-harness/blob/d1e3260bc43d8b4e2decdf6a41789ae1587c9e80/LICENSE)
