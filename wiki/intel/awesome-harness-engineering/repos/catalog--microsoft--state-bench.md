---
# catalog-derived-begin
title: "microsoft/STATE-Bench"
type: "repo-intel"
status: "active"
active: true
source_identity: "microsoft/STATE-Bench"
source: "https://github.com/microsoft/STATE-Bench"
source_categories: [["Evals & Verification"]]
source_occurrences: [["Evals & Verification"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 82
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "5644b1838d96bc4483da29642d058ecaa6f80f7f"
readme_path: "README.md"
readme_url: "https://github.com/microsoft/STATE-Bench/blob/5644b1838d96bc4483da29642d058ecaa6f80f7f/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/microsoft/STATE-Bench/blob/5644b1838d96bc4483da29642d058ecaa6f80f7f/LICENSE"
---
# microsoft/STATE-Bench
## Quick take
A stateful enterprise-agent benchmark combining sandbox databases, simulated users, policy compliance, final-state verification, UX, reliability, and cost.
## Score
**82/100**
- **Harness relevance — 23/30:** A complete evaluation harness for tool-using enterprise agents rather than an operational agent runtime.
- **Practical pattern value — 22/25:** Task-local databases, simulated users, policy-sensitive tools, final-state checks, repeated runs, UX judging, and cost tracking are reusable.
- **Evidence and maturity — 16/20:** Microsoft-backed MIT benchmark with 450 documented tasks and two tracks, though its datasets are synthetic.
- **Novelty — 13/15:** The learning track reuses one simulator while adding trajectories and retrieval hooks for memory, skills, and prompt optimization.
- **Risk-adjusted accessibility — 8/10:** Open licensing and clear tracks aid use, but full repeated evaluation and judge/model calls can be resource-intensive.
## Why it matters
- It tests both conversational procedure and database outcomes, avoiding a purely textual success signal.
- The shared learning track offers a controlled way to compare memories, skills, and prompt optimizations.
## Caveat
The tasks and datasets are synthetically generated, so benchmark gains may not transfer to real enterprise users, policies, or system integrations.
## Sources
[Repository](https://github.com/microsoft/STATE-Bench) · [README](https://github.com/microsoft/STATE-Bench/blob/5644b1838d96bc4483da29642d058ecaa6f80f7f/README.md) · [License](https://github.com/microsoft/STATE-Bench/blob/5644b1838d96bc4483da29642d058ecaa6f80f7f/LICENSE)
