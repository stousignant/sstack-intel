---
# catalog-derived-begin
title: "claw-eval/claw-eval"
type: "repo-intel"
status: "active"
active: true
source_identity: "claw-eval/claw-eval"
source: "https://github.com/claw-eval/claw-eval"
source_categories: [["Evals & Verification"]]
source_occurrences: [["Evals & Verification"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "5680b8b11ff2ee5dd2b07b89086a29a5c5c984d7"
readme_path: "README.md"
readme_url: "https://github.com/claw-eval/claw-eval/blob/5680b8b11ff2ee5dd2b07b89086a29a5c5c984d7/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/claw-eval/claw-eval/blob/5680b8b11ff2ee5dd2b07b89086a29a5c5c984d7/LICENSE"
---
# claw-eval/claw-eval
## Quick take
A rigorous autonomous-agent benchmark built around human-verified rubrics and three-run consistency.
## Score
**89/100**
- **Harness relevance — 30/30:** This is explicitly an evaluation harness for autonomous agents across completion, safety, and robustness.
- **Practical pattern value — 22/25:** Human-verified rubrics, repeated trials, fixtures, and trajectory auditing are reusable evaluation patterns.
- **Evidence and maturity — 17/20:** The README describes 300 tasks, 2,159 rubrics, a paper, datasets, releases, and an active audit.
- **Novelty — 13/15:** Pass^3 scoring combines strict multi-trial consistency with full-trajectory safety and completion review.
- **Risk-adjusted accessibility — 7/10:** MIT helps, but sandbox setup, large fixtures, model keys, and grader dependencies raise evaluation cost.
## Why it matters
- Provides a concrete model for evaluating completion, safety, and robustness together.
- Uses strict repeated-trial credit to reduce lucky-pass benchmark noise.
## Caveat
The README says reproducibility is still being audited, and full runs require external models, graders, web access, and large fixtures.
## Sources
[Repository](https://github.com/claw-eval/claw-eval) · [README](https://github.com/claw-eval/claw-eval/blob/5680b8b11ff2ee5dd2b07b89086a29a5c5c984d7/README.md) · [License](https://github.com/claw-eval/claw-eval/blob/5680b8b11ff2ee5dd2b07b89086a29a5c5c984d7/LICENSE)
