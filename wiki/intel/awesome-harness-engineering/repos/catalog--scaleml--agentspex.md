---
# catalog-derived-begin
title: "ScaleML/AgentSPEX"
type: "repo-intel"
status: "active"
active: true
source_identity: "ScaleML/AgentSPEX"
source: "https://github.com/ScaleML/AgentSPEX"
source_categories: [["Design Primitives","Agent Loop"]]
source_occurrences: [["Design Primitives","Agent Loop"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 84
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "db99b7b6802fe15ef2997c82ec1d49e5228128f6"
readme_path: "README.md"
readme_url: "https://github.com/ScaleML/AgentSPEX/blob/db99b7b6802fe15ef2997c82ec1d49e5228128f6/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/ScaleML/AgentSPEX/blob/db99b7b6802fe15ef2997c82ec1d49e5228128f6/LICENSE"
---
# ScaleML/AgentSPEX
## Quick take
AgentSPEX is a declarative language and execution harness for explicit, modular, reproducible agent pipelines.
## Score
**84/100**
- **Harness relevance — 29/30:** Defines and executes complete agent pipelines with explicit control flow, tools, state, traces, and sandboxing.
- **Practical pattern value — 22/25:** Declarative steps, parameters, loops, conditions, parallelism, sub-workflows, checkpoints, resume, and replay transfer directly.
- **Evidence and maturity — 13/20:** The Apache-2.0 reference implementation has a paper, language guide, examples, and quickstart but limited maturity evidence.
- **Novelty — 14/15:** A specification language joining explicit workflow control with reproducible execution and trace replay is highly differentiated.
- **Risk-adjusted accessibility — 6/10:** Conda, API keys, Docker, a sandbox VM, and optional persistent services make evaluation moderately heavy.
## Why it matters
- Loops, conditions, parallel steps, sub-workflows, and parameters make orchestration inspectable as data.
- Run-scoped outputs, checkpoints, resume, and trace replay provide a useful reproducibility contract.
## Caveat
This is a young paper implementation with a multi-step Conda and Docker setup; README-level review does not establish language stability or production behavior.
## Sources
[Repository](https://github.com/ScaleML/AgentSPEX) · [README](https://github.com/ScaleML/AgentSPEX/blob/db99b7b6802fe15ef2997c82ec1d49e5228128f6/README.md) · [License](https://github.com/ScaleML/AgentSPEX/blob/db99b7b6802fe15ef2997c82ec1d49e5228128f6/LICENSE)
