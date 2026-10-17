---
# catalog-derived-begin
title: "deeplethe/forkd"
type: "repo-intel"
status: "active"
active: true
source_identity: "deeplethe/forkd"
source: "https://github.com/deeplethe/forkd"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 78
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "07a1ffb1543c0f7e12719064c881ae769cf4dcec"
readme_path: "README.md"
readme_url: "https://github.com/deeplethe/forkd/blob/07a1ffb1543c0f7e12719064c881ae769cf4dcec/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/deeplethe/forkd/blob/07a1ffb1543c0f7e12719064c881ae769cf4dcec/LICENSE"
---
# deeplethe/forkd
## Quick take
forkd is a high-signal sandbox primitive for rapidly cloning warm Firecracker microVMs and branching live agent state.
## Score
**78/100**
- **Harness relevance — 24/30:** Provides isolated, forkable microVM execution specifically for agent fan-out and evaluation workloads.
- **Practical pattern value — 20/25:** Warm parents, copy-on-write children, live branching, snapshot chains, and SDK surfaces are strong infrastructure patterns.
- **Evidence and maturity — 16/20:** The active Apache-2.0 project publishes CI, releases, benchmark methodology, results, and operational documentation.
- **Novelty — 15/15:** Fork-like microVM cloning and mid-execution branching are unusually differentiated agent-sandbox primitives.
- **Risk-adjusted accessibility — 3/10:** It requires Linux, KVM, userfaultfd or elevated capability, and a vendored Firecracker build.
## Why it matters
- Copy-on-write memory and snapshot chains target the cost of parallel agent exploration without dropping VM isolation.
- Live branching creates a concrete execution primitive for counterfactual search and fan-out from in-flight state.
## Caveat
The specialized Linux, KVM, userfaultfd, and Firecracker requirements make local evaluation operationally heavy, and one documented CLI composition path remains incomplete.
## Sources
[Repository](https://github.com/deeplethe/forkd) · [README](https://github.com/deeplethe/forkd/blob/07a1ffb1543c0f7e12719064c881ae769cf4dcec/README.md) · [License](https://github.com/deeplethe/forkd/blob/07a1ffb1543c0f7e12719064c881ae769cf4dcec/LICENSE)
