---
# catalog-derived-begin
title: "agentscope-ai/agentscope-java"
type: "repo-intel"
status: "active"
active: true
source_identity: "agentscope-ai/agentscope-java"
source: "https://github.com/agentscope-ai/agentscope-java"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 88
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "6ba5fefe0484ea3dda37cbeeb97b754f471ce7df"
readme_path: "README.md"
readme_url: "https://github.com/agentscope-ai/agentscope-java/blob/6ba5fefe0484ea3dda37cbeeb97b754f471ce7df/README.md"
metadata_observed: 2026-09-08
license_url: null
---
# agentscope-ai/agentscope-java
## Quick take
A production-oriented Java agent harness centered on permissions, event streams, sandboxes, subagents, and distributed recovery.
## Score
**88/100**
- **Harness relevance — 30/30:** The project is a core Java framework for long-running, safely controlled, distributed agents.
- **Practical pattern value — 25/25:** Typed events, tool permissions, middleware, sandboxes, subagents, and recoverable sessions are directly transferable harness patterns.
- **Evidence and maturity — 20/20:** The README identifies a 2.0 GA release, extensive documentation, Maven distribution, and institutional maintenance.
- **Novelty — 10/15:** Its combination of stateless agents, cross-replica recovery, and enterprise control-plane integration is distinctive.
- **Risk-adjusted accessibility — 3/10:** Maven setup is documented, but the repository evidence includes no immutable license URL and distributed backends add evaluation weight.
## Why it matters
- Offers concrete control-plane primitives for safe long-running execution and human approval.
- Demonstrates session persistence and subagent routing across service replicas.
## Caveat
The README labels the project Apache-2.0, but the captured repository metadata did not provide immutable license evidence; production-readiness claims remain README claims.
## Sources
[Repository](https://github.com/agentscope-ai/agentscope-java) · [README](https://github.com/agentscope-ai/agentscope-java/blob/6ba5fefe0484ea3dda37cbeeb97b754f471ce7df/README.md)
