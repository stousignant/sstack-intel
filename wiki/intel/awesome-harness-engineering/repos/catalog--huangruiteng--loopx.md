---
# catalog-derived-begin
title: "huangruiteng/loopx"
type: "repo-intel"
status: "active"
active: true
source_identity: "huangruiteng/loopx"
source: "https://github.com/huangruiteng/loopx"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 91
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "f0375cc621cf8201ea457dfafeda5c938f1663a0"
readme_path: "README.md"
readme_url: "https://github.com/huangruiteng/loopx/blob/f0375cc621cf8201ea457dfafeda5c938f1663a0/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/huangruiteng/loopx/blob/f0375cc621cf8201ea457dfafeda5c938f1663a0/LICENSE"
---
# huangruiteng/loopx
## Quick take
A provider-neutral state kernel that keeps long-horizon goals, gates, evidence, quotas, and handoffs durable across agent turns.
## Score
**91/100**
- **Harness relevance — 30/30:** Durable goals, gates, evidence, quotas, handoffs, recovery, and scheduling form a core long-horizon control plane.
- **Practical pattern value — 24/25:** Typed todos, claims, leases, review packets, bounded capabilities, and evidence writeback are directly reusable.
- **Evidence and maturity — 15/20:** The active project documents a usable 1.0, extensive contracts, quality gates, and public cases, while broader adoption is early.
- **Novelty — 14/15:** It unusually separates durable semantic control state from interchangeable execution harnesses and providers.
- **Risk-adjusted accessibility — 8/10:** Apache-2.0 licensing and local-first CLI paths aid review, with several integrations still optional or experimental.
## Why it matters
- Separates persistent control-plane truth from whichever harness executes the next bounded turn.
- Its evidence-backed review packets and explicit continuation decisions address long-running agent drift.
## Caveat
The project is recently created, advanced integrations remain optional or experimental, and its 200-hour cases measure elapsed project lifetime rather than continuous autonomy.
## Sources
[Repository](https://github.com/huangruiteng/loopx) · [README](https://github.com/huangruiteng/loopx/blob/f0375cc621cf8201ea457dfafeda5c938f1663a0/README.md) · [License](https://github.com/huangruiteng/loopx/blob/f0375cc621cf8201ea457dfafeda5c938f1663a0/LICENSE)
