---
# catalog-derived-begin
title: "vercel-labs/deepsec"
type: "repo-intel"
status: "active"
active: true
source_identity: "vercel-labs/deepsec"
source: "https://github.com/vercel-labs/deepsec"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 79
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "23a69227e3380e6b44a7ebd93c52e023c59f17c3"
readme_path: "README.md"
readme_url: "https://github.com/vercel-labs/deepsec/blob/23a69227e3380e6b44a7ebd93c52e023c59f17c3/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/vercel-labs/deepsec/blob/23a69227e3380e6b44a7ebd93c52e023c59f17c3/LICENSE"
---
# vercel-labs/deepsec
## Quick take
Deepsec is a resumable coding-agent security harness for distributed repository analysis and finding revalidation.
## Score
**79/100**
- **Harness relevance — 30/30:** Deepsec is a core coding-agent harness specialized for repository security analysis and finding revalidation.
- **Practical pattern value — 20/25:** Resumable analysis, finding revalidation, persistent state, and distributed workers provide reusable patterns.
- **Evidence and maturity — 14/20:** The active project has workflow documentation, sandbox guidance, model comparisons, and Apache-2.0 licensing.
- **Novelty — 12/15:** Long-running agentic security analysis with resumability and a separate revalidation phase is distinctive.
- **Risk-adjusted accessibility — 3/10:** The README warns scans can cost thousands of dollars and unsandboxed agents expand code and credential exposure.
## Why it matters
- Persists analysis state so interrupted or budget-limited scans can resume rather than restart.
- Separates broad vulnerability discovery from a later revalidation pass intended to reduce false positives.
## Caveat
The README warns large scans can be extremely costly, and meaningful use exposes code and model credentials unless carefully sandboxed.
## Sources
[Repository](https://github.com/vercel-labs/deepsec) · [README](https://github.com/vercel-labs/deepsec/blob/23a69227e3380e6b44a7ebd93c52e023c59f17c3/README.md) · [License](https://github.com/vercel-labs/deepsec/blob/23a69227e3380e6b44a7ebd93c52e023c59f17c3/LICENSE)
