---
# catalog-derived-begin
title: "kerlenton/mcpsnoop"
type: "repo-intel"
status: "active"
active: true
source_identity: "kerlenton/mcpsnoop"
source: "https://github.com/kerlenton/mcpsnoop"
source_categories: [["Design Primitives","Debugging & Developer Experience"]]
source_occurrences: [["Design Primitives","Debugging & Developer Experience"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: low
availability: available
last_reviewed: 2026-09-08
observed_revision: "b9e90e7732eed233f20b99738d17ea8c053830a3"
readme_path: "README.md"
readme_url: "https://github.com/kerlenton/mcpsnoop/blob/b9e90e7732eed233f20b99738d17ea8c053830a3/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/kerlenton/mcpsnoop/blob/b9e90e7732eed233f20b99738d17ea8c053830a3/LICENSE"
---
# kerlenton/mcpsnoop
## Quick take
A transparent MCP proxy that captures real tool traffic and turns protocol behavior into inspectable and CI-gated evidence.
## Score
**81/100**
- **Harness relevance — 20/30:** Mcpsnoop is a substantial MCP observability and verification component placed in the real client-server data path.
- **Practical pattern value — 25/25:** Frame capture, redaction, session comparison, protocol assertions, SARIF reporting, and CI gating are directly reusable patterns.
- **Evidence and maturity — 14/20:** The README documents CI, releases, package channels, a GitHub Action, metrics, and integration checks, but the capture is truncated.
- **Novelty — 15/15:** Observing real client traffic and detecting missing calls, negotiation drift, and tool-definition changes is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and npm, Go, or Homebrew installs ease use, though proxying live MCP traffic can expose secrets without redaction.
## Why it matters
- Tests the actual client-server path rather than a synthetic inspector client.
- Combines live TUI inspection with export, redaction, assertions, diffs, metrics, and SARIF.
## Caveat
The supplied README evidence is truncated, and placing a proxy in the data path requires deliberate redaction and handling of sensitive tool payloads.
## Sources
[Repository](https://github.com/kerlenton/mcpsnoop) · [README](https://github.com/kerlenton/mcpsnoop/blob/b9e90e7732eed233f20b99738d17ea8c053830a3/README.md) · [License](https://github.com/kerlenton/mcpsnoop/blob/b9e90e7732eed233f20b99738d17ea8c053830a3/LICENSE)
