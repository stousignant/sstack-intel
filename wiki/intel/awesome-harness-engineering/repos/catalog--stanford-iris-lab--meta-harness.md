---
# catalog-derived-begin
title: "stanford-iris-lab/meta-harness"
type: "repo-intel"
status: "active"
active: true
source_identity: "stanford-iris-lab/meta-harness"
source: "https://github.com/stanford-iris-lab/meta-harness"
source_categories: [["Reference Implementations","Generators & Meta-Harnesses"]]
source_occurrences: [["Reference Implementations","Generators & Meta-Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 92
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "44b9942127847f7421db70d8c7e48407f09a3c70"
readme_path: "README.md"
readme_url: "https://github.com/stanford-iris-lab/meta-harness/blob/44b9942127847f7421db70d8c7e48407f09a3c70/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/stanford-iris-lab/meta-harness/blob/44b9942127847f7421db70d8c7e48407f09a3c70/LICENSE"
---
# stanford-iris-lab/meta-harness
## Quick take
The reference framework for automated search over task-specific model harnesses, with examples for memory systems and Terminal-Bench scaffolds.
## Score
**92/100**
- **Harness relevance — 30/30:** Meta-Harness directly searches and optimizes the code surrounding a fixed model.
- **Practical pattern value — 25/25:** Task-specific storage, retrieval, proposer wrappers, domain onboarding, and reference experiments are directly transferable.
- **Evidence and maturity — 15/20:** Institutional research, a paper, runnable examples, and active metadata are strong, though the release notes limited testing.
- **Novelty — 15/15:** End-to-end automated search over harness implementations is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and uv-based examples help, while adapting proposer logging and domain evaluation still requires engineering.
## Why it matters
- Frames harness components themselves as an optimization search space around a fixed model.
- Includes a reusable onboarding path for defining a new domain and wrapping proposer agents.
## Caveat
The authors describe this as cleaned research code tested only for basic execution, so operational robustness is not established.
## Sources
[Repository](https://github.com/stanford-iris-lab/meta-harness) · [README](https://github.com/stanford-iris-lab/meta-harness/blob/44b9942127847f7421db70d8c7e48407f09a3c70/README.md) · [License](https://github.com/stanford-iris-lab/meta-harness/blob/44b9942127847f7421db70d8c7e48407f09a3c70/LICENSE)
