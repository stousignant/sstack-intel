---
# catalog-derived-begin
title: "stackoneHQ/defender"
type: "repo-intel"
status: "active"
active: true
source_identity: "stackoneHQ/defender"
source: "https://github.com/stackoneHQ/defender"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 85
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "b3d1c508057f4d54895122eebf813b7b8f8825d1"
readme_path: "README.md"
readme_url: "https://github.com/StackOneHQ/defender/blob/b3d1c508057f4d54895122eebf813b7b8f8825d1/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/StackOneHQ/defender/blob/b3d1c508057f4d54895122eebf813b7b8f8825d1/LICENSE"
---
# stackoneHQ/defender
## Quick take
A tiered prompt-injection guard for untrusted tool results, combining patterns, local ML, optional LLM review, and sanitization.
## Score
**85/100**
- **Harness relevance — 27/30:** Pre-model inspection and gating of untrusted tool results directly protects a critical agent-harness boundary.
- **Practical pattern value — 23/25:** Tiered detection, explicit degradation signals, fail-closed configuration, and sentence-level sanitization are reusable.
- **Evidence and maturity — 15/20:** The active Apache-licensed project documents APIs, thresholds, integration, bundled models, development, and testing.
- **Novelty — 12/15:** It combines synchronous patterns, local ML, optional consumer LLMs, and field-aware sanitization in one guard.
- **Risk-adjusted accessibility — 8/10:** A bundled CPU model and clear fallback state ease trials, but sanitization is best-effort and requires correct gating.
## Why it matters
- Makes degraded protection observable and offers a fail-closed mode when the ML tier cannot load.
- Places inspection between tool output and model context, where indirect prompt injection enters the loop.
## Caveat
Sanitization is explicitly best-effort, so consumers must honor the allow verdict and tune thresholds rather than treating cleaned text as safe.
## Sources
[Repository](https://github.com/stackoneHQ/defender) · [README](https://github.com/StackOneHQ/defender/blob/b3d1c508057f4d54895122eebf813b7b8f8825d1/README.md) · [License](https://github.com/StackOneHQ/defender/blob/b3d1c508057f4d54895122eebf813b7b8f8825d1/LICENSE)
