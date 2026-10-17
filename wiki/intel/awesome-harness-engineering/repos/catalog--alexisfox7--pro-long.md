---
# catalog-derived-begin
title: "alexisfox7/PRO-LONG"
type: "repo-intel"
status: "active"
active: true
source_identity: "alexisfox7/PRO-LONG"
source: "https://github.com/alexisfox7/PRO-LONG"
source_categories: [["Design Primitives","Context Delivery & Compaction"]]
source_occurrences: [["Design Primitives","Context Delivery & Compaction"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 82
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "9d2f2d46fea8759ed494ce5b0166c7004a2e97c4"
readme_path: "README.md"
readme_url: "https://github.com/alexisfox7/PRO-LONG/blob/9d2f2d46fea8759ed494ce5b0166c7004a2e97c4/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/alexisfox7/PRO-LONG/blob/9d2f2d46fea8759ed494ce5b0166c7004a2e97c4/LICENSE"
---
# alexisfox7/PRO-LONG
## Quick take
A compact local-memory pattern that logs coding sessions durably and lets agents search only the history they need.
## Score
**82/100**
- **Harness relevance — 27/30:** Provides durable context delivery across compaction and sessions for several coding-agent clients.
- **Practical pattern value — 22/25:** A project-local append-only log plus agent-initiated search is a simple transferable memory pattern.
- **Evidence and maturity — 12/20:** The young MIT project has documented client adapters, commands, privacy guidance, and a research citation.
- **Novelty — 13/15:** Keeping full history off-prompt while exposing programmatic retrieval is a distinctive compact design.
- **Risk-adjusted accessibility — 8/10:** Local installation is straightforward, but retained transcripts can contain prompts, tool results, and secrets.
## Why it matters
- Separates durable history from the active prompt instead of repeatedly injecting an entire transcript.
- Project-local adapters cover Codex, Claude Code, OpenCode, and pi lifecycle events.
## Caveat
The log may retain sensitive prompts, tool inputs, results, or secrets, and this README-level review did not validate retrieval quality.
## Sources
[Repository](https://github.com/alexisfox7/PRO-LONG) · [README](https://github.com/alexisfox7/PRO-LONG/blob/9d2f2d46fea8759ed494ce5b0166c7004a2e97c4/README.md) · [License](https://github.com/alexisfox7/PRO-LONG/blob/9d2f2d46fea8759ed494ce5b0166c7004a2e97c4/LICENSE)
