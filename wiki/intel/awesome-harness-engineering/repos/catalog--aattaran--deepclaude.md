---
# catalog-derived-begin
title: "aattaran/deepclaude"
type: "repo-intel"
status: "active"
active: true
source_identity: "aattaran/deepclaude"
source: "https://github.com/aattaran/deepclaude"
source_categories: [["Design Primitives","Agent Loop"]]
source_occurrences: [["Design Primitives","Agent Loop"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 68
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "70518b6cdcf3cc488e62e817b86da4b550dd7dfa"
readme_path: "README.md"
readme_url: "https://github.com/aattaran/deepclaude/blob/70518b6cdcf3cc488e62e817b86da4b550dd7dfa/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/aattaran/deepclaude/blob/70518b6cdcf3cc488e62e817b86da4b550dd7dfa/LICENSE"
---
# aattaran/deepclaude
## Quick take
A lightweight wrapper redirects Claude Code’s agent loop to alternative Anthropic-compatible model backends.
## Score
**68/100**
- **Harness relevance — 20/30:** Wraps Claude Code’s existing autonomous tool loop with alternate Anthropic-compatible model backends.
- **Practical pattern value — 17/25:** Backend-selection scripts and session-scoped environment handling provide a reusable routing pattern.
- **Evidence and maturity — 14/20:** The README documents installation, backend flags, costs, and limitations, and the repository is active and MIT-licensed.
- **Novelty — 10/15:** Preserving a mature coding harness while swapping its model backend is a distinctive but focused combination.
- **Risk-adjusted accessibility — 7/10:** The shell/PowerShell wrapper is simple to try, but it needs provider keys and lacks vision and MCP support.
## Why it matters
- Shows a minimal environment-variable boundary for swapping models without rebuilding the tool loop.
- Documents backend selection, cost inspection, and session-local configuration.
## Caveat
The README reports no image input or MCP tools through the compatibility layer, so this is narrower than full Claude Code parity.
## Sources
[Repository](https://github.com/aattaran/deepclaude) · [README](https://github.com/aattaran/deepclaude/blob/70518b6cdcf3cc488e62e817b86da4b550dd7dfa/README.md) · [License](https://github.com/aattaran/deepclaude/blob/70518b6cdcf3cc488e62e817b86da4b550dd7dfa/LICENSE)
