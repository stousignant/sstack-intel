---
# catalog-derived-begin
title: "aohp-os/aohp"
type: "repo-intel"
status: "active"
active: true
source_identity: "aohp-os/aohp"
source: "https://github.com/aohp-os/aohp"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 76
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "b8ab9e98a2bd51f7fbd01a95d3b45dca078c5884"
readme_path: "README.md"
readme_url: "https://github.com/aohp-os/aohp/blob/b8ab9e98a2bd51f7fbd01a95d3b45dca078c5884/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/aohp-os/aohp/blob/b8ab9e98a2bd51f7fbd01a95d3b45dca078c5884/LICENSE"
---
# aohp-os/aohp
## Quick take
AOHP explores an Android-level agent harness that combines OS-native actions, personalized composition, and information-flow security.
## Score
**76/100**
- **Harness relevance — 29/30:** Makes agents first-class OS actors with interfaces, memory, skills, orchestration, and information-flow controls.
- **Practical pattern value — 16/25:** Agent-facing OS APIs and sensitive-value tracking are valuable patterns but difficult to transplant.
- **Evidence and maturity — 13/20:** The README supplies demos, a 30-task benchmark, security cases, build guidance, and Apache-2.0 licensing.
- **Novelty — 15/15:** An Android-level personalized agent harness with fine-grained information-flow tracking is unusually differentiated.
- **Risk-adjusted accessibility — 3/10:** Evaluation requires an Android 16 AOSP build and the README disclaims production and security-critical readiness.
## Why it matters
- It treats agent execution and sensitive-value flow as operating-system concerns rather than application add-ons.
- The demos and benchmark span GUI, non-GUI, event, retrieval, memory, and hybrid workflows.
## Caveat
The project explicitly says it is not ready for production or security-critical workloads, and reproducing it requires a substantial AOSP and Cuttlefish build.
## Sources
[Repository](https://github.com/aohp-os/aohp) · [README](https://github.com/aohp-os/aohp/blob/b8ab9e98a2bd51f7fbd01a95d3b45dca078c5884/README.md) · [License](https://github.com/aohp-os/aohp/blob/b8ab9e98a2bd51f7fbd01a95d3b45dca078c5884/LICENSE)
