---
# catalog-derived-begin
title: "huggingface/smolagents"
type: "repo-intel"
status: "active"
active: true
source_identity: "huggingface/smolagents"
source: "https://github.com/huggingface/smolagents"
source_categories: [["Reference Implementations","Tutorials & Educational"]]
source_occurrences: [["Reference Implementations","Tutorials & Educational"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "30bb1161095dbae2271e6bc3cc4c219cc3897a57"
readme_path: "README.md"
readme_url: "https://github.com/huggingface/smolagents/blob/30bb1161095dbae2271e6bc3cc4c219cc3897a57/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/huggingface/smolagents/blob/30bb1161095dbae2271e6bc3cc4c219cc3897a57/LICENSE"
---
# huggingface/smolagents
## Quick take
A deliberately small agent framework centered on code actions, broad model/tool adapters, and optional sandboxed execution.
## Score
**89/100**
- **Harness relevance — 30/30:** The library implements complete code-acting and tool-calling agent loops with model, tool, and sandbox integrations.
- **Practical pattern value — 22/25:** Minimal agent abstractions, pluggable executors, MCP tools, and model adapters are readily transferable.
- **Evidence and maturity — 20/20:** Long-lived active metadata, releases, institutional stewardship, and extensive documentation provide strong evidence.
- **Novelty — 8/15:** Code-first actions in a deliberately small framework are differentiated but build on established agent patterns.
- **Risk-adjusted accessibility — 9/10:** Apache-2.0 and a simple package install ease evaluation, with clear warnings around local code execution.
## Why it matters
- Provides a readable reference loop for code agents without a large abstraction stack.
- Makes sandbox choice and the limits of its local executor explicit.
## Caveat
Its local Python executor is explicitly not a security boundary, so untrusted code requires one of the external sandbox options.
## Sources
[Repository](https://github.com/huggingface/smolagents) · [README](https://github.com/huggingface/smolagents/blob/30bb1161095dbae2271e6bc3cc4c219cc3897a57/README.md) · [License](https://github.com/huggingface/smolagents/blob/30bb1161095dbae2271e6bc3cc4c219cc3897a57/LICENSE)
