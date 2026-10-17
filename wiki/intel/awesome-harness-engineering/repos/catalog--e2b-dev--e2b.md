---
# catalog-derived-begin
title: "e2b-dev/E2B"
type: "repo-intel"
status: "active"
active: true
source_identity: "e2b-dev/E2B"
source: "https://github.com/e2b-dev/E2B"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 78
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "b8b43232c885396a6c9d1ee9d1280325e5766536"
readme_path: "README.md"
readme_url: "https://github.com/e2b-dev/E2B/blob/b8b43232c885396a6c9d1ee9d1280325e5766536/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/e2b-dev/E2B/blob/b8b43232c885396a6c9d1ee9d1280325e5766536/LICENSE"
---
# e2b-dev/E2B
## Quick take
A concise SDK-backed sandbox layer for agent-generated commands, code interpretation, and desktop control.
## Score
**78/100**
- **Harness relevance — 20/30:** Secure code and desktop sandboxes are a substantial execution component within agent harnesses.
- **Practical pattern value — 24/25:** Small Python and JavaScript SDK surfaces make isolated command, code, and desktop execution directly transferable.
- **Evidence and maturity — 18/20:** The active project has packages, documentation, a cookbook, and self-hosting infrastructure under Apache-2.0.
- **Novelty — 9/15:** One service spans command, interpreter, and desktop sandboxes, though hosted isolation is not unique.
- **Risk-adjusted accessibility — 7/10:** SDK setup is simple, but hosted use needs an account and self-hosting requires cloud infrastructure.
## Why it matters
- Provides a small cross-language interface for disposable isolated execution.
- Offers both hosted sandboxes and a documented Terraform-based self-hosting path.
## Caveat
The README does not substantiate the security boundary in detail, and hosted evaluation requires an E2B API key.
## Sources
[Repository](https://github.com/e2b-dev/E2B) · [README](https://github.com/e2b-dev/E2B/blob/b8b43232c885396a6c9d1ee9d1280325e5766536/README.md) · [License](https://github.com/e2b-dev/E2B/blob/b8b43232c885396a6c9d1ee9d1280325e5766536/LICENSE)
