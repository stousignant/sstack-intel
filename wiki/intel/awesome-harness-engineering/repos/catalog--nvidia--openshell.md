---
# catalog-derived-begin
title: "NVIDIA/OpenShell"
type: "repo-intel"
status: "active"
active: true
source_identity: "NVIDIA/OpenShell"
source: "https://github.com/NVIDIA/OpenShell"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
harness_intel_score: 94
score_confidence: high
availability: available
last_reviewed: 2026-09-08
review_state: reviewed
observed_revision: "6e6e6493b3df093540cfcc43b4a1df501470e561"
readme_path: "README.md"
readme_url: "https://github.com/NVIDIA/OpenShell/blob/6e6e6493b3df093540cfcc43b4a1df501470e561/README.md"
metadata_observed: "2026-09-08"
license_url: "https://github.com/NVIDIA/OpenShell/blob/6e6e6493b3df093540cfcc43b4a1df501470e561/LICENSE"
---

# NVIDIA/OpenShell

## Quick take

OpenShell is a top-tier reference for giving autonomous coding agents useful capabilities without unrestricted host, network, or credential access.[1][2] Its strongest catalog value is the integrated containment design, even where deployment would be operationally heavy.

## Score
**94/100**
- **Harness relevance — 30/30:** Directly addresses autonomous-agent containment.
- **Practical pattern value — 24/25:** Declarative policy, intercepted egress, credential mediation, and sandbox lifecycle are reusable patterns.
- **Evidence and maturity — 18/20:** NVIDIA-backed, actively developed, documented, and released; still explicitly alpha.[1][4]
- **Novelty — 14/15:** Integrates host containment, application-aware egress, credentials, and inference routing.
- **Risk-adjusted accessibility — 8/10:** Apache-2.0 and packaged releases help; runtime dependencies raise cost.[3][4]
## Review-time observations (2026-09-08)

- Availability: active; 8,533 stars and 1,260 forks at review time.[1]
- Reference-stack usage observation: **`not-used`**; a dated observation, not a quality verdict.

## Why it matters

- Demonstrates defense in depth across filesystem, process, network, inference, and credential boundaries.[2]
- Offers patterns for deny-by-default egress, credential stripping/injection, and isolated Hermes-like lanes.[2]

## Caveat

The project remains alpha, and some deployment paths are experimental.[2] This preview did not rerun code-level or runtime security verification.

## Sources

[1] https://github.com/NVIDIA/OpenShell
[2] https://github.com/NVIDIA/OpenShell/blob/main/README.md
[3] https://github.com/NVIDIA/OpenShell/blob/main/LICENSE
[4] https://github.com/NVIDIA/OpenShell/releases/tag/v0.0.116
