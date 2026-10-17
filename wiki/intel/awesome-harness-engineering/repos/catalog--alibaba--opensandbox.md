---
# catalog-derived-begin
title: "alibaba/OpenSandbox"
type: "repo-intel"
status: "active"
active: true
source_identity: "alibaba/OpenSandbox"
source: "https://github.com/alibaba/OpenSandbox"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 80
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "b056b1878105fde409aff9bf1fbbf50a3ce30afa"
readme_path: "README.md"
readme_url: "https://github.com/opensandbox-group/OpenSandbox/blob/b056b1878105fde409aff9bf1fbbf50a3ce30afa/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/opensandbox-group/OpenSandbox/blob/b056b1878105fde409aff9bf1fbbf50a3ce30afa/LICENSE"
---
# alibaba/OpenSandbox
## Quick take
OpenSandbox is a broad agent-sandbox platform with unified lifecycle APIs, execution environments, and security controls.
## Score
**80/100**
- **Harness relevance — 20/30:** Sandbox lifecycle, execution, files, networking, and credentials form a substantial agent-harness component.
- **Practical pattern value — 24/25:** Unified APIs, pluggable runtimes, egress controls, and credential injection are directly transferable patterns.
- **Evidence and maturity — 17/20:** Detailed documentation, active development, signed release images, and Apache-2.0 licensing provide solid evidence.
- **Novelty — 13/15:** The protocol, SDK, MCP, runtime, network, and vault layers form a notably complete sandbox package.
- **Risk-adjusted accessibility — 6/10:** Local Docker support helps, but stronger isolation and distributed operation require substantial infrastructure.
## Why it matters
- Separates a stable sandbox protocol from Docker, Kubernetes, and stronger isolation runtimes.
- Combines network policy and protected credential injection with command, file, and code execution.
## Caveat
The exact source identity redirects to opensandbox-group/OpenSandbox, and README claims were not validated by deploying its infrastructure.
## Sources
[Repository](https://github.com/alibaba/OpenSandbox) · [README](https://github.com/opensandbox-group/OpenSandbox/blob/b056b1878105fde409aff9bf1fbbf50a3ce30afa/README.md) · [License](https://github.com/opensandbox-group/OpenSandbox/blob/b056b1878105fde409aff9bf1fbbf50a3ce30afa/LICENSE)
