---
# catalog-derived-begin
title: "google/agent-shell-tools"
type: "repo-intel"
status: "active"
active: true
source_identity: "google/agent-shell-tools"
source: "https://github.com/google/agent-shell-tools"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 74
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "c205f555004b253f7ca624d1d2c6629ab26c54ff"
readme_path: "README.md"
readme_url: "https://github.com/google/agent-shell-tools/blob/c205f555004b253f7ca624d1d2c6629ab26c54ff/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/google/agent-shell-tools/blob/c205f555004b253f7ca624d1d2c6629ab26c54ff/LICENSE"
---
# google/agent-shell-tools
## Quick take
A small toolkit for composing sandboxed shell execution, narrowly filtered host commands, streamed execution, and MCP development loops.
## Score
**74/100**
- **Harness relevance — 20/30:** Sandboxed and filtered shell access is a substantial execution and permission component of coding harnesses.
- **Practical pattern value — 23/25:** Container isolation, narrow host delegation, streamed execution, and MCP server multiplexing are directly reusable.
- **Evidence and maturity — 14/20:** Institutional metadata, concise documentation, and a hermetic Bazel test command support active implementation evidence.
- **Novelty — 10/15:** The explicit split between sandbox freedom and filtered ambient-credential commands is a distinctive composition.
- **Risk-adjusted accessibility — 7/10:** Apache-2.0 is permissive, while nsjail and Bazel requirements add platform and setup constraints.
## Why it matters
- Cleanly separates container isolation from explicitly delegated host capabilities.
- Provides a compact reference for edit-test cycles against MCP servers inside a controlled shell boundary.
## Caveat
It is not an officially supported Google product, and its nsjail/Bazel stack may limit portability.
## Sources
[Repository](https://github.com/google/agent-shell-tools) · [README](https://github.com/google/agent-shell-tools/blob/c205f555004b253f7ca624d1d2c6629ab26c54ff/README.md) · [License](https://github.com/google/agent-shell-tools/blob/c205f555004b253f7ca624d1d2c6629ab26c54ff/LICENSE)
