---
# catalog-derived-begin
title: "kubernetes-sigs/agent-sandbox"
type: "repo-intel"
status: "active"
active: true
source_identity: "kubernetes-sigs/agent-sandbox"
source: "https://github.com/kubernetes-sigs/agent-sandbox"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
harness_intel_score: 87
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
review_state: reviewed
observed_revision: "e5e2831295a789299722a9f4d922250167b1e879"
readme_path: "README.md"
readme_url: "https://github.com/kubernetes-sigs/agent-sandbox/blob/e5e2831295a789299722a9f4d922250167b1e879/README.md"
metadata_observed: "2026-09-08"
license_url: "https://github.com/kubernetes-sigs/agent-sandbox/blob/e5e2831295a789299722a9f4d922250167b1e879/LICENSE"
---

# kubernetes-sigs/agent-sandbox

## Quick take

A strong reference for Kubernetes-scale agent isolation, especially declarative lifecycle and warm-pool patterns.[1][2] It orchestrates sandboxes rather than supplying the underlying security boundary.

## Score
**87/100**
- **Harness relevance — 29/30:** Directly manages isolated, persistent environments for agents and generated code.[2]
- **Practical pattern value — 23/25:** CRDs, templates, claims, warm pools, stable identity, and pause/resume form a useful control plane.[2]
- **Evidence and maturity — 16/20:** Kubernetes SIG stewardship, active development, docs, releases, and Apache-2.0 are positive signals.[1][3]
- **Novelty — 13/15:** Packages stateful singleton workloads and pre-warmed allocation for agent/eval use.
- **Risk-adjusted accessibility — 6/10:** Requires Kubernetes expertise plus a separate runtime such as gVisor or Kata Containers.[2]
## Review-time observations (2026-09-08)

- Availability: active; 3,770 stars and 489 forks at review time.[1]

## Why it matters

- Provides a control-plane pattern for persistent, resumable, individually addressable agent environments.[2]
- Cleanly separates sandbox lifecycle orchestration from low-level runtime isolation.[2]

## Caveat

No implementation or cluster test was performed. Security depends on Kubernetes configuration and the selected sandbox runtime, not this controller alone.[2]

## Sources

[1] https://github.com/kubernetes-sigs/agent-sandbox
[2] https://github.com/kubernetes-sigs/agent-sandbox/blob/main/README.md
[3] https://github.com/kubernetes-sigs/agent-sandbox/blob/main/LICENSE
