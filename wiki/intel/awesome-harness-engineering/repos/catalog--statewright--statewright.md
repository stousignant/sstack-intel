---
# catalog-derived-begin
title: "statewright/statewright"
type: "repo-intel"
status: "active"
active: true
source_identity: "statewright/statewright"
source: "https://github.com/statewright/statewright"
source_categories: [["Design Primitives","Agent Loop"]]
source_occurrences: [["Design Primitives","Agent Loop"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 86
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "b2fb7fa7e4b59663350d79e78dea052953f5bd28"
readme_path: "README.md"
readme_url: "https://github.com/statewright/statewright/blob/b2fb7fa7e4b59663350d79e78dea052953f5bd28/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/statewright/statewright/blob/b2fb7fa7e4b59663350d79e78dea052953f5bd28/PATENTS.md"
---
# statewright/statewright
## Quick take
A state-machine control layer that narrows tools, models, budgets, and transitions as agents move through workflow phases.
## Score
**86/100**
- **Harness relevance — 28/30:** Constrains agent execution with deterministic state, tool, model, budget, transition, and approval rules.
- **Practical pattern value — 24/25:** Per-state tool surfaces, guarded transitions, managed restarts, approval routing, and an escape hatch are reusable.
- **Evidence and maturity — 14/20:** The project documents releases, architecture, multiple host integrations, self-hosting, and a limited benchmark.
- **Novelty — 15/15:** Hard state-machine enforcement across existing agent interfaces is unusually differentiated.
- **Risk-adjusted accessibility — 5/10:** Mixed Apache and FSL licensing, patent terms, hand-authored workflows, and host-specific enforcement increase evaluation risk.
## Why it matters
- Turns planning, implementation, testing, and approval phases into enforceable capabilities rather than prompt suggestions.
- Supports several agent hosts through a shared executor while preserving explicit transition and escape semantics.
## Caveat
The published result uses only five SWE-bench tasks, restrictive workflows can stall agents, and gateway code has FSL and patent considerations.
## Sources
[Repository](https://github.com/statewright/statewright) · [README](https://github.com/statewright/statewright/blob/b2fb7fa7e4b59663350d79e78dea052953f5bd28/README.md) · [License](https://github.com/statewright/statewright/blob/b2fb7fa7e4b59663350d79e78dea052953f5bd28/PATENTS.md)
