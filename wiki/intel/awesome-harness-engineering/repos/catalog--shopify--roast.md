---
# catalog-derived-begin
title: "Shopify/roast"
type: "repo-intel"
status: "active"
active: true
source_identity: "Shopify/roast"
source: "https://github.com/Shopify/roast"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 86
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "0cd5406ea02ac8f64b8b7a697270fd4d84a57b2c"
readme_path: "README.md"
readme_url: "https://github.com/Shopify/roast/blob/0cd5406ea02ac8f64b8b7a697270fd4d84a57b2c/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/Shopify/roast/blob/0cd5406ea02ac8f64b8b7a697270fd4d84a57b2c/LICENSE.md"
---
# Shopify/roast
## Quick take
Roast is a strong declarative orchestration reference for composing model calls, coding agents, commands, code, and control flow.
## Score
**86/100**
- **Harness relevance — 27/30:** Provides a structured workflow runtime for chaining agent, model, command, and code steps.
- **Practical pattern value — 24/25:** The declarative cog model and ordinary-language escape hatch are directly transferable orchestration patterns.
- **Evidence and maturity — 17/20:** Shopify-backed active project documents a package, provider setup, examples, and an end-to-end example suite.
- **Novelty — 10/15:** The Ruby DSL is polished, but composable workflow runners are an established design.
- **Risk-adjusted accessibility — 8/10:** MIT licensing and a gem simplify access, while Ruby and external provider CLIs remain prerequisites.
## Why it matters
- Its cog DSL makes dependencies and data flow explicit without hiding ordinary Ruby.
- Serial and parallel collections, scopes, retries, and provider adapters map well to reusable task runners.
## Caveat
Using it requires Ruby plus separately installed and authenticated agent providers, and this review did not run workflows.
## Sources
[Repository](https://github.com/Shopify/roast) · [README](https://github.com/Shopify/roast/blob/0cd5406ea02ac8f64b8b7a697270fd4d84a57b2c/README.md) · [License](https://github.com/Shopify/roast/blob/0cd5406ea02ac8f64b8b7a697270fd4d84a57b2c/LICENSE.md)
