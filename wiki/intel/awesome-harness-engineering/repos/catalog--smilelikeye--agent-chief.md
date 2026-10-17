---
# catalog-derived-begin
title: "SmileLikeYe/agent-chief"
type: "repo-intel"
status: "active"
active: true
source_identity: "SmileLikeYe/agent-chief"
source: "https://github.com/SmileLikeYe/agent-chief"
source_categories: [["Design Primitives","Human-in-the-Loop"]]
source_occurrences: [["Design Primitives","Human-in-the-Loop"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 87
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "d46072a804ff16aa7ce87751b82178f13fb973be"
readme_path: "README.md"
readme_url: "https://github.com/SmileLikeYe/agent-chief/blob/d46072a804ff16aa7ce87751b82178f13fb973be/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/SmileLikeYe/agent-chief/blob/d46072a804ff16aa7ce87751b82178f13fb973be/LICENSE"
---
# SmileLikeYe/agent-chief
## Quick take
A local-first chief-of-staff layer that filters events, times interruptions, dispatches agents with verification, and curates lower-priority information.
## Score
**87/100**
- **Harness relevance — 25/30:** Acts as an orchestration and attention-control layer between agents, event sources, memory, and a human operator.
- **Practical pattern value — 23/25:** Staged filtering, scene thresholds, shadow mode, verified dispatch, editable policy, cost traces, and held-out preference evaluation transfer well.
- **Evidence and maturity — 17/20:** MIT project documents hundreds of tests, golden-set and cohort evaluations, deterministic demos, and reproducible metrics, though it is new.
- **Novelty — 14/15:** Combining interruption budgeting, dispatch verification, memory curation, and explainable adaptive policy is unusually distinctive.
- **Risk-adjusted accessibility — 8/10:** A local SQLite/Markdown deployment and offline demo are approachable; live judging and webhook integrations introduce model cost and trust boundaries.
## Why it matters
- Its cheap-rules-first escalation and shadow-mode rollout are strong patterns for attention-safe automation.
- Decision traces, versioned prompts, eval diffs, and held-out preference tests make policy learning unusually inspectable.
## Caveat
README metrics come from the project's committed demos and evaluations, not this review; real event distributions, noisy feedback, and integration failures may behave differently.
## Sources
[Repository](https://github.com/SmileLikeYe/agent-chief) · [README](https://github.com/SmileLikeYe/agent-chief/blob/d46072a804ff16aa7ce87751b82178f13fb973be/README.md) · [License](https://github.com/SmileLikeYe/agent-chief/blob/d46072a804ff16aa7ce87751b82178f13fb973be/LICENSE)
