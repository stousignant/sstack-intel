---
# catalog-derived-begin
title: "alibaba/open-code-review"
type: "repo-intel"
status: "active"
active: true
source_identity: "alibaba/open-code-review"
source: "https://github.com/alibaba/open-code-review"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "1471cfa4862b1d8dabc484b659cb927527ec79fc"
readme_path: "README.md"
readme_url: "https://github.com/alibaba/open-code-review/blob/1471cfa4862b1d8dabc484b659cb927527ec79fc/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/alibaba/open-code-review/blob/1471cfa4862b1d8dabc484b659cb927527ec79fc/LICENSE"
---
# alibaba/open-code-review
## Quick take
Open Code Review is a focused review harness with a useful deterministic-pipeline-plus-agent architecture.
## Score
**89/100**
- **Harness relevance — 27/30:** Combines deterministic diff/rule selection with an agent that gathers repository context.
- **Practical pattern value — 23/25:** Its line-level output, resumable review modes, and benchmark design are transferable review-harness patterns.
- **Evidence and maturity — 18/20:** Active Apache-licensed project documents packages, plugins, a multi-repository benchmark, and prior internal use.
- **Novelty — 12/15:** The hybrid of deterministic rules and contextual agent review is more distinctive than a generic review prompt.
- **Risk-adjusted accessibility — 9/10:** Apache-2.0 licensing, an npm package, release binaries, and portable plugins lower evaluation friction.
## Why it matters
- Combines deterministic diff/rule selection with an agent that gathers repository context.
- Its line-level output, resumable review modes, and benchmark design are transferable review-harness patterns.
## Caveat
Scale and benchmark results are README claims; this catalog pass did not reproduce them.
## Sources
[Repository](https://github.com/alibaba/open-code-review) · [README](https://github.com/alibaba/open-code-review/blob/1471cfa4862b1d8dabc484b659cb927527ec79fc/README.md) · [License](https://github.com/alibaba/open-code-review/blob/1471cfa4862b1d8dabc484b659cb927527ec79fc/LICENSE)
