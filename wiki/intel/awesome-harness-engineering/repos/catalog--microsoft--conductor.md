---
# catalog-derived-begin
title: "microsoft/conductor"
type: "repo-intel"
status: "active"
active: true
source_identity: "microsoft/conductor"
source: "https://github.com/microsoft/conductor"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 90
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "ff4b3123cd4e0204373ef0be2ea7de6338164598"
readme_path: "README.md"
readme_url: "https://github.com/microsoft/conductor/blob/ff4b3123cd4e0204373ef0be2ea7de6338164598/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/microsoft/conductor/blob/ff4b3123cd4e0204373ef0be2ea7de6338164598/LICENSE"
---
# microsoft/conductor
## Quick take
A version-controlled multi-agent workflow runner that keeps routing deterministic while supporting parallelism, human gates, and live operations.
## Score
**90/100**
- **Harness relevance — 29/30:** Defines and runs complete multi-agent workflows with routing, gates, limits, state, and operator controls.
- **Practical pattern value — 24/25:** Versioned YAML, deterministic conditions, parallel groups, reusable subflows, termination semantics, and validation are transferable.
- **Evidence and maturity — 17/20:** The active Microsoft MIT project documents CI, release installation, many examples, provider contracts, and operator interfaces.
- **Novelty — 13/15:** Deterministic no-LLM orchestration across several agent providers with live human guidance is distinctive.
- **Risk-adjusted accessibility — 7/10:** Quick installation and dry runs help, but several providers and sandbox modes remain experimental or subscription-dependent.
## Why it matters
- Separates orchestration decisions into validated YAML and first-match expressions rather than spending model calls on routing.
- Combines reusable subworkflows, explicit termination, safety limits, dashboards, and fleet control in one execution surface.
## Caveat
Provider capabilities differ materially, and the README labels Claude Agent SDK, Hermes, and Azure Container Apps integrations experimental.
## Sources
[Repository](https://github.com/microsoft/conductor) · [README](https://github.com/microsoft/conductor/blob/ff4b3123cd4e0204373ef0be2ea7de6338164598/README.md) · [License](https://github.com/microsoft/conductor/blob/ff4b3123cd4e0204373ef0be2ea7de6338164598/LICENSE)
