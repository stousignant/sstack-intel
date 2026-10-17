---
# catalog-derived-begin
title: "google-labs-code/design.md"
type: "repo-intel"
status: "active"
active: true
source_identity: "google-labs-code/design.md"
source: "https://github.com/google-labs-code/design.md"
source_categories: [["Design Primitives","Context Delivery & Compaction"]]
source_occurrences: [["Design Primitives","Context Delivery & Compaction"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 71
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "9bf8eae67128b6cc55ad9bf86665767deb4c11cd"
readme_path: "README.md"
readme_url: "https://github.com/google-labs-code/design.md/blob/9bf8eae67128b6cc55ad9bf86665767deb4c11cd/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/google-labs-code/design.md/blob/9bf8eae67128b6cc55ad9bf86665767deb4c11cd/LICENSE"
---
# google-labs-code/design.md
## Quick take
DESIGN.md defines a durable context format that pairs exact design tokens with prose explaining how coding agents should apply them.
## Score
**71/100**
- **Harness relevance — 20/30:** Supplies persistent structured design context and validation for coding agents rather than a full harness.
- **Practical pattern value — 17/25:** Normative tokens plus explanatory prose, linting, diffs, exports, and unknown-key behavior form a reusable context contract.
- **Evidence and maturity — 14/20:** The Apache-2.0 project has a detailed specification and CLI, while the format remains explicitly alpha.
- **Novelty — 10/15:** Combines machine-readable design tokens with agent-facing rationale in one durable file format.
- **Risk-adjusted accessibility — 10/10:** A permissive spec and npx lint command make evaluation simple and low-risk.
## Why it matters
- The split between normative tokens and rationale is a useful pattern for reliable context delivery.
- Lint and diff commands turn design-system drift into structured findings that an agent can consume.
## Caveat
The format is explicitly alpha and covers one narrow context domain, so its conventions may still change and it is not a general agent harness.
## Sources
[Repository](https://github.com/google-labs-code/design.md) · [README](https://github.com/google-labs-code/design.md/blob/9bf8eae67128b6cc55ad9bf86665767deb4c11cd/README.md) · [License](https://github.com/google-labs-code/design.md/blob/9bf8eae67128b6cc55ad9bf86665767deb4c11cd/LICENSE)
