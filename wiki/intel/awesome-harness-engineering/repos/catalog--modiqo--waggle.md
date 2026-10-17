---
# catalog-derived-begin
title: "modiqo/waggle"
type: "repo-intel"
status: "active"
active: true
source_identity: "modiqo/waggle"
source: "https://github.com/modiqo/waggle"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 84
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "ae8cdfd291fe92e3c20a77b41b4b0f79d59d8c28"
readme_path: "README.md"
readme_url: "https://github.com/modiqo/waggle/blob/ae8cdfd291fe92e3c20a77b41b4b0f79d59d8c28/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/modiqo/waggle/blob/ae8cdfd291fe92e3c20a77b41b4b0f79d59d8c28/LICENSE-APACHE"
---
# modiqo/waggle
## Quick take
An MCP-native artifact handoff layer that adds immutable versions, consumer-specific projections, lineage, revocation, and read receipts to path-sized references.
## Score
**84/100**
- **Harness relevance — 25/30:** Provides a dedicated reference and handoff layer for multi-agent harnesses rather than a full agent runtime.
- **Practical pattern value — 23/25:** Immutable artifact tokens, consumer projections, byte-bounded reads, lineage, revocation, receipts, and MCP transport are directly reusable.
- **Evidence and maturity — 13/20:** Apache-2.0 project has detailed protocol documentation, packages, and benchmark claims, but is very new.
- **Novelty — 15/15:** Combining content-addressed handoffs, per-consumer views, cross-host reach, and read telemetry is unusually differentiated.
- **Risk-adjusted accessibility — 8/10:** A local binary, SQLite store, and MCP interface lower friction, though distributed reach and identity policy add operational complexity.
## Why it matters
- It addresses a real orchestration blind spot: proving what delegated agents actually resolved and read.
- The same token spanning local and remote consumers offers a vendor-neutral alternative to copying context into every prompt.
## Caveat
For local short-lived agents sharing a filesystem, the README itself notes that plain paths may be nearly as effective and substantially simpler; benchmark claims were not reproduced.
## Sources
[Repository](https://github.com/modiqo/waggle) · [README](https://github.com/modiqo/waggle/blob/ae8cdfd291fe92e3c20a77b41b4b0f79d59d8c28/README.md) · [License](https://github.com/modiqo/waggle/blob/ae8cdfd291fe92e3c20a77b41b4b0f79d59d8c28/LICENSE-APACHE)
