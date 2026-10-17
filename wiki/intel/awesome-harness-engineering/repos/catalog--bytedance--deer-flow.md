---
# catalog-derived-begin
title: "bytedance/deer-flow"
type: "repo-intel"
status: "active"
active: true
source_identity: "bytedance/deer-flow"
source: "https://github.com/bytedance/deer-flow"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 95
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "062273f850902ee4072626cad2dc0f614a386aad"
readme_path: "README.md"
readme_url: "https://github.com/bytedance/deer-flow/blob/062273f850902ee4072626cad2dc0f614a386aad/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/bytedance/deer-flow/blob/062273f850902ee4072626cad2dc0f614a386aad/LICENSE"
---
# bytedance/deer-flow
## Quick take
A full long-horizon super-agent harness integrating subagents, memory, skills, sandboxed execution, tracing, and message delivery.
## Score
**95/100**
- **Harness relevance — 30/30:** README describes a complete long-horizon harness with subagents, memory, skills, tools, sandboxes, and gateways.
- **Practical pattern value — 25/25:** Setup diagnostics, sandbox controls, compaction, subagent limits, tracing, and durable delivery receipts are directly transferable.
- **Evidence and maturity — 20/20:** Institutional ownership, active metadata, extensive documentation, and operational tooling provide strong maturity evidence.
- **Novelty — 13/15:** The integrated long-horizon stack and explicit delivery/event semantics form a distinctive combination.
- **Risk-adjusted accessibility — 7/10:** MIT licensing helps, but the Python/Node stack, model services, and optional sandbox infrastructure are substantial.
## Why it matters
- Provides unusually detailed operational patterns for setup diagnosis, run correlation, recovery, and durable delivery receipts.
- Combines context compaction, bounded subagents, sandboxes, and observability in one reference implementation.
## Caveat
The 2.0 rewrite is operationally broad and infrastructure-heavy, so individual patterns are easier to assess than the complete deployment.
## Sources
[Repository](https://github.com/bytedance/deer-flow) · [README](https://github.com/bytedance/deer-flow/blob/062273f850902ee4072626cad2dc0f614a386aad/README.md) · [License](https://github.com/bytedance/deer-flow/blob/062273f850902ee4072626cad2dc0f614a386aad/LICENSE)
