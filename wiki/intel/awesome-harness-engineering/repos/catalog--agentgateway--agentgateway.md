---
# catalog-derived-begin
title: "agentgateway/agentgateway"
type: "repo-intel"
status: "active"
active: true
source_identity: "agentgateway/agentgateway"
source: "https://github.com/agentgateway/agentgateway"
source_categories: [["Design Primitives","Skills & MCP"]]
source_occurrences: [["Design Primitives","Skills & MCP"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "748b38b25d6e8c981c42e40b5e808d84c483c1bf"
readme_path: "README.md"
readme_url: "https://github.com/agentgateway/agentgateway/blob/748b38b25d6e8c981c42e40b5e808d84c483c1bf/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/agentgateway/agentgateway/blob/748b38b25d6e8c981c42e40b5e808d84c483c1bf/LICENSE"
---
# agentgateway/agentgateway
## Quick take
Agentgateway is an agent-native proxy for routing and governing LLM, tool, and agent-to-agent traffic.
## Score
**81/100**
- **Harness relevance — 20/30:** An MCP, A2A, and LLM gateway is a substantial connectivity and governance component of an agent harness.
- **Practical pattern value — 23/25:** Unified routing, authentication, policy, observability, and federation are directly reusable boundary patterns.
- **Evidence and maturity — 18/20:** Active development, Apache-2.0 licensing, detailed docs, and standalone and Kubernetes quickstarts are strong signals.
- **Novelty — 12/15:** Combining MCP, A2A, inference routing, and policy in one proxy is a distinctive package.
- **Risk-adjusted accessibility — 8/10:** A permissive license and standalone quickstart help, while the full Kubernetes surface adds complexity.
## Why it matters
- Provides a concrete shared boundary for MCP federation, A2A connectivity, authentication, and telemetry.
- Demonstrates framework-neutral policy and routing between agents and external capabilities.
## Caveat
README-level review does not verify operational behavior, and its broad gateway and Kubernetes options increase deployment scope.
## Sources
[Repository](https://github.com/agentgateway/agentgateway) · [README](https://github.com/agentgateway/agentgateway/blob/748b38b25d6e8c981c42e40b5e808d84c483c1bf/README.md) · [License](https://github.com/agentgateway/agentgateway/blob/748b38b25d6e8c981c42e40b5e808d84c483c1bf/LICENSE)
