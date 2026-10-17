---
# catalog-derived-begin
title: "truefoundry/trueforge"
type: "repo-intel"
status: "active"
active: true
source_identity: "truefoundry/trueforge"
source: "https://github.com/truefoundry/trueforge"
source_categories: [["Production Infrastructure & Operations"]]
source_occurrences: [["Production Infrastructure & Operations"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "6ca52de4788fbf66b995c80a60cedea1cabc8490"
readme_path: "README.md"
readme_url: "https://github.com/truefoundry/trueforge/blob/6ca52de4788fbf66b995c80a60cedea1cabc8490/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/truefoundry/trueforge/blob/6ca52de4788fbf66b995c80a60cedea1cabc8490/LICENSE"
---
# truefoundry/trueforge
## Quick take
A broad open-source agent runtime that packages execution loops, MCP, skills, approvals, sandboxing, context management, sessions, APIs, and UI.
## Score
**89/100**
- **Harness relevance — 30/30:** A full agent harness runtime covering model calls, tools, skills, sandboxing, approvals, context, sessions, API, and UI.
- **Practical pattern value — 24/25:** Deferred tools, sandbox-as-tool, subagents, compaction, approval checkpoints, resource catalogs, and local/hosted separation are directly reusable.
- **Evidence and maturity — 15/20:** Active MIT project with documentation, quickstarts, SDK/UI surfaces, deployment modes, and benchmark materials, though it is young.
- **Novelty — 12/15:** The integrated local-to-hosted runtime plus embeddable UI and context-management features form a strong combination.
- **Risk-adjusted accessibility — 8/10:** One-command local evaluation is easy, but production mode adds Postgres, Redis, authentication, and external sandbox-provider concerns.
## Why it matters
- Its local-versus-hosted architecture makes the operational boundary from personal trial to multi-replica service explicit.
- Deferred tool loading, Code Mode, compaction, and sandbox-as-tool offer concrete context and capability-management references.
## Caveat
Local mode has no login and is explicitly unsuitable for internet-facing use; hosted claims and benchmark results were not independently exercised.
## Sources
[Repository](https://github.com/truefoundry/trueforge) · [README](https://github.com/truefoundry/trueforge/blob/6ca52de4788fbf66b995c80a60cedea1cabc8490/README.md) · [License](https://github.com/truefoundry/trueforge/blob/6ca52de4788fbf66b995c80a60cedea1cabc8490/LICENSE)
