---
# catalog-derived-begin
title: "AMAP-ML/LongHorizon-Harness"
type: "repo-intel"
status: "active"
active: true
source_identity: "AMAP-ML/LongHorizon-Harness"
source: "https://github.com/AMAP-ML/LongHorizon-Harness"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 91
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "a1dd930614972b92361c1b9cd6aac441a6db5a65"
readme_path: "README.md"
readme_url: "https://github.com/AMAP-ML/LongHorizon-Harness/blob/a1dd930614972b92361c1b9cd6aac441a6db5a65/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/AMAP-ML/LongHorizon-Harness/blob/a1dd930614972b92361c1b9cd6aac441a6db5a65/LICENSE"
---
# AMAP-ML/LongHorizon-Harness
## Quick take
LongHorizon-Harness coordinates fresh-context agent rounds around durable state, independent audits, and recovery.
## Score
**91/100**
- **Harness relevance — 30/30:** Implements the core long-running agent loop: plan, act, independently verify, checkpoint, and recover.
- **Practical pattern value — 25/25:** Manager, executor, auditor, and verified-state boundaries are directly transferable harness patterns.
- **Evidence and maturity — 14/20:** The active MIT project documents releases, benchmarks, installation, and multiple agent adapters, but it is newly created.
- **Novelty — 15/15:** Fresh-context execution with durable verified checkpoints and independent auditing is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** A packaged CLI is available, but the README says current testing is primarily on macOS.
## Why it matters
- Separates state planning, execution, and ground-truth verification into explicit loop responsibilities.
- Carries only accepted checkpoints forward, preserving failure evidence for later rounds.
## Caveat
The project is young and the README says macOS is the currently tested platform, with Windows support not yet thoroughly tested.
## Sources
[Repository](https://github.com/AMAP-ML/LongHorizon-Harness) · [README](https://github.com/AMAP-ML/LongHorizon-Harness/blob/a1dd930614972b92361c1b9cd6aac441a6db5a65/README.md) · [License](https://github.com/AMAP-ML/LongHorizon-Harness/blob/a1dd930614972b92361c1b9cd6aac441a6db5a65/LICENSE)
