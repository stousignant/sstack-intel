---
# catalog-derived-begin
title: "kevinrgu/autoagent"
type: "repo-intel"
status: "active"
active: true
source_identity: "kevinrgu/autoagent"
source: "https://github.com/kevinrgu/autoagent"
source_categories: [["Reference Implementations","Generators & Meta-Harnesses"]]
source_occurrences: [["Reference Implementations","Generators & Meta-Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 80
score_confidence: low
availability: available
last_reviewed: 2026-09-08
observed_revision: "eb3f185dc9faac276955b4fe5feb93c8f836b644"
readme_path: "README.md"
readme_url: "https://github.com/thirdlayerinc/autoagent/blob/eb3f185dc9faac276955b4fe5feb93c8f836b644/README.md"
metadata_observed: 2026-09-08
license_url: null
---
# kevinrgu/autoagent
## Quick take
An experimental meta-harness that autonomously edits a harness, benchmarks it, and retains only score improvements.
## Score
**80/100**
- **Harness relevance — 30/30:** The meta-agent directly edits, benchmarks, and selects changes to an agent harness.
- **Practical pattern value — 23/25:** A fixed adapter plus editable single-file harness and score-driven keep-or-discard loop is highly reusable.
- **Evidence and maturity — 9/20:** The repository is documented but young, ships without benchmark tasks, and has no captured license file.
- **Novelty — 15/15:** Autonomous overnight hill-climbing over prompts, tools, configuration, and orchestration is unusually differentiated.
- **Risk-adjusted accessibility — 3/10:** Docker, provider credentials, custom tasks, cleanup, and absent license provenance make evaluation heavy.
## Why it matters
- Separates the fixed Harbor adapter boundary from the harness surface the meta-agent may change.
- Turns harness engineering into a repeatable numeric hill-climbing loop.
## Caveat
The assigned identity redirects to thirdlayerinc/autoagent; the repo ships without tasks, and no license file was captured despite the README stating MIT.
## Sources
[Repository](https://github.com/kevinrgu/autoagent) · [README](https://github.com/thirdlayerinc/autoagent/blob/eb3f185dc9faac276955b4fe5feb93c8f836b644/README.md)
