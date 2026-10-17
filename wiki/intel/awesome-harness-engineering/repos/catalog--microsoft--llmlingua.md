---
# catalog-derived-begin
title: "microsoft/LLMLingua"
type: "repo-intel"
status: "active"
active: true
source_identity: "microsoft/LLMLingua"
source: "https://github.com/microsoft/LLMLingua"
source_categories: [["Design Primitives","Context Delivery & Compaction"]]
source_occurrences: [["Design Primitives","Context Delivery & Compaction"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "e0e9d99beb94098bbd924aa53c2c112eac41c758"
readme_path: "README.md"
readme_url: "https://github.com/microsoft/LLMLingua/blob/e0e9d99beb94098bbd924aa53c2c112eac41c758/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/microsoft/LLMLingua/blob/e0e9d99beb94098bbd924aa53c2c112eac41c758/LICENSE"
---
# microsoft/LLMLingua
## Quick take
LLMLingua is a strong research-backed component for reducing the prompt and long-context burden of agent harnesses.
## Score
**81/100**
- **Harness relevance — 20/30:** Prompt compression is a substantial context-delivery component rather than a complete harness.
- **Practical pattern value — 21/25:** The compressor API and long-context variants are reusable in context-budget pipelines.
- **Evidence and maturity — 19/20:** Microsoft-backed project cites peer-reviewed papers, integrations, models, and maintained installation guidance.
- **Novelty — 14/15:** Task-aware and security-aware compression methods are a distinctive extension beyond simple truncation.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and pip installation help, but local compressor models and accuracy validation add cost.
## Why it matters
- Its compression APIs offer a concrete pre-context transformation stage.
- Multiple methods and reported token ratios provide design options for context-budget policies.
## Caveat
Compression adds model dependencies and can discard task-relevant information; this review did not reproduce accuracy claims.
## Sources
[Repository](https://github.com/microsoft/LLMLingua) · [README](https://github.com/microsoft/LLMLingua/blob/e0e9d99beb94098bbd924aa53c2c112eac41c758/README.md) · [License](https://github.com/microsoft/LLMLingua/blob/e0e9d99beb94098bbd924aa53c2c112eac41c758/LICENSE)
