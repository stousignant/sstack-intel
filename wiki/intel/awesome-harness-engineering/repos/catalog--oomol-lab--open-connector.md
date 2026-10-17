---
# catalog-derived-begin
title: "oomol-lab/open-connector"
type: "repo-intel"
status: "active"
active: true
source_identity: "oomol-lab/open-connector"
source: "https://github.com/oomol-lab/open-connector"
source_categories: [["Design Primitives","Skills & MCP"]]
source_occurrences: [["Design Primitives","Skills & MCP"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "03992d5e16e01bd281811b263ef09596efa249eb"
readme_path: "README.md"
readme_url: "https://github.com/oomol-lab/open-connector/blob/03992d5e16e01bd281811b263ef09596efa249eb/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/oomol-lab/open-connector/blob/03992d5e16e01bd281811b263ef09596efa249eb/LICENSE.txt"
---
# oomol-lab/open-connector
## Quick take
An inspectable credential and action gateway that exposes one SaaS connector catalog across agent protocols.
## Score
**81/100**
- **Harness relevance — 20/30:** Credentialed SaaS actions and MCP or OpenAPI exposure are substantial agent-tooling components.
- **Practical pattern value — 24/25:** Stable action schemas, credential isolation, runtime tokens, scopes, policies, and redacted logs are directly transferable.
- **Evidence and maturity — 17/20:** The active Apache-2.0 project documents tests, deployment options, migration boundaries, and a large connector catalog.
- **Novelty — 13/15:** It keeps provider secrets behind one gateway while preserving action identities across SDK, CLI, MCP, HTTP, and hosted modes.
- **Risk-adjusted accessibility — 7/10:** Docker quick start is approachable, but OAuth providers require registered apps or a hosted service.
## Why it matters
- Provides a useful boundary where agents receive schemas and results without receiving provider secrets.
- Keeps action identities and contracts stable across self-hosted and managed deployment paths.
## Caveat
Connector breadth is a README claim, and credentialed evaluation requires provider-specific OAuth apps or OOMOL hosting.
## Sources
[Repository](https://github.com/oomol-lab/open-connector) · [README](https://github.com/oomol-lab/open-connector/blob/03992d5e16e01bd281811b263ef09596efa249eb/README.md) · [License](https://github.com/oomol-lab/open-connector/blob/03992d5e16e01bd281811b263ef09596efa249eb/LICENSE.txt)
