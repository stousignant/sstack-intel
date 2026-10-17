---
# catalog-derived-begin
title: "HKUDS/CLI-Anything"
type: "repo-intel"
status: "active"
active: true
source_identity: "HKUDS/CLI-Anything"
source: "https://github.com/HKUDS/CLI-Anything"
source_categories: [["Design Primitives","Tool Design"]]
source_occurrences: [["Design Primitives","Tool Design"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 97
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "810c18b0d1ab9b234bc996c9fd999318523a3ef0"
readme_path: "README.md"
readme_url: "https://github.com/HKUDS/CLI-Anything/blob/810c18b0d1ab9b234bc996c9fd999318523a3ef0/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/HKUDS/CLI-Anything/blob/810c18b0d1ab9b234bc996c9fd999318523a3ef0/LICENSE"
---
# HKUDS/CLI-Anything
## Quick take
CLI-Anything combines a harness generator and package hub for exposing existing software through agent-friendly command lines.
## Score
**97/100**
- **Harness relevance — 30/30:** Generates and distributes CLI harnesses that make existing software operable by agents.
- **Practical pattern value — 25/25:** The phased generator, self-describing commands, JSON output, skills, and registry are directly transferable.
- **Evidence and maturity — 20/20:** The active Apache-2.0 project documents many merged harnesses, tests, a package registry, and ongoing hardening.
- **Novelty — 15/15:** A generator plus hub for converting arbitrary applications into agent-native deterministic interfaces is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** The hub and skills are accessible, but generated wrappers still depend on each upstream application and its security model.
## Why it matters
- Its phased workflow standardizes discovery, implementation, testing, documentation, and skill packaging.
- Structured output and self-describing commands reduce parsing and discovery burden for agents.
## Caveat
The captured README was truncated at 50,000 characters, and each generated CLI still inherits the dependencies, permissions, and risks of its wrapped application.
## Sources
[Repository](https://github.com/HKUDS/CLI-Anything) · [README](https://github.com/HKUDS/CLI-Anything/blob/810c18b0d1ab9b234bc996c9fd999318523a3ef0/README.md) · [License](https://github.com/HKUDS/CLI-Anything/blob/810c18b0d1ab9b234bc996c9fd999318523a3ef0/LICENSE)
