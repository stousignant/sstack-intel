---
# catalog-derived-begin
title: "vaquarkhan/mcp-test-harness"
type: "repo-intel"
status: "active"
active: true
source_identity: "vaquarkhan/mcp-test-harness"
source: "https://github.com/vaquarkhan/mcp-test-harness"
source_categories: [["Design Primitives","Verification & CI Integration"]]
source_occurrences: [["Design Primitives","Verification & CI Integration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 87
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "2b7bb513d3018aa928a386e10a174ae6020763b1"
readme_path: "README.md"
readme_url: "https://github.com/vaquarkhan/mcp-test-harness/blob/2b7bb513d3018aa928a386e10a174ae6020763b1/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/vaquarkhan/mcp-test-harness/blob/2b7bb513d3018aa928a386e10a174ae6020763b1/LICENSE"
---
# vaquarkhan/mcp-test-harness
## Quick take
A deterministic MCP server test framework spanning protocol behavior, regression, performance, chaos, security gates, and CI reporting.
## Score
**87/100**
- **Harness relevance — 22/30:** Provides deterministic CI validation for the MCP servers that expose tools and data to agent harnesses.
- **Practical pattern value — 25/25:** Functional, regression, performance, chaos, conformance, manifest, security, and report gates are directly transferable.
- **Evidence and maturity — 19/20:** The MIT project documents release 5.2.0, PyPI and container distribution, CI dogfooding, and over one thousand self-tests.
- **Novelty — 12/15:** Unifying MCP protocol assertions, performance baselines, chaos, and supply-chain gates is distinctive.
- **Risk-adjusted accessibility — 9/10:** PyPI, Docker, scaffolding, and CI integrations ease evaluation, with large optional dependency sets clearly separated.
## Why it matters
- Tests MCP behavior directly without putting an LLM in the validation loop.
- Combines assertions, snapshots, load thresholds, manifest drift, Unicode instruction checks, SARIF, JUnit, and HTML evidence.
## Caveat
The repository's test-count and coverage claims were not rerun, and the tool validates MCP servers rather than model-answer quality or runtime defense.
## Sources
[Repository](https://github.com/vaquarkhan/mcp-test-harness) · [README](https://github.com/vaquarkhan/mcp-test-harness/blob/2b7bb513d3018aa928a386e10a174ae6020763b1/README.md) · [License](https://github.com/vaquarkhan/mcp-test-harness/blob/2b7bb513d3018aa928a386e10a174ae6020763b1/LICENSE)
