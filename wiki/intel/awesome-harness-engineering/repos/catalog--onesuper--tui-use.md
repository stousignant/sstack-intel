---
# catalog-derived-begin
title: "onesuper/tui-use"
type: "repo-intel"
status: "active"
active: true
source_identity: "onesuper/tui-use"
source: "https://github.com/onesuper/tui-use"
source_categories: [["Design Primitives","Tool Design"]]
source_occurrences: [["Design Primitives","Tool Design"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "0170481831ca57974d3c7da306c654a815e57efa"
readme_path: "README.md"
readme_url: "https://github.com/onesuper/tui-use/blob/0170481831ca57974d3c7da306c654a815e57efa/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/onesuper/tui-use/blob/0170481831ca57974d3c7da306c654a815e57efa/LICENSE"
---
# onesuper/tui-use
## Quick take
A PTY control tool that lets agents drive REPLs, debuggers, and TUIs through snapshots and signal-based waits.
## Score
**81/100**
- **Harness relevance — 20/30:** Tui-use is a substantial interactive-process tool component for coding-agent harnesses.
- **Practical pattern value — 25/25:** PTY sessions, deterministic snapshots, stable-screen waits, semantic text waits, and highlighted selection spans are directly transferable.
- **Evidence and maturity — 14/20:** The README documents npm distribution, Codex and Claude plugins, integration tests, commands, and troubleshooting, though the project is recent.
- **Novelty — 15/15:** Replacing sleep-and-poll terminal control with render-aware waits and machine-readable TUI highlights is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and npm installation ease trials, while controlling arbitrary interactive processes remains a high-impact capability.
## Why it matters
- Avoids brittle sleep timing by waiting for screen stability or expected text.
- Exposes inverse-video highlights so agents can identify selected terminal UI elements.
## Caveat
It can control arbitrary interactive programs with the operator’s privileges, and the harness plugin still requires the separate CLI installation.
## Sources
[Repository](https://github.com/onesuper/tui-use) · [README](https://github.com/onesuper/tui-use/blob/0170481831ca57974d3c7da306c654a815e57efa/README.md) · [License](https://github.com/onesuper/tui-use/blob/0170481831ca57974d3c7da306c654a815e57efa/LICENSE)
