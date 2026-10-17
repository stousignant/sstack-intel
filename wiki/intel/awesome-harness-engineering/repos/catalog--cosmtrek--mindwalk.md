---
# catalog-derived-begin
title: "cosmtrek/mindwalk"
type: "repo-intel"
status: "active"
active: true
source_identity: "cosmtrek/mindwalk"
source: "https://github.com/cosmtrek/mindwalk"
source_categories: [["Design Primitives","Debugging & Developer Experience"]]
source_occurrences: [["Design Primitives","Debugging & Developer Experience"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 63
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "77cd79596a1b7f9f62256ea06485e15182a09566"
readme_path: "README.md"
readme_url: "https://github.com/cosmtrek/mindwalk/blob/77cd79596a1b7f9f62256ea06485e15182a09566/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/cosmtrek/mindwalk/blob/77cd79596a1b7f9f62256ea06485e15182a09566/LICENSE"
---
# cosmtrek/mindwalk
## Quick take
A local visualization and replay tool that maps coding-agent activity onto a 3D view of the codebase.
## Score
**63/100**
- **Harness relevance — 10/30:** Mindwalk is adjacent harness observability rather than an agent runtime or execution component.
- **Practical pattern value — 17/25:** Its normalized trace export, session replay, and optional rubric-based analysis are reusable review patterns.
- **Evidence and maturity — 14/20:** The README documents releases, checksummed installation, three supported session stores, and concrete commands.
- **Novelty — 15/15:** Replaying an agent session as activity over a 3D codebase map is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and a single Go binary ease trials, though optional analysis sends a session summary through a configured model CLI.
## Why it matters
- Makes search, read, and edit coverage visible rather than relying only on transcript chronology.
- Normalizes Claude Code, Codex, and pi sessions and can export traces for downstream analysis.
## Caveat
Visualization is interpretive rather than proof of task correctness, and optional model evaluation transmits summarized session content.
## Sources
[Repository](https://github.com/cosmtrek/mindwalk) · [README](https://github.com/cosmtrek/mindwalk/blob/77cd79596a1b7f9f62256ea06485e15182a09566/README.md) · [License](https://github.com/cosmtrek/mindwalk/blob/77cd79596a1b7f9f62256ea06485e15182a09566/LICENSE)
