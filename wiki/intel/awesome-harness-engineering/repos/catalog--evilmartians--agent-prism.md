---
# catalog-derived-begin
title: "evilmartians/agent-prism"
type: "repo-intel"
status: "active"
active: true
source_identity: "evilmartians/agent-prism"
source: "https://github.com/evilmartians/agent-prism"
source_categories: [["Design Primitives","Debugging & Developer Experience"]]
source_occurrences: [["Design Primitives","Debugging & Developer Experience"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 65
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "53a9078b533b6958e9081d68a05b03b053059e97"
readme_path: "readme.md"
readme_url: "https://github.com/evilmartians/agent-prism/blob/53a9078b533b6958e9081d68a05b03b053059e97/readme.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/evilmartians/agent-prism/blob/53a9078b533b6958e9081d68a05b03b053059e97/LICENSE"
---
# evilmartians/agent-prism
## Quick take
Composable React components that turn OpenTelemetry or Langfuse agent traces into navigable timelines and detail views.
## Score
**65/100**
- **Harness relevance — 20/30:** Trace visualization is a substantial debugging component, but not a complete agent harness or telemetry backend.
- **Practical pattern value — 18/25:** Normalized adapters and composable trace-list, tree, and details views are reusable developer-experience patterns.
- **Evidence and maturity — 11/20:** The institutional project has packages, examples, Storybook, and documentation, but explicitly labels the release alpha.
- **Novelty — 8/15:** Agent-focused hierarchical trace UI is useful but incrementally extends familiar observability interfaces.
- **Risk-adjusted accessibility — 8/10:** MIT licensing and copyable React components help, with React 19 and alpha API churn as constraints.
## Why it matters
- Offers a concrete UI boundary between raw span data and agent debugging workflows.
- Its common adapter interface supports replacing telemetry sources without rebuilding the viewer.
## Caveat
The library is alpha, requires a modern React and Tailwind stack, and does not itself collect, store, or evaluate traces.
## Sources
[Repository](https://github.com/evilmartians/agent-prism) · [README](https://github.com/evilmartians/agent-prism/blob/53a9078b533b6958e9081d68a05b03b053059e97/readme.md) · [License](https://github.com/evilmartians/agent-prism/blob/53a9078b533b6958e9081d68a05b03b053059e97/LICENSE)
