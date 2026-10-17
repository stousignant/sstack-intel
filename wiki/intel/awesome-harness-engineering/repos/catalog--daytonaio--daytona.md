---
# catalog-derived-begin
title: "daytonaio/daytona"
type: "repo-intel"
status: "active"
active: true
source_identity: "daytonaio/daytona"
source: "https://github.com/daytonaio/daytona"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 72
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "ec4c21b2d597091ac09ecc278f3bcc172575a987"
readme_path: "README.md"
readme_url: "https://github.com/daytonaio/daytona/blob/ec4c21b2d597091ac09ecc278f3bcc172575a987/README.md"
metadata_observed: 2026-09-08
license_url: null
---
# daytonaio/daytona
## Quick take
A detailed reference architecture for stateful agent sandboxes, snapshots, lifecycle APIs, and separated control and compute planes.
## Score
**72/100**
- **Harness relevance — 25/30:** Provides isolated stateful computers and lifecycle APIs for agent-generated code execution.
- **Practical pattern value — 22/25:** Control/compute plane separation, snapshots, SDKs, process/filesystem operations, and network controls are reusable sandbox patterns.
- **Evidence and maturity — 10/20:** The public repository is extensively documented but explicitly unmaintained after development moved private.
- **Novelty — 11/15:** Sub-90ms stateful sandbox claims plus multi-plane governance form a distinctive execution service design.
- **Risk-adjusted accessibility — 4/10:** SDK quickstarts are simple, but service dependence, absent asserted license metadata, and discontinued public maintenance increase risk.
## Why it matters
- Its SDK and plane boundaries show how a harness can treat secure execution as a programmable service.
- Persistent sandboxes, snapshots, audit controls, and interactive access cover both agent and operator needs.
## Caveat
The README says this public repository is no longer maintained and core development moved private; no current support, fixes, or releases should be expected.
## Sources
[Repository](https://github.com/daytonaio/daytona) · [README](https://github.com/daytonaio/daytona/blob/ec4c21b2d597091ac09ecc278f3bcc172575a987/README.md)
