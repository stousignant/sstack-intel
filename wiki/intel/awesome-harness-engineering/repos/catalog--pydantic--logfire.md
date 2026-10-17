---
# catalog-derived-begin
title: "pydantic/logfire"
type: "repo-intel"
status: "active"
active: true
source_identity: "pydantic/logfire"
source: "https://github.com/pydantic/logfire"
source_categories: [["Design Primitives","Observability & Tracing"]]
source_occurrences: [["Design Primitives","Observability & Tracing"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 65
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "49619ab15e331d59fa744fa4ba742ac32b017fc3"
readme_path: "README.md"
readme_url: "https://github.com/pydantic/logfire/blob/49619ab15e331d59fa744fa4ba742ac32b017fc3/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/pydantic/logfire/blob/49619ab15e331d59fa744fa4ba742ac32b017fc3/LICENSE"
---
# pydantic/logfire
## Quick take
An opinionated Python and agent observability SDK built on OpenTelemetry with portable backend export.
## Score
**65/100**
- **Harness relevance — 20/30:** Logfire is a substantial observability component for LLM, agent, and Python application harnesses.
- **Practical pattern value — 17/25:** OpenTelemetry traces, metrics, logs, Python instrumentation, and portable export offer reusable monitoring patterns.
- **Evidence and maturity — 20/20:** The Pydantic team maintains an active SDK with extensive integrations, documentation, and security reporting guidance.
- **Novelty — 5/15:** Its Python-friendly OpenTelemetry wrapper is useful but incremental relative to established observability stacks.
- **Risk-adjusted accessibility — 3/10:** The SDK is MIT and exports to OTel backends, but the hosted UI and server are closed source and self-hosting requires an enterprise license.
## Why it matters
- Provides low-friction tracing and instrumentation across Python applications and LLM systems.
- Keeps telemetry compatible with external OpenTelemetry backends rather than locking data to one destination.
## Caveat
Only the SDK and documentation are open source; the Logfire application backend and UI are closed source, with enterprise licensing required for self-hosting.
## Sources
[Repository](https://github.com/pydantic/logfire) · [README](https://github.com/pydantic/logfire/blob/49619ab15e331d59fa744fa4ba742ac32b017fc3/README.md) · [License](https://github.com/pydantic/logfire/blob/49619ab15e331d59fa744fa4ba742ac32b017fc3/LICENSE)
