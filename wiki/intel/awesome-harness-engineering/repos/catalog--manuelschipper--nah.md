---
# catalog-derived-begin
title: "manuelschipper/nah"
type: "repo-intel"
status: "active"
active: true
source_identity: "manuelschipper/nah"
source: "https://github.com/manuelschipper/nah"
source_categories: [["Design Primitives","Permissions & Authorization"]]
source_occurrences: [["Design Primitives","Permissions & Authorization"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 91
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "55b2b3421ea99105f38cca3950dde0aa209e9d8d"
readme_path: "README.md"
readme_url: "https://github.com/manuelschipper/nah/blob/55b2b3421ea99105f38cca3950dde0aa209e9d8d/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/manuelschipper/nah/blob/55b2b3421ea99105f38cca3950dde0aa209e9d8d/LICENSE"
---
# manuelschipper/nah
## Quick take
A deterministic pre-tool guard that blocks provable disasters while leaving all other decisions to the host runtime.
## Score
**91/100**
- **Harness relevance — 28/30:** Deterministic pre-tool guards and native denial adapters directly implement a critical harness authorization boundary.
- **Practical pattern value — 24/25:** Typed effects, block-or-delegate semantics, structural audit logs, and stricter-only extensions are directly reusable.
- **Evidence and maturity — 16/20:** The active Rust project documents 46 guards, tested examples, many runtime adapters, a threat model, and migration guidance.
- **Novelty — 14/15:** Deterministic effect analysis with tamper resistance and byte-pinned project guards is unusually well combined.
- **Risk-adjusted accessibility — 9/10:** MIT licensing, one binary, dry-run testing, and abstaining instead of approving make evaluation low risk.
## Why it matters
- Its block-or-delegate contract cannot widen existing permissions and composes cleanly with native approvals.
- Typed effect parsing and stricter-only extensions provide a concrete alternative to LLM safety judges.
## Caveat
Nah is not a sandbox, intentionally delegates ambiguous calls, and its README guard-coverage claims were not tested in this review.
## Sources
[Repository](https://github.com/manuelschipper/nah) · [README](https://github.com/manuelschipper/nah/blob/55b2b3421ea99105f38cca3950dde0aa209e9d8d/README.md) · [License](https://github.com/manuelschipper/nah/blob/55b2b3421ea99105f38cca3950dde0aa209e9d8d/LICENSE)
