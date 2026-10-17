---
# catalog-derived-begin
title: "Infisical/agent-vault"
type: "repo-intel"
status: "active"
active: true
source_identity: "Infisical/agent-vault"
source: "https://github.com/Infisical/agent-vault"
source_categories: [["Design Primitives","Permissions & Authorization"]]
source_occurrences: [["Design Primitives","Permissions & Authorization"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "bd1a325d79129644487f3e5b4f18c51adbc64638"
readme_path: "README.md"
readme_url: "https://github.com/Infisical/agent-vault/blob/bd1a325d79129644487f3e5b4f18c51adbc64638/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/Infisical/agent-vault/blob/bd1a325d79129644487f3e5b4f18c51adbc64638/LICENSE"
---
# Infisical/agent-vault
## Quick take
A credential-brokering proxy that lets agents call approved APIs without ever receiving the real secrets.
## Score
**81/100**
- **Harness relevance — 24/30:** Provides a credential boundary for agents and harnesses making outbound API requests.
- **Practical pattern value — 23/25:** Dummy credentials, outbound substitution, target controls, and pluggable secret stores are directly reusable patterns.
- **Evidence and maturity — 15/20:** The Infisical project documents releases, provenance attestation, deployment modes, SDK use, and production PostgreSQL.
- **Novelty — 13/15:** Brokering requests so an agent never receives the real secret is a distinctive security boundary.
- **Risk-adjusted accessibility — 6/10:** Basic use is documented, but operating a credential proxy creates a sensitive new enforcement and availability dependency.
## Why it matters
- Moves secret attachment to a controlled outbound boundary rather than trusting prompt-injection resistance.
- Supports local encrypted or external credential stores and release-artifact attestation.
## Caveat
The proxy becomes security-critical infrastructure, and the repository notes separate licensing for future enterprise code under its ee directory.
## Sources
[Repository](https://github.com/Infisical/agent-vault) · [README](https://github.com/Infisical/agent-vault/blob/bd1a325d79129644487f3e5b4f18c51adbc64638/README.md) · [License](https://github.com/Infisical/agent-vault/blob/bd1a325d79129644487f3e5b4f18c51adbc64638/LICENSE)
