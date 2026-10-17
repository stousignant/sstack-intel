---
# catalog-derived-begin
title: "affaan-m/agentshield"
type: "repo-intel"
status: "active"
active: true
source_identity: "affaan-m/agentshield"
source: "https://github.com/affaan-m/agentshield"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 80
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "bdad15dd28da548a0586d6ca989cb5aa35a67ad6"
readme_path: "README.md"
readme_url: "https://github.com/affaan-m/agentshield/blob/bdad15dd28da548a0586d6ca989cb5aa35a67ad6/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/affaan-m/agentshield/blob/bdad15dd28da548a0586d6ca989cb5aa35a67ad6/LICENSE"
---
# affaan-m/agentshield
## Quick take
AgentShield is an agent-configuration security auditor with unusually broad checks for permissions, hooks, MCP servers, secrets, and supply-chain risks.
## Score
**80/100**
- **Harness relevance — 24/30:** Audits agent configuration, tool permissions, hooks, MCP servers, and prompt-injection exposure.
- **Practical pattern value — 22/25:** Its rule taxonomy, runtime-confidence labels, CI output, and evidence packs are reusable security patterns.
- **Evidence and maturity — 15/20:** The active project documents 102 rules, multiple integrations, tests, changelog, and an MIT license.
- **Novelty — 10/15:** Combines configuration scanning with agent-specific permission, hook, MCP, and supply-chain checks.
- **Risk-adjusted accessibility — 9/10:** The MIT CLI runs via npx and offers JSON output, though auto-fix and online analysis need care.
## Why it matters
- Its runtime-confidence model separates active configuration from examples and caches.
- Machine-readable CI reports and evidence packs make the rules useful beyond an interactive scan.
## Caveat
This review covers documented rules rather than measured detection accuracy; auto-fix and online or model-backed analysis expand the trust surface.
## Sources
[Repository](https://github.com/affaan-m/agentshield) · [README](https://github.com/affaan-m/agentshield/blob/bdad15dd28da548a0586d6ca989cb5aa35a67ad6/README.md) · [License](https://github.com/affaan-m/agentshield/blob/bdad15dd28da548a0586d6ca989cb5aa35a67ad6/LICENSE)
