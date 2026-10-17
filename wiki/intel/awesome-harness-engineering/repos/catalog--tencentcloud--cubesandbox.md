---
# catalog-derived-begin
title: "TencentCloud/CubeSandbox"
type: "repo-intel"
status: "active"
active: true
source_identity: "TencentCloud/CubeSandbox"
source: "https://github.com/TencentCloud/CubeSandbox"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 82
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "a15e080dc92f7caa4f57a8ff6c3edb9cfd53f2ff"
readme_path: "README.md"
readme_url: "https://github.com/TencentCloud/CubeSandbox/blob/a15e080dc92f7caa4f57a8ff6c3edb9cfd53f2ff/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/TencentCloud/CubeSandbox/blob/a15e080dc92f7caa4f57a8ff6c3edb9cfd53f2ff/LICENSE"
---
# TencentCloud/CubeSandbox
## Quick take
CubeSandbox is agent-oriented microVM infrastructure combining rapid lifecycle operations, snapshots, rollback, network policy, and protected credential injection.
## Score
**82/100**
- **Harness relevance — 25/30:** Provides secure, concurrent, lifecycle-managed microVM sandboxes for agent code execution.
- **Practical pattern value — 21/25:** Pooling, snapshots, rollback, fork, credential injection, egress policy, pause/resume, and E2B compatibility are transferable.
- **Evidence and maturity — 18/20:** The institutional project has active releases, documentation, benchmarks, PyPI packaging, deployment tooling, and an Apache-2.0 license file.
- **Novelty — 14/15:** Combines low-overhead microVMs, event-level cloning, security proxying, and cross-node lifecycle management.
- **Risk-adjusted accessibility — 4/10:** A quickstart exists, but hardware isolation, networking, storage, and cluster deployment remain operationally heavy.
## Why it matters
- Its security proxy keeps credentials outside sandbox code while enforcing domain, path, and method policies.
- Copy-on-write snapshots, pause/resume, rollback, and fork support parallel and recoverable agent execution.
## Caveat
The README reports strong performance and production-deployment features, but operating the isolation, networking, storage, and cluster stack remains complex and was not tested here.
## Sources
[Repository](https://github.com/TencentCloud/CubeSandbox) · [README](https://github.com/TencentCloud/CubeSandbox/blob/a15e080dc92f7caa4f57a8ff6c3edb9cfd53f2ff/README.md) · [License](https://github.com/TencentCloud/CubeSandbox/blob/a15e080dc92f7caa4f57a8ff6c3edb9cfd53f2ff/LICENSE)
