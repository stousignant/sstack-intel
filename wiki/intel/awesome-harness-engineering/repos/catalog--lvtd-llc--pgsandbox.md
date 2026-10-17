---
# catalog-derived-begin
title: "LVTD-LLC/pgsandbox"
type: "repo-intel"
status: "active"
active: true
source_identity: "LVTD-LLC/pgsandbox"
source: "https://github.com/LVTD-LLC/pgsandbox"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "53e1013b0e29619940d0f79d6f36245fa3e3e210"
readme_path: "README.md"
readme_url: "https://github.com/LVTD-LLC/pgsandbox/blob/53e1013b0e29619940d0f79d6f36245fa3e3e210/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/LVTD-LLC/pgsandbox/blob/53e1013b0e29619940d0f79d6f36245fa3e3e210/LICENSE"
---
# LVTD-LLC/pgsandbox
## Quick take
PGSandbox gives coding agents lifecycle-managed disposable PostgreSQL databases for migration, query, seed, and bug-reproduction work.
## Score
**81/100**
- **Harness relevance — 22/30:** Provides an agent-facing MCP sandbox for isolated database experiments and repository validation.
- **Practical pattern value — 23/25:** Scoped roles, TTLs, quotas, bounded results, credential masking, schema diffs, and safe command injection are directly reusable.
- **Evidence and maturity — 16/20:** The active MIT project documents architecture, safety boundaries, packaging, unit tests, and live integration tests.
- **Novelty — 12/15:** Turns disposable real PostgreSQL databases into a typed, lifecycle-managed MCP resource for coding agents.
- **Risk-adjusted accessibility — 8/10:** Released binaries and managed local Postgres avoid Docker, though setup still grants database and command capabilities.
## Why it matters
- It scopes each task to a tracked database and login while bounding output and masking privileged credentials.
- Schema snapshots, diffs, templates, and injected sandbox URLs connect isolation to real repository validation workflows.
## Caveat
The MCP can execute SQL and repository commands against a real local or external Postgres service, so profile selection, quotas, TTLs, and admin credentials remain security-sensitive.
## Sources
[Repository](https://github.com/LVTD-LLC/pgsandbox) · [README](https://github.com/LVTD-LLC/pgsandbox/blob/53e1013b0e29619940d0f79d6f36245fa3e3e210/README.md) · [License](https://github.com/LVTD-LLC/pgsandbox/blob/53e1013b0e29619940d0f79d6f36245fa3e3e210/LICENSE)
