---
# catalog-derived-begin
title: "facebookresearch/cca-swebench"
type: "repo-intel"
status: "active"
active: true
source_identity: "facebookresearch/cca-swebench"
source: "https://github.com/facebookresearch/cca-swebench"
source_categories: [["Design Primitives","Agent Loop"]]
source_occurrences: [["Design Primitives","Agent Loop"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 80
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "bdeb74b3d828bfbb2c61030c6201fa9da44e69d0"
readme_path: "README.md"
readme_url: "https://github.com/facebookresearch/cca-swebench/blob/bdeb74b3d828bfbb2c61030c6201fa9da44e69d0/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/facebookresearch/cca-swebench/blob/bdeb74b3d828bfbb2c61030c6201fa9da44e69d0/LICENSE"
---
# facebookresearch/cca-swebench
## Quick take
CCA-SWEBench is a compact, concrete reference for putting a coding agent inside its benchmark container.
## Score
**80/100**
- **Harness relevance — 28/30:** Implements a minimal coding-agent harness around direct actions inside the task container.
- **Practical pattern value — 20/25:** The in-container placement and explicit runtime trade-off are reusable benchmark-harness patterns.
- **Evidence and maturity — 14/20:** An active Meta research repository documents setup and a SWE-bench Pro result, but notes limited testing across agents.
- **Novelty — 12/15:** Putting the agent inside the container is a distinctive simplification of common external-runtime designs.
- **Risk-adjusted accessibility — 6/10:** MIT licensing helps, but container packaging, Conda, benchmark data, and provider credentials raise trial cost.
## Why it matters
- Its direct in-container action model exposes a simple harness boundary with little abstraction.
- The Docker and runtime comparison documents practical isolation trade-offs.
## Caveat
The README says support beyond SWE-Agent is not well tested, and setup depends on benchmark containers and model credentials.
## Sources
[Repository](https://github.com/facebookresearch/cca-swebench) · [README](https://github.com/facebookresearch/cca-swebench/blob/bdeb74b3d828bfbb2c61030c6201fa9da44e69d0/README.md) · [License](https://github.com/facebookresearch/cca-swebench/blob/bdeb74b3d828bfbb2c61030c6201fa9da44e69d0/LICENSE)
