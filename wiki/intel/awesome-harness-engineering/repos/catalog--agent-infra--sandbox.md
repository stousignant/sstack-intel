---
# catalog-derived-begin
title: "agent-infra/sandbox"
type: "repo-intel"
status: "active"
active: true
source_identity: "agent-infra/sandbox"
source: "https://github.com/agent-infra/sandbox"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 78
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "89186e8c9fb3f78b2f67cc472a36c1cb63e25ccb"
readme_path: "README.md"
readme_url: "https://github.com/agent-infra/sandbox/blob/89186e8c9fb3f78b2f67cc472a36c1cb63e25ccb/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/agent-infra/sandbox/blob/89186e8c9fb3f78b2f67cc472a36c1cb63e25ccb/LICENSE"
---
# agent-infra/sandbox
## Quick take
AIO Sandbox is a practical reference for consolidating common agent execution surfaces into one container.
## Score
**78/100**
- **Harness relevance — 22/30:** Packages browser, shell, files, editor, notebooks, and MCP behind one sandbox API.
- **Practical pattern value — 22/25:** The unified-container and pinned-image guidance are reusable environment patterns.
- **Evidence and maturity — 16/20:** Active documentation includes SDKs, examples, evaluation material, API references, and version-pinning guidance.
- **Novelty — 11/15:** The browser, shell, files, IDE, notebook, and MCP bundle is a useful but incremental sandbox combination.
- **Risk-adjusted accessibility — 7/10:** Apache-2.0 SDKs and images help, but Docker, broad services, and relaxed seccomp increase evaluation cost.
## Why it matters
- Packages browser, shell, files, editor, notebooks, and MCP behind one sandbox API.
- The unified-container and pinned-image guidance are reusable environment patterns.
## Caveat
The quick start requests seccomp=unconfined and the all-in-one image is operationally heavier than a narrow sandbox.
## Sources
[Repository](https://github.com/agent-infra/sandbox) · [README](https://github.com/agent-infra/sandbox/blob/89186e8c9fb3f78b2f67cc472a36c1cb63e25ccb/README.md) · [License](https://github.com/agent-infra/sandbox/blob/89186e8c9fb3f78b2f67cc472a36c1cb63e25ccb/LICENSE)
