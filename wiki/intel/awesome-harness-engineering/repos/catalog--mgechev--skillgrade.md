---
# catalog-derived-begin
title: "mgechev/skillgrade"
type: "repo-intel"
status: "active"
active: true
source_identity: "mgechev/skillgrade"
source: "https://github.com/mgechev/skillgrade"
source_categories: [["Design Primitives","Skills & MCP"]]
source_occurrences: [["Design Primitives","Skills & MCP"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 86
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "8d9e5b8a275fd5f951b1239211a87d9a7133b23b"
readme_path: "README.md"
readme_url: "https://github.com/mgechev/skillgrade/blob/8d9e5b8a275fd5f951b1239211a87d9a7133b23b/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/mgechev/skillgrade/blob/8d9e5b8a275fd5f951b1239211a87d9a7133b23b/LICENSE"
---
# mgechev/skillgrade
## Quick take
A focused evaluation harness that turns agent-skill discovery and use into repeatable, CI-gated trials with deterministic and rubric graders.
## Score
**86/100**
- **Harness relevance — 26/30:** Directly evaluates whether coding agents discover and use skills correctly across supported harnesses.
- **Practical pattern value — 24/25:** Task fixtures, repeated trials, deterministic and rubric graders, container isolation, reference outputs, filtering, and CI thresholds transfer directly.
- **Evidence and maturity — 16/20:** Active MIT CLI with documented configuration, examples, multiple agents, and smoke/reliable/regression presets.
- **Novelty — 13/15:** Treating agent skills as unit-testable behavior with hidden expected values and mixed graders is notably differentiated.
- **Risk-adjusted accessibility — 7/10:** The CLI is accessible, but Docker, agent CLIs, model credentials, and nondeterministic trial cost add setup and operating weight.
## Why it matters
- Its answer-key isolation and structured grader input are strong patterns for preventing evaluation leakage.
- Trial presets and thresholded CI make stochastic agent behavior explicit rather than hiding it behind one successful run.
## Caveat
Reliable conclusions still depend on representative tasks, sound graders, enough trials, and paid model execution; the tool cannot supply those choices automatically.
## Sources
[Repository](https://github.com/mgechev/skillgrade) · [README](https://github.com/mgechev/skillgrade/blob/8d9e5b8a275fd5f951b1239211a87d9a7133b23b/README.md) · [License](https://github.com/mgechev/skillgrade/blob/8d9e5b8a275fd5f951b1239211a87d9a7133b23b/LICENSE)
