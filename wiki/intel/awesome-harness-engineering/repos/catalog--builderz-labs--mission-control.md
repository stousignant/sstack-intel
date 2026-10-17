---
# catalog-derived-begin
title: "builderz-labs/mission-control"
type: "repo-intel"
status: "active"
active: true
source_identity: "builderz-labs/mission-control"
source: "https://github.com/builderz-labs/mission-control"
source_categories: [["Production Infrastructure & Operations"]]
source_occurrences: [["Production Infrastructure & Operations"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "5483a0e1eef15b467c167e95796791112cedbb7c"
readme_path: "README.md"
readme_url: "https://github.com/builderz-labs/mission-control/blob/5483a0e1eef15b467c167e95796791112cedbb7c/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/builderz-labs/mission-control/blob/5483a0e1eef15b467c167e95796791112cedbb7c/LICENSE"
---
# builderz-labs/mission-control
## Quick take
A self-hosted multi-runtime control plane for dispatch, review, governance, activity, schedules, and completion evidence.
## Score
**89/100**
- **Harness relevance — 30/30:** Task dispatch, run review, runtime registration, schedules, approvals, receipts, and spend tracking are core harness operations.
- **Practical pattern value — 24/25:** Its control-plane separation, completion receipts, review gates, runtime adapters, and event interfaces are directly transferable.
- **Evidence and maturity — 15/20:** The active project documents architecture, tests, deployment, security hardening, and releases, while explicitly remaining alpha.
- **Novelty — 13/15:** It unifies operational, knowledge, governance, and quality-review surfaces above multiple agent runtimes.
- **Risk-adjusted accessibility — 7/10:** MIT licensing, Docker, and local SQLite ease trials, but network exposure and alpha schema churn add risk.
## Why it matters
- Models the operator layer as separate from each agent's reasoning and tool loop.
- Completion receipts and approval-backed task transitions are strong verification patterns.
## Caveat
The project labels itself alpha; adapter depth varies, and network-accessible deployment requires explicit hardening beyond the default local setup.
## Sources
[Repository](https://github.com/builderz-labs/mission-control) · [README](https://github.com/builderz-labs/mission-control/blob/5483a0e1eef15b467c167e95796791112cedbb7c/README.md) · [License](https://github.com/builderz-labs/mission-control/blob/5483a0e1eef15b467c167e95796791112cedbb7c/LICENSE)
