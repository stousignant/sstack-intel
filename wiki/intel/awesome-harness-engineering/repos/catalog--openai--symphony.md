---
# catalog-derived-begin
title: "openai/symphony"
type: "repo-intel"
status: "active"
active: true
source_identity: "openai/symphony"
source: "https://github.com/openai/symphony"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 85
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "8001b52e3062495a16e520e4ceaf8f9de868c4d0"
readme_path: "README.md"
readme_url: "https://github.com/openai/symphony/blob/8001b52e3062495a16e520e4ceaf8f9de868c4d0/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/openai/symphony/blob/8001b52e3062495a16e520e4ceaf8f9de868c4d0/LICENSE"
---
# openai/symphony
## Quick take
A specification and experimental implementation for turning queued project work into isolated, evidence-backed coding-agent runs.
## Score
**85/100**
- **Harness relevance — 30/30:** It coordinates isolated autonomous implementation runs from project work through proof, review, and landing.
- **Practical pattern value — 23/25:** Work-queue polling, isolated runs, proof bundles, acceptance, and safe landing are directly transferable patterns.
- **Evidence and maturity — 12/20:** OpenAI provides an Apache-licensed specification and experimental reference implementation, but labels it an engineering preview.
- **Novelty — 13/15:** The work-management abstraction shifts supervision from agent turns to evidence-backed project outcomes.
- **Risk-adjusted accessibility — 7/10:** The open specification and license aid inspection, while the trusted-environment warning and experimental implementation add risk.
## Why it matters
- Reframes orchestration around accepted work outcomes rather than continuous agent supervision.
- Its proof-of-work bundle joins CI, review feedback, complexity evidence, and walkthroughs before landing.
## Caveat
OpenAI labels Symphony a low-key preview for trusted environments, and the captured README leaves most implementation detail to the specification and Elixir guide.
## Sources
[Repository](https://github.com/openai/symphony) · [README](https://github.com/openai/symphony/blob/8001b52e3062495a16e520e4ceaf8f9de868c4d0/README.md) · [License](https://github.com/openai/symphony/blob/8001b52e3062495a16e520e4ceaf8f9de868c4d0/LICENSE)
