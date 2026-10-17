---
# catalog-derived-begin
title: "microsoft/SkillOpt"
type: "repo-intel"
status: "active"
active: true
source_identity: "microsoft/SkillOpt"
source: "https://github.com/microsoft/SkillOpt"
source_categories: [["Design Primitives","Skills & MCP"]]
source_occurrences: [["Design Primitives","Skills & MCP"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "79124b37e9a6371e13b753f8bcd7adb1e493ade1"
readme_path: "README.md"
readme_url: "https://github.com/microsoft/SkillOpt/blob/79124b37e9a6371e13b753f8bcd7adb1e493ade1/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/microsoft/SkillOpt/blob/79124b37e9a6371e13b753f8bcd7adb1e493ade1/LICENSE"
---
# microsoft/SkillOpt
## Quick take
A text-space optimizer that improves reusable agent skills through scored rollouts, bounded edits, and validation-gated selection.
## Score
**81/100**
- **Harness relevance — 20/30:** SkillOpt is a substantial evaluation and optimization component for reusable agent skills across several harnesses.
- **Practical pattern value — 25/25:** Trajectory-driven bounded edits, epoch loops, validation gates, held-out selection, and compact deployment artifacts are directly transferable.
- **Evidence and maturity — 14/20:** Microsoft maintains the project; the README documents a v0.1.0 release, PyPI package, six benchmarks, seven models, and three harnesses.
- **Novelty — 15/15:** Treating natural-language skills as trainable state with weight-training discipline is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and PyPI installation ease entry, but optimization requires repeated model rollouts, scoring, and validation resources.
## Why it matters
- Turns skill evolution into a reproducible train-and-evaluate loop rather than one-shot prompt editing.
- Deploys a compact best_skill.md without adding inference-time model calls.
## Caveat
The reported gains and best-or-tied-best results are README-level evidence, and reproducing them can incur substantial model and benchmark cost.
## Sources
[Repository](https://github.com/microsoft/SkillOpt) · [README](https://github.com/microsoft/SkillOpt/blob/79124b37e9a6371e13b753f8bcd7adb1e493ade1/README.md) · [License](https://github.com/microsoft/SkillOpt/blob/79124b37e9a6371e13b753f8bcd7adb1e493ade1/LICENSE)
