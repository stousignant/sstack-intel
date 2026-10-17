---
# catalog-derived-begin
title: "exoharness/exo"
type: "repo-intel"
status: "active"
active: true
source_identity: "exoharness/exo"
source: "https://github.com/exoharness/exo"
source_categories: [["Reference Implementations","Generators & Meta-Harnesses"]]
source_occurrences: [["Reference Implementations","Generators & Meta-Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 87
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "c5c1963a3445417e64938c139da88edd9154075d"
readme_path: "README.md"
readme_url: "https://github.com/exoharness/exo/blob/c5c1963a3445417e64938c139da88edd9154075d/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/exoharness/exo/blob/c5c1963a3445417e64938c139da88edd9154075d/LICENSE"
---
# exoharness/exo
## Quick take
A recursive agent harness designed to inspect and evolve its own prompts, memory, tools, policies, and code while retaining canonical event history.
## Score
**87/100**
- **Harness relevance — 30/30:** Exo is explicitly a complete harness with tools, tasks, adapters, sandboxing, scheduling, and durable state.
- **Practical pattern value — 23/25:** Immutable event history, sandbox rewind, adapters, templates, and clone lineage offer reusable system patterns.
- **Evidence and maturity — 14/20:** Active metadata, CI badges, integration tests, and detailed documentation support an implemented but early project.
- **Novelty — 15/15:** Runtime self-modification with a protected canonical event log is unusually differentiated.
- **Risk-adjusted accessibility — 5/10:** MIT licensing helps, but Docker, API keys, remote chat surfaces, and recursive self-editing raise evaluation risk.
## Why it matters
- Offers a concrete safety pattern for self-modification: mutable harness components around an immutable event log.
- Combines long-running adapters, schedulers, sandbox snapshots, and agent lineage in one minimal architecture.
## Caveat
The project calls itself early-stage, and recursive self-editing plus remote adapters materially expand the security and operational review surface.
## Sources
[Repository](https://github.com/exoharness/exo) · [README](https://github.com/exoharness/exo/blob/c5c1963a3445417e64938c139da88edd9154075d/README.md) · [License](https://github.com/exoharness/exo/blob/c5c1963a3445417e64938c139da88edd9154075d/LICENSE)
