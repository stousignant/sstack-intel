---
# catalog-derived-begin
title: "nearai/ironclaw"
type: "repo-intel"
status: "active"
active: true
source_identity: "nearai/ironclaw"
source: "https://github.com/nearai/ironclaw"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
harness_intel_score: 91
score_confidence: high
availability: available
last_reviewed: 2026-09-08
review_state: reviewed
observed_revision: "0280dd1a48a4f813f123735b31558c459d1ce032"
readme_path: "README.md"
readme_url: "https://github.com/nearai/ironclaw/blob/0280dd1a48a4f813f123735b31558c459d1ce032/README.md"
metadata_observed: "2026-09-08"
license_url: "https://github.com/nearai/ironclaw/blob/0280dd1a48a4f813f123735b31558c459d1ce032/LICENSE-MIT"
---

# nearai/ironclaw

## Quick take

IronClaw is a high-signal reference architecture for capability-based agent containment and protected tool execution.[1][2] Its patterns are more valuable here than adopting another complete agent runtime.

## Score
**91/100**
- **Harness relevance — 28/30:** WASM isolation, capabilities, secrets, egress, approvals, and injection controls directly serve secure harnesses.[2]
- **Practical pattern value — 23/25:** The host-boundary design can strengthen Hermes without replacing it.
- **Evidence and maturity — 18/20:** Active, documented, permissively licensed, and recently released.[1][3][4]
- **Novelty — 14/15:** Unusually complete combination of capability-scoped tools and protected credentials.
- **Risk-adjusted accessibility — 8/10:** Installers help, but the broad runtime and generated-tool surface require isolation.[2]
## Review-time observations (2026-09-08)

- Availability: active; 12,607 stars and 1,478 forks at review time.[1]
- Reference-stack usage observation: **`reference-only`**; a dated observation, not an adoption verdict.

## Why it matters

- Provides a coherent model across WASM permissions, endpoint allowlists, secret protection, approvals, and output sanitization.[2]
- Can inform a stronger Hermes host boundary without becoming the active runtime.

## Caveat

Current security features were reviewed at README depth only.[2] Direct adoption would add an overlapping Agent OS plus execution, credential, and web-control surfaces.

## Sources

[1] https://github.com/nearai/ironclaw
[2] https://github.com/nearai/ironclaw/blob/main/README.md
[3] https://github.com/nearai/ironclaw/blob/main/LICENSE-MIT
[4] https://github.com/nearai/ironclaw/releases/tag/ironclaw-v1.4.0
