---
# catalog-derived-begin
title: "BerriAI/litellm"
type: "repo-intel"
status: "active"
active: true
source_identity: "BerriAI/litellm"
source: "https://github.com/BerriAI/litellm"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 73
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "1af7a403c66e037bec2e0ae6ea455a1c10b17b1b"
readme_path: "README.md"
readme_url: "https://github.com/BerriAI/litellm/blob/1af7a403c66e037bec2e0ae6ea455a1c10b17b1b/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/BerriAI/litellm/blob/1af7a403c66e037bec2e0ae6ea455a1c10b17b1b/LICENSE"
---
# BerriAI/litellm
## Quick take
LiteLLM supplies a unified SDK and gateway for routing harness traffic across many model providers and agent protocols.
## Score
**73/100**
- **Harness relevance — 20/30:** Acts as a substantial model and agent gateway component rather than a complete agent harness.
- **Practical pattern value — 25/25:** Unified provider APIs, routing, retries, budgets, guardrails, and MCP/A2A gateways are directly transferable.
- **Evidence and maturity — 20/20:** The active project documents stable images, load testing, SDK and proxy paths, and broad provider support.
- **Novelty — 5/15:** Provider normalization and gateway controls are mature infrastructure patterns, not a novel harness design.
- **Risk-adjusted accessibility — 3/10:** It is readily packaged, but the full gateway is operationally heavy and the observed license is not clearly classified.
## Why it matters
- Provides practical retry, fallback, spend, guardrail, and observability controls at the model boundary.
- Its OpenAI-compatible proxy can decouple harness code from provider-specific APIs.
## Caveat
This is gateway infrastructure rather than an end-to-end harness, and the captured license metadata is NOASSERTION despite a license file.
## Sources
[Repository](https://github.com/BerriAI/litellm) · [README](https://github.com/BerriAI/litellm/blob/1af7a403c66e037bec2e0ae6ea455a1c10b17b1b/README.md) · [License](https://github.com/BerriAI/litellm/blob/1af7a403c66e037bec2e0ae6ea455a1c10b17b1b/LICENSE)
