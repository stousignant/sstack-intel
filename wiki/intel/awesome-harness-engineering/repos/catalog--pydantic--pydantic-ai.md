---
# catalog-derived-begin
title: "pydantic/pydantic-ai"
type: "repo-intel"
status: "active"
active: true
source_identity: "pydantic/pydantic-ai"
source: "https://github.com/pydantic/pydantic-ai"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 92
score_confidence: high
availability: available
last_reviewed: 2026-09-12
observed_revision: "62f1e8302a356d09962c55117f41a282cf1eb243"
readme_path: "README.md"
readme_url: "https://github.com/pydantic/pydantic-ai/blob/62f1e8302a356d09962c55117f41a282cf1eb243/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/pydantic/pydantic-ai/blob/62f1e8302a356d09962c55117f41a282cf1eb243/LICENSE"
---
# pydantic/pydantic-ai
## Quick take
A mature typed Python agent SDK with composable capabilities, durable execution, evals, and a companion coding harness.
## Score
**92/100**
- **Harness relevance — 28/30:** The typed agent loop, tools, capabilities, durable execution, and companion harness are core functions.
- **Practical pattern value — 24/25:** Composable capabilities, typed dependencies and outputs, evals, and durable adapters are directly transferable.
- **Evidence and maturity — 20/20:** The active MIT project has institutional stewardship, CI, stated full coverage, packages, and extensive documentation.
- **Novelty — 11/15:** Typed capability composition across CLI, web, voice, durable workflows, and coding agents is a distinctive combination.
- **Risk-adjusted accessibility — 9/10:** MIT, uv installation, many model adapters, and a built-in test model make evaluation straightforward.
## Why it matters
- Makes tools, dependencies, outputs, and reusable capability bundles visible to both type checkers and models.
- Runs one agent definition across ordinary calls, queues, web, CLI, voice, and harness compositions.
## Durable execution
- Pydantic AI officially supports Temporal, DBOS, Prefect, Restate, and AWS Lambda durable functions; third-party runtime authors can use its stable durable-backend builder.
- With Temporal, deterministic agent coordination runs in a Workflow while model requests, I/O-capable tools, validators, and MCP communication run as retryable Activities.
- `TemporalDurability` is the current capability API. The older `TemporalAgent` wrapper remains documented but is deprecated.
- Production use requires stable agent/toolset identifiers, idempotent effects, explicit activity retry policy, payload/history discipline, and Temporal replay/versioning compatibility. Layered provider, transport, and Temporal retries can multiply model calls and cost.
## Caveat
The fullest coding-harness features live in the separate pydantic-ai-harness package, and some interfaces remain experimental. Durable support supplies framework integration, not a managed Temporal service or zero-operations deployment.
## Sources
[Repository](https://github.com/pydantic/pydantic-ai) · [README](https://github.com/pydantic/pydantic-ai/blob/62f1e8302a356d09962c55117f41a282cf1eb243/README.md) · [License](https://github.com/pydantic/pydantic-ai/blob/62f1e8302a356d09962c55117f41a282cf1eb243/LICENSE) · [Durable execution](https://ai.pydantic.dev/durable_execution/overview/) · [Temporal integration](https://ai.pydantic.dev/durable_execution/temporal/)
