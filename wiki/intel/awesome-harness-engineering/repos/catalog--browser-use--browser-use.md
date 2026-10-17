---
# catalog-derived-begin
title: "browser-use/browser-use"
type: "repo-intel"
status: "active"
active: true
source_identity: "browser-use/browser-use"
source: "https://github.com/browser-use/browser-use"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "2b1f9d377999a59fe7627c1a5aa88c12aa42e11f"
readme_path: "README.md"
readme_url: "https://github.com/browser-use/browser-use/blob/2b1f9d377999a59fe7627c1a5aa88c12aa42e11f/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/browser-use/browser-use/blob/2b1f9d377999a59fe7627c1a5aa88c12aa42e11f/LICENSE"
---
# browser-use/browser-use
## Quick take
A focused browser-agent harness with a usable local library, custom tool surface, authentication patterns, and an optional managed execution path.
## Score
**89/100**
- **Harness relevance — 27/30:** Provides the browser-control agent loop and tooling needed for a major class of harness tasks.
- **Practical pattern value — 23/25:** Custom actions, structured results, session reuse, authentication patterns, and local-versus-hosted boundaries are transferable.
- **Evidence and maturity — 19/20:** Active MIT project with documented installs, benchmark references, cloud operation, and a substantial integration surface.
- **Novelty — 12/15:** Combines LLM-directed browsing, reusable profiles, custom tools, and hosted browser infrastructure in a focused package.
- **Risk-adjusted accessibility — 8/10:** The local library is easy to install, but authenticated sites, CAPTCHAs, resource use, and remote services add operational risk.
## Why it matters
- It is a strong reference for separating an agent loop from browser/session infrastructure.
- The local-versus-cloud boundary makes scaling, stealth, profile reuse, and integration tradeoffs explicit.
## Caveat
README benchmark and production claims were not reproduced, and browser automation remains sensitive to site changes and credential handling.
## Sources
[Repository](https://github.com/browser-use/browser-use) · [README](https://github.com/browser-use/browser-use/blob/2b1f9d377999a59fe7627c1a5aa88c12aa42e11f/README.md) · [License](https://github.com/browser-use/browser-use/blob/2b1f9d377999a59fe7627c1a5aa88c12aa42e11f/LICENSE)
