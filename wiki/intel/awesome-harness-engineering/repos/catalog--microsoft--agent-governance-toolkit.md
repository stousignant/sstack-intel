---
# catalog-derived-begin
title: "microsoft/agent-governance-toolkit"
type: "repo-intel"
status: "active"
active: true
source_identity: "microsoft/agent-governance-toolkit"
source: "https://github.com/microsoft/agent-governance-toolkit"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
harness_intel_score: 88
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
review_state: reviewed
observed_revision: "359a2332f57d9000924baba269ed24e4e15ad8b0"
readme_path: "README.md"
readme_url: "https://github.com/microsoft/agent-governance-toolkit/blob/359a2332f57d9000924baba269ed24e4e15ad8b0/README.md"
metadata_observed: "2026-09-08"
license_url: "https://github.com/microsoft/agent-governance-toolkit/blob/359a2332f57d9000924baba269ed24e4e15ad8b0/LICENSE"
---

# microsoft/agent-governance-toolkit

## Quick take

A strong catalog entry for deterministic governance around agent actions rather than prompt-only safety.[1][2] Its best contribution is the layered policy, identity, audit, and reliability model.

## Score
**88/100**
- **Harness relevance — 29/30:** Directly targets policy enforcement, identity, audit, execution controls, and MCP governance.[2]
- **Practical pattern value — 23/25:** Pre-execution gates, fail-closed decisions, privilege rings, and audit evidence are reusable.
- **Evidence and maturity — 15/20:** Microsoft-owned, active, documented, and packaged, but still public preview.[1][2]
- **Novelty — 13/15:** Combines governance, identity, compliance, and SRE in one framework-neutral layer.
- **Risk-adjusted accessibility — 8/10:** MIT and short quick starts help; breadth and preview-stage churn add risk.[2][3]
## Review-time observations (2026-09-08)

- Availability: active; 6,219 stars and 1,113 forks at review time.[1]

## Why it matters

- Shows how to gate tool calls deterministically before side effects.[2]
- Connects policy decisions with agent identity, audit evidence, MCP controls, and operational kill switches.[2]

## Caveat

This was not code-inspected or executed. Broad feature and standards-coverage claims remain README claims, and the project warns that public-preview APIs may break.[2]

## Sources

[1] https://github.com/microsoft/agent-governance-toolkit
[2] https://github.com/microsoft/agent-governance-toolkit/blob/main/README.md
[3] https://github.com/microsoft/agent-governance-toolkit/blob/main/LICENSE
