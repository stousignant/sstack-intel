---
# catalog-derived-begin
title: "AgentOps-AI/agentops"
type: "repo-intel"
status: "active"
active: true
source_identity: "AgentOps-AI/agentops"
source: "https://github.com/AgentOps-AI/agentops"
source_categories: [["Design Primitives","Debugging & Developer Experience"]]
source_occurrences: [["Design Primitives","Debugging & Developer Experience"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 69
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "f8e907b92dabe47232978023fdcb01e2a7d4b752"
readme_path: "README.md"
readme_url: "https://github.com/AgentOps-AI/agentops/blob/f8e907b92dabe47232978023fdcb01e2a7d4b752/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/AgentOps-AI/agentops/blob/f8e907b92dabe47232978023fdcb01e2a7d4b752/LICENSE"
---
# AgentOps-AI/agentops
## Quick take
AgentOps instruments agent runs with traces, replay analytics, evaluations, and cost tracking.
## Score
**69/100**
- **Harness relevance — 20/30:** Provides observability, replay, evaluation, and cost tracking around agent executions.
- **Practical pattern value — 17/25:** Decorator-based spans and broad framework integrations are reusable instrumentation patterns.
- **Evidence and maturity — 20/20:** The active MIT project documents a Python package, self-hosted app, dashboard, and many named integrations.
- **Novelty — 5/15:** Agent tracing and cost dashboards are established patterns rather than an unusual harness architecture.
- **Risk-adjusted accessibility — 7/10:** The SDK is easy to install, but the full dashboard and API add service and account overhead.
## Why it matters
- Its session, agent, workflow, and operation spans map cleanly onto harness observability boundaries.
- Native integrations show how one telemetry layer can cover multiple agent frameworks.
## Caveat
The two-line SDK path is lightweight, but the complete replay experience depends on the AgentOps dashboard or a self-hosted application stack.
## Sources
[Repository](https://github.com/AgentOps-AI/agentops) · [README](https://github.com/AgentOps-AI/agentops/blob/f8e907b92dabe47232978023fdcb01e2a7d4b752/README.md) · [License](https://github.com/AgentOps-AI/agentops/blob/f8e907b92dabe47232978023fdcb01e2a7d4b752/LICENSE)
