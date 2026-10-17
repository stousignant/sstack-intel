---
# catalog-derived-begin
title: "facebook/mcpguard-dynamic"
type: "repo-intel"
status: "active"
active: true
source_identity: "facebook/mcpguard-dynamic"
source: "https://github.com/facebook/mcpguard-dynamic"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 77
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "f36a2f593cb7fbc4cbf3a8a6770ed28426371b68"
readme_path: "README.md"
readme_url: "https://github.com/facebook/mcpguard-dynamic/blob/f36a2f593cb7fbc4cbf3a8a6770ed28426371b68/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/facebook/mcpguard-dynamic/blob/f36a2f593cb7fbc4cbf3a8a6770ed28426371b68/LICENSE"
---
# facebook/mcpguard-dynamic
## Quick take
A layered MCP sandbox that translates tool capabilities into proxy checks and kernel-enforced eBPF restrictions.
## Score
**77/100**
- **Harness relevance — 24/30:** Enforces capability policy around untrusted MCP server tool calls at proxy and kernel layers.
- **Practical pattern value — 21/25:** Schema-derived policy, argument validation, response sanitization, and fail-closed OS controls are reusable.
- **Evidence and maturity — 14/20:** The Meta repository includes an 82-case benchmark, reproduction commands, edge tests, and MIT licensing.
- **Novelty — 15/15:** Carrying per-tool capabilities into eBPF file, network, process, and fork enforcement is unusually differentiated.
- **Risk-adjusted accessibility — 3/10:** Evaluation needs a Linux 6.x kernel with BPF LSM, clang 21, bpftool, and elevated setup.
## Why it matters
- Treats the MCP server as untrusted and enforces file, network, process, and environment boundaries below its implementation.
- Ships switchable defense configurations and a reproducible benchmark for comparing application and kernel controls.
## Caveat
The kernel, agent runner, and host remain trusted, setup is specialized, and the benchmark and security claims were not reproduced.
## Sources
[Repository](https://github.com/facebook/mcpguard-dynamic) · [README](https://github.com/facebook/mcpguard-dynamic/blob/f36a2f593cb7fbc4cbf3a8a6770ed28426371b68/README.md) · [License](https://github.com/facebook/mcpguard-dynamic/blob/f36a2f593cb7fbc4cbf3a8a6770ed28426371b68/LICENSE)
