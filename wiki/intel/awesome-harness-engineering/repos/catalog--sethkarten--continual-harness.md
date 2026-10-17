---
# catalog-derived-begin
title: "sethkarten/continual-harness"
type: "repo-intel"
status: "active"
active: true
source_identity: "sethkarten/continual-harness"
source: "https://github.com/sethkarten/continual-harness"
source_categories: [["Reference Implementations","Generators & Meta-Harnesses"]]
source_occurrences: [["Reference Implementations","Generators & Meta-Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "bbab97ad73e460b7cd7c08527d10ced30cc03fbe"
readme_path: "README.md"
readme_url: "https://github.com/sethkarten/continual-harness/blob/bbab97ad73e460b7cd7c08527d10ced30cc03fbe/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/sethkarten/continual-harness/blob/bbab97ad73e460b7cd7c08527d10ced30cc03fbe/LICENSE"
---
# sethkarten/continual-harness
## Quick take
A research harness that continuously rewrites its own prompt, subagents, skills, and memory from recent trajectory failures without resetting the episode.
## Score
**89/100**
- **Harness relevance — 30/30:** The project implements in-episode evolution of prompts, subagents, skills, and memory in a complete benchmark harness.
- **Practical pattern value — 22/25:** Trajectory-window refinement, component CRUD, bootstrap modes, and restricted external-agent MCP surfaces are reusable.
- **Evidence and maturity — 17/20:** A paper, reference implementation, benchmarks, and active public metadata provide strong research evidence.
- **Novelty — 15/15:** Reset-free full-harness refinement during one continuous episode is unusually differentiated.
- **Risk-adjusted accessibility — 5/10:** MIT licensing helps, but ROMs, emulators, models, and game-specific infrastructure make evaluation heavy.
## Why it matters
- Provides a concrete four-component CRUD model for online harness adaptation.
- Documents capability-dependent results and bootstrap variants instead of implying universal gains.
## Caveat
The reference domain requires Pokémon ROM and emulator infrastructure, and the paper reports that gains depend strongly on model capability.
## Sources
[Repository](https://github.com/sethkarten/continual-harness) · [README](https://github.com/sethkarten/continual-harness/blob/bbab97ad73e460b7cd7c08527d10ced30cc03fbe/README.md) · [License](https://github.com/sethkarten/continual-harness/blob/bbab97ad73e460b7cd7c08527d10ced30cc03fbe/LICENSE)
