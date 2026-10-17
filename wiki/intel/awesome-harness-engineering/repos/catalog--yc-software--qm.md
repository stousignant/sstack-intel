---
# catalog-derived-begin
title: "yc-software/qm"
type: "repo-intel"
status: "active"
active: true
source_identity: "yc-software/qm"
source: "https://github.com/yc-software/qm"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 88
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "1a6b0e443016079b7e79ac874a8cfda0a5f3b306"
readme_path: "README.md"
readme_url: "https://github.com/yc-software/qm/blob/1a6b0e443016079b7e79ac874a8cfda0a5f3b306/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/yc-software/qm/blob/1a6b0e443016079b7e79ac874a8cfda0a5f3b306/LICENSE"
---
# yc-software/qm
## Quick take
A multiplayer work harness that gives people and rooms isolated scopes while sharing organizational policy, skills, persistence, and agent infrastructure.
## Score
**88/100**
- **Harness relevance — 29/30:** A multiplayer organizational agent harness spanning identity, scopes, policy, persistence, scheduling, sandboxes, Slack, and web.
- **Practical pattern value — 24/25:** Per-person and per-room scopes, harness adapters, durable sandboxes, skill grants, policy inheritance, background work, and deployment separation transfer directly.
- **Evidence and maturity — 15/20:** Active MIT project with detailed architecture, security, deployment, and end-to-end development guidance, but it is young.
- **Novelty — 14/15:** Multi-user scoped memory, credentials, skills, and computers over interchangeable harnesses is an unusually differentiated design.
- **Risk-adjusted accessibility — 6/10:** The deployment skill helps setup, while real use requires organizational cloud infrastructure, Postgres, identity, connectors, secrets, and careful security choices.
## Why it matters
- Its scope-owned memory, files, credentials, permissions, crons, and sandboxes offer a strong multi-tenant harness model.
- Interchangeable Pi, OpenCode, Codex, and Claude Code backends separate organizational state from one agent vendor.
## Caveat
Production deployment is infrastructure-heavy, in-memory sessions vanish without Postgres, and the Auto and Dangerous postures depend on operator-chosen trust boundaries.
## Sources
[Repository](https://github.com/yc-software/qm) · [README](https://github.com/yc-software/qm/blob/1a6b0e443016079b7e79ac874a8cfda0a5f3b306/README.md) · [License](https://github.com/yc-software/qm/blob/1a6b0e443016079b7e79ac874a8cfda0a5f3b306/LICENSE)
