---
# catalog-derived-begin
title: "earendil-works/pi"
type: "repo-intel"
status: "active"
active: true
source_identity: "earendil-works/pi"
source: "https://github.com/earendil-works/pi"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 92
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "4a6ed01945c7f6a2a350996fb439148149ab65ee"
readme_path: "README.md"
readme_url: "https://github.com/earendil-works/pi/blob/4a6ed01945c7f6a2a350996fb439148149ab65ee/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/earendil-works/pi/blob/4a6ed01945c7f6a2a350996fb439148149ab65ee/LICENSE"
---
# earendil-works/pi
## Quick take
A compact, self-extensible coding-agent harness with clean package boundaries for models, loops, telemetry, TUI, and CLI behavior.
## Score
**92/100**
- **Harness relevance — 30/30:** A core agent harness spanning model APIs, tool-calling loop, state, coding CLI, TUI, telemetry, and extension surfaces.
- **Practical pattern value — 24/25:** Its composable packages, self-extension model, conformance tests, release builds, and explicit sandbox boundary are directly transferable.
- **Evidence and maturity — 18/20:** Active MIT project documents tests, offline builds, releases, smoke tests, and substantial supply-chain hardening.
- **Novelty — 12/15:** A deliberately small extensible coding agent paired with modular runtime and telemetry packages is a distinctive combination.
- **Risk-adjusted accessibility — 8/10:** Installation is approachable and permissive, but Pi inherits launcher permissions unless separately containerized or sandboxed.
## Why it matters
- Its explicit separation between core loop, provider API, UI, and composition runtime is a useful modularity reference.
- The documented release and dependency controls provide unusually concrete supply-chain patterns for agent CLIs.
## Caveat
Pi has no built-in permission system and runs with the launching user's access unless an external container or sandbox is configured.
## Sources
[Repository](https://github.com/earendil-works/pi) · [README](https://github.com/earendil-works/pi/blob/4a6ed01945c7f6a2a350996fb439148149ab65ee/README.md) · [License](https://github.com/earendil-works/pi/blob/4a6ed01945c7f6a2a350996fb439148149ab65ee/LICENSE)
