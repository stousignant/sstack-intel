---
# catalog-derived-begin
title: "sierra-research/tau-bench"
type: "repo-intel"
status: "active"
active: true
source_identity: "sierra-research/tau-bench"
source: "https://github.com/sierra-research/tau-bench"
source_categories: [["Evals & Verification"]]
source_occurrences: [["Evals & Verification"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 78
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "59a200c6d575d595120f1cb70fea53cef0632f6b"
readme_path: "README.md"
readme_url: "https://github.com/sierra-research/tau-bench/blob/59a200c6d575d595120f1cb70fea53cef0632f6b/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/sierra-research/tau-bench/blob/59a200c6d575d595120f1cb70fea53cef0632f6b/LICENSE"
---
# sierra-research/tau-bench
## Quick take
τ-bench evaluates tool-using agents in simulated airline and retail conversations with domain policies and user models.
## Score
**78/100**
- **Harness relevance — 30/30:** Provides a core benchmark harness for tool-agent-user interaction in realistic policy-constrained domains.
- **Practical pattern value — 17/25:** User simulation, pass^k analysis, trajectory error attribution, and domain tools are reusable evaluation patterns.
- **Evidence and maturity — 14/20:** The MIT research repository includes code, data, results, and run commands, but labels its tasks outdated.
- **Novelty — 10/15:** Dynamic user-agent-tool evaluation and repeated-run reliability metrics remain distinctive benchmark elements.
- **Risk-adjusted accessibility — 7/10:** The code is installable, but experiments require several model APIs and the repository directs users to tau3-bench.
## Why it matters
- Measures repeated-run reliability rather than only single-run task success.
- Includes trajectory-oriented error attribution across agent, user, and environment faults.
## Caveat
The README explicitly says these tasks are outdated and directs current evaluation work to τ³-bench, which contains fixes and additional domains.
## Sources
[Repository](https://github.com/sierra-research/tau-bench) · [README](https://github.com/sierra-research/tau-bench/blob/59a200c6d575d595120f1cb70fea53cef0632f6b/README.md) · [License](https://github.com/sierra-research/tau-bench/blob/59a200c6d575d595120f1cb70fea53cef0632f6b/LICENSE)
