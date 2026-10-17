---
# catalog-derived-begin
title: "traceloop/openllmetry"
type: "repo-intel"
status: "active"
active: true
source_identity: "traceloop/openllmetry"
source: "https://github.com/traceloop/openllmetry"
source_categories: [["Design Primitives","Observability & Tracing"]]
source_occurrences: [["Design Primitives","Observability & Tracing"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 82
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "62e24c2ffde6c1ee04dc290e52d8d5dbda054cff"
readme_path: "README.md"
readme_url: "https://github.com/traceloop/openllmetry/blob/62e24c2ffde6c1ee04dc290e52d8d5dbda054cff/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/traceloop/openllmetry/blob/62e24c2ffde6c1ee04dc290e52d8d5dbda054cff/LICENSE"
---
# traceloop/openllmetry
## Quick take
An OpenTelemetry-based instrumentation suite for tracing LLM providers, agent frameworks, and vector databases.
## Score
**82/100**
- **Harness relevance — 20/30:** OpenLLMetry is a substantial observability component for LLM and agent harnesses.
- **Practical pattern value — 25/25:** Standard OpenTelemetry instrumentations, LLM semantic conventions, provider hooks, vector-database traces, and backend portability are directly transferable.
- **Evidence and maturity — 20/20:** The established project documents many tested destinations and integrations, active maintenance, and semantic-convention adoption by OpenTelemetry.
- **Novelty — 10/15:** Combining LLM-specific spans with standard OpenTelemetry pipelines is distinctive, though observability instrumentation is established practice.
- **Risk-adjusted accessibility — 7/10:** Apache-2.0 licensing and a small SDK entry point ease trials, while telemetry handling still requires privacy and backend configuration.
## Why it matters
- Lets harnesses emit standard telemetry to existing observability backends.
- Provides LLM-specific semantic conventions and broad automatic instrumentation coverage.
## Caveat
Instrumentation can capture prompts, responses, and other sensitive application data, so exporters and telemetry policy need deliberate configuration.
## Sources
[Repository](https://github.com/traceloop/openllmetry) · [README](https://github.com/traceloop/openllmetry/blob/62e24c2ffde6c1ee04dc290e52d8d5dbda054cff/README.md) · [License](https://github.com/traceloop/openllmetry/blob/62e24c2ffde6c1ee04dc290e52d8d5dbda054cff/LICENSE)
