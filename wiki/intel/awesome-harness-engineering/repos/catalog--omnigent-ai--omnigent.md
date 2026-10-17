---
# catalog-derived-begin
title: "omnigent-ai/omnigent"
type: "repo-intel"
status: "active"
active: true
source_identity: "omnigent-ai/omnigent"
source: "https://github.com/omnigent-ai/omnigent"
source_categories: [["Reference Implementations","Generators & Meta-Harnesses"]]
source_occurrences: [["Reference Implementations","Generators & Meta-Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 91
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "943848d8d3d7e298d70ffe096924578791503779"
readme_path: "README.md"
readme_url: "https://github.com/omnigent-ai/omnigent/blob/943848d8d3d7e298d70ffe096924578791503779/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/omnigent-ai/omnigent/blob/943848d8d3d7e298d70ffe096924578791503779/LICENSE"
---
# omnigent-ai/omnigent
## Quick take
Omnigent provides one orchestration and policy layer over several coding agents, models, clients, and sandboxes.
## Score
**91/100**
- **Harness relevance — 30/30:** Provides a core meta-harness for orchestrating, supervising, governing, and sandboxing multiple agent runtimes.
- **Practical pattern value — 25/25:** Adapter, policy, approval, spend-limit, sandbox, and synchronized-session patterns are directly transferable.
- **Evidence and maturity — 14/20:** The active Apache-2.0 project documents packaged installs, many integrations, remote clients, and sandbox providers, but is new.
- **Novelty — 15/15:** Combining cross-harness sessions, collaboration, device continuity, and policy enforcement is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** It is packaged, but the breadth of runtimes, cloud providers, and mandatory Linux sandboxing adds setup complexity.
## Why it matters
- Allows heterogeneous agents to share sessions and supervise one another.
- Applies approval, tool, spend, and sandbox policies at server, agent, or chat scope.
## Caveat
The broad integration surface brings Python, Node, terminal, sandbox, and optional cloud-provider dependencies; Linux terminal wrappers require bubblewrap isolation.
## Sources
[Repository](https://github.com/omnigent-ai/omnigent) · [README](https://github.com/omnigent-ai/omnigent/blob/943848d8d3d7e298d70ffe096924578791503779/README.md) · [License](https://github.com/omnigent-ai/omnigent/blob/943848d8d3d7e298d70ffe096924578791503779/LICENSE)
