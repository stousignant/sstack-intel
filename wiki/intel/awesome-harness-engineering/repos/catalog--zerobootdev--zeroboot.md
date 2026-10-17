---
# catalog-derived-begin
title: "zerobootdev/zeroboot"
type: "repo-intel"
status: "active"
active: true
source_identity: "zerobootdev/zeroboot"
source: "https://github.com/zerobootdev/zeroboot"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 77
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "87ca9c018a9c2a343ece768eec508e16497753f9"
readme_path: "README.md"
readme_url: "https://github.com/zerobootdev/zeroboot/blob/87ca9c018a9c2a343ece768eec508e16497753f9/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/zerobootdev/zeroboot/blob/87ca9c018a9c2a343ece768eec508e16497753f9/LICENSE"
---
# zerobootdev/zeroboot
## Quick take
A working prototype that forks prewarmed Firecracker snapshots into sub-millisecond, hardware-isolated agent sandboxes.
## Score
**77/100**
- **Harness relevance — 27/30:** Fast hardware-isolated execution environments directly address the sandbox boundary for code-running agents.
- **Practical pattern value — 21/25:** Snapshot templates and copy-on-write KVM forks are a transferable pattern for low-latency disposable sandboxes.
- **Evidence and maturity — 9/20:** The Apache-licensed project provides a working prototype, API, SDKs, docs, benchmarks, and candid limitations.
- **Novelty — 15/15:** Sub-millisecond Firecracker VM cloning with very low incremental memory is unusually differentiated.
- **Risk-adjusted accessibility — 5/10:** A live API and permissive license help, but self-hosting needs Linux KVM and the prototype has material isolation caveats.
## Why it matters
- Targets the latency and memory costs that make per-action VM isolation difficult.
- Its snapshot-and-copy-on-write design is a distinctive disposable-execution pattern.
## Caveat
The project is not production-hardened; forks can share userspace PRNG state, support one vCPU, lack networking, and require full template resnapshots.
## Sources
[Repository](https://github.com/zerobootdev/zeroboot) · [README](https://github.com/zerobootdev/zeroboot/blob/87ca9c018a9c2a343ece768eec508e16497753f9/README.md) · [License](https://github.com/zerobootdev/zeroboot/blob/87ca9c018a9c2a343ece768eec508e16497753f9/LICENSE)
