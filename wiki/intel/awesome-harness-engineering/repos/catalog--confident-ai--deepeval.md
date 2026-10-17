---
# catalog-derived-begin
title: "confident-ai/deepeval"
type: "repo-intel"
status: "active"
active: true
source_identity: "confident-ai/deepeval"
source: "https://github.com/confident-ai/deepeval"
source_categories: [["Evals & Verification"]]
source_occurrences: [["Evals & Verification"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 92
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "f94d940c1e5afc4b280420fe73fe17d146274018"
readme_path: "README.md"
readme_url: "https://github.com/confident-ai/deepeval/blob/f94d940c1e5afc4b280420fe73fe17d146274018/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/confident-ai/deepeval/blob/f94d940c1e5afc4b280420fe73fe17d146274018/LICENSE.md"
---
# confident-ai/deepeval
## Quick take
DeepEval brings pytest-style tests and specialized metrics to agent trajectories, tool calls, RAG, and LLM outputs.
## Score
**92/100**
- **Harness relevance — 30/30:** Provides core evaluation and regression testing for agents, trajectories, tool use, RAG, and LLM applications.
- **Practical pattern value — 25/25:** Pytest-style assertions, component metrics, datasets, and CI integration are directly transferable.
- **Evidence and maturity — 20/20:** The active Apache-2.0 project has a packaged framework, extensive metrics, documentation, and broad integrations.
- **Novelty — 10/15:** Combining end-to-end, trajectory, step, MCP, and custom judge metrics is a distinctive evaluation suite.
- **Risk-adjusted accessibility — 7/10:** The package is easy to install, though many metrics require judge models and cloud reporting is separately offered.
## Why it matters
- Supports both black-box outcomes and component-level checks such as tool correctness and plan adherence.
- Fits repeatable local and CI evaluation workflows across several agent frameworks.
## Caveat
Many evaluations depend on an LLM judge, and the optional hosted reporting path requires an account and sends test records to that platform.
## Sources
[Repository](https://github.com/confident-ai/deepeval) · [README](https://github.com/confident-ai/deepeval/blob/f94d940c1e5afc4b280420fe73fe17d146274018/README.md) · [License](https://github.com/confident-ai/deepeval/blob/f94d940c1e5afc4b280420fe73fe17d146274018/LICENSE.md)
