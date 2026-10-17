---
# catalog-derived-begin
title: "langchain-ai/langgraph"
type: "repo-intel"
status: "active"
active: true
source_identity: "langchain-ai/langgraph"
source: "https://github.com/langchain-ai/langgraph"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"],["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 93
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "81bf17b23123e4ef8b9d5f49fa09a0122fc2edd1"
readme_path: "README.md"
readme_url: "https://github.com/langchain-ai/langgraph/blob/81bf17b23123e4ef8b9d5f49fa09a0122fc2edd1/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/langchain-ai/langgraph/blob/81bf17b23123e4ef8b9d5f49fa09a0122fc2edd1/LICENSE"
---
# langchain-ai/langgraph
## Quick take
A low-level graph runtime for durable, stateful agents with resumable execution, human interrupts, memory, and observability integrations.
## Score
**93/100**
- **Harness relevance — 30/30:** LangGraph is core orchestration infrastructure for long-running, stateful agents.
- **Practical pattern value — 24/25:** Durable execution, interrupts, stateful memory, subgraphs, and deployment patterns are directly transferable.
- **Evidence and maturity — 20/20:** Long-lived active metadata, releases, extensive docs, and institutional usage claims provide strong maturity evidence.
- **Novelty — 10/15:** Its graph runtime combines established workflow ideas into a distinctive agent-focused state model.
- **Risk-adjusted accessibility — 9/10:** MIT licensing and pip installation lower friction, though production tooling spans a broader commercial ecosystem.
## Why it matters
- Provides mature primitives for checkpoints, failure recovery, and human modification of in-flight state.
- Separates a low-level orchestration substrate from higher-level agent packages.
## Caveat
The open framework is usable standalone, but several debugging, deployment, and production paths point into the wider LangSmith ecosystem.
## Sources
[Repository](https://github.com/langchain-ai/langgraph) · [README](https://github.com/langchain-ai/langgraph/blob/81bf17b23123e4ef8b9d5f49fa09a0122fc2edd1/README.md) · [License](https://github.com/langchain-ai/langgraph/blob/81bf17b23123e4ef8b9d5f49fa09a0122fc2edd1/LICENSE)
