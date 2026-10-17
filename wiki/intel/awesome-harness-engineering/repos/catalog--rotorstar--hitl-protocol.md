---
# catalog-derived-begin
title: "rotorstar/hitl-protocol"
type: "repo-intel"
status: "active"
active: true
source_identity: "rotorstar/hitl-protocol"
source: "https://github.com/rotorstar/hitl-protocol"
source_categories: [["Design Primitives","Human-in-the-Loop"]]
source_occurrences: [["Design Primitives","Human-in-the-Loop"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "655eba84932669af057e3cd9cacb1c94ae51ae65"
readme_path: "README.md"
readme_url: "https://github.com/rotorstar/hitl-protocol/blob/655eba84932669af057e3cd9cacb1c94ae51ae65/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/rotorstar/hitl-protocol/blob/655eba84932669af057e3cd9cacb1c94ae51ae65/LICENSE"
---
# rotorstar/hitl-protocol
## Quick take
HITL Protocol standardizes how services pause agent workflows and obtain structured, auditable human decisions.
## Score
**81/100**
- **Harness relevance — 20/30:** Defines a substantial human-decision boundary for agent and service workflows rather than a complete harness.
- **Practical pattern value — 25/25:** HTTP 202 handoff, typed reviews, polling, audit state, and URL fallback are directly transferable.
- **Evidence and maturity — 14/20:** The active Apache-2.0 project documents v0.8, OpenAPI and JSON schemas, reference implementations, and compliance tests.
- **Novelty — 15/15:** A framework-neutral service-to-human decision protocol with service-held state is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** Plain HTTP lowers integration cost, but the standard is young and identity and authorization remain separate concerns.
## Why it matters
- Keeps approval state on the service side instead of relying on compactable agent context.
- Provides framework-neutral HTTP polling plus typed review forms and URL fallbacks.
## Caveat
Version 0.8 standardizes proof of human but explicitly leaves identity, authorization, and agent binding to separate systems.
## Sources
[Repository](https://github.com/rotorstar/hitl-protocol) · [README](https://github.com/rotorstar/hitl-protocol/blob/655eba84932669af057e3cd9cacb1c94ae51ae65/README.md) · [License](https://github.com/rotorstar/hitl-protocol/blob/655eba84932669af057e3cd9cacb1c94ae51ae65/LICENSE)
