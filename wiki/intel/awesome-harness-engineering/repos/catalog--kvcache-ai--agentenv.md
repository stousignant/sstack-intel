---
# catalog-derived-begin
title: "kvcache-ai/AgentENV"
type: "repo-intel"
status: "active"
active: true
source_identity: "kvcache-ai/AgentENV"
source: "https://github.com/kvcache-ai/AgentENV"
source_categories: [["Production Infrastructure & Operations"]]
source_occurrences: [["Production Infrastructure & Operations"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 79
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "1d742e4e149092be895f2c3cf0a097201229a250"
readme_path: "README.md"
readme_url: "https://github.com/kvcache-ai/AgentENV/blob/1d742e4e149092be895f2c3cf0a097201229a250/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/kvcache-ai/AgentENV/blob/1d742e4e149092be895f2c3cf0a097201229a250/LICENSE"
---
# kvcache-ai/AgentENV
## Quick take
AgentENV is distributed Firecracker infrastructure for large fleets of fast, snapshot-backed agent environments.
## Score
**79/100**
- **Harness relevance — 25/30:** Runs scalable, forkable Firecracker environments for agent training and parallel workflows.
- **Practical pattern value — 20/25:** Distributed image caching, incremental snapshots, pause/resume, fork, overcommit, and E2B compatibility are strong patterns.
- **Evidence and maturity — 17/20:** The MIT project has active development, docs, coverage CI, deployment paths, and reported production use for Kimi K3.
- **Novelty — 14/15:** Combines massive OCI image scale with sub-100ms lifecycle operations and persistent distributed snapshots.
- **Risk-adjusted accessibility — 3/10:** Requires Linux 6.8+, KVM, privileged device access, and trusted networking or external TLS termination.
## Why it matters
- Its bounded local cache plus remote image and snapshot storage addresses environment diversity at cluster scale.
- Pause, resume, fork, ballooning, and shared page-cache patterns target the economics of long-lived agent workloads.
## Caveat
Single-node setup still needs modern Linux, KVM, privileged access, and trusted transport because the server authenticates requests but does not encrypt them.
## Sources
[Repository](https://github.com/kvcache-ai/AgentENV) · [README](https://github.com/kvcache-ai/AgentENV/blob/1d742e4e149092be895f2c3cf0a097201229a250/README.md) · [License](https://github.com/kvcache-ai/AgentENV/blob/1d742e4e149092be895f2c3cf0a097201229a250/LICENSE)
