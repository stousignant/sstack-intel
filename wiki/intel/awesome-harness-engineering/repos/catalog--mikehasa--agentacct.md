---
# catalog-derived-begin
title: "mikehasa/agentacct"
type: "repo-intel"
status: "active"
active: true
source_identity: "mikehasa/agentacct"
source: "https://github.com/mikehasa/agentacct"
source_categories: [["Design Primitives","Observability & Tracing"]]
source_occurrences: [["Design Primitives","Observability & Tracing"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "87534eeed28234888b303088d1f17fd5f926fdbf"
readme_path: "README.md"
readme_url: "https://github.com/mikehasa/agentacct/blob/87534eeed28234888b303088d1f17fd5f926fdbf/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/mikehasa/agentacct/blob/87534eeed28234888b303088d1f17fd5f926fdbf/LICENSE"
---
# mikehasa/agentacct
## Quick take
A local-first task receipt that separates agent claims, observed work, machine checks, attribution confidence, token use, and estimated cost.
## Score
**81/100**
- **Harness relevance — 25/30:** Task receipts, tool and file activity, costs, machine checks, and verification tiers directly support harness observability.
- **Practical pattern value — 23/25:** Separating reported completion from evidence, grading check independence, and labeling attribution confidence are reusable.
- **Evidence and maturity — 12/20:** The active MIT project has detailed setup and provenance semantics, but explicitly identifies itself as early alpha.
- **Novelty — 13/15:** Work receipts join local client usage with independently graded execution evidence without hosted telemetry.
- **Risk-adjusted accessibility — 8/10:** Local-only operation, demo mode, explicit estimates, and MIT licensing help, while setup reads several client stores.
## Why it matters
- Encodes the difference between reported completion and independently verified evidence.
- Its provenance and confidence labels avoid presenting joined local session data as exact when it is not.
## Caveat
The project is early alpha, cost figures may be estimates, and capability depth differs across supported clients.
## Sources
[Repository](https://github.com/mikehasa/agentacct) · [README](https://github.com/mikehasa/agentacct/blob/87534eeed28234888b303088d1f17fd5f926fdbf/README.md) · [License](https://github.com/mikehasa/agentacct/blob/87534eeed28234888b303088d1f17fd5f926fdbf/LICENSE)
