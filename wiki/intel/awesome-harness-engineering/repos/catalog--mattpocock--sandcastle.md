---
# catalog-derived-begin
title: "mattpocock/sandcastle"
type: "repo-intel"
status: "active"
active: true
source_identity: "mattpocock/sandcastle"
source: "https://github.com/mattpocock/sandcastle"
source_categories: [["Design Primitives","Task Runners & Orchestration"]]
source_occurrences: [["Design Primitives","Task Runners & Orchestration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 88
score_confidence: low
availability: available
last_reviewed: 2026-09-08
observed_revision: "e99f832f26dc9d245c019a9ddd19fa5dee792427"
readme_path: "README.md"
readme_url: "https://github.com/mattpocock/sandcastle/blob/e99f832f26dc9d245c019a9ddd19fa5dee792427/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/mattpocock/sandcastle/blob/e99f832f26dc9d245c019a9ddd19fa5dee792427/LICENSE"
---
# mattpocock/sandcastle
## Quick take
Sandcastle is a TypeScript orchestration harness for running coding agents in isolated branches and sandboxes.
## Score
**88/100**
- **Harness relevance — 30/30:** It directly orchestrates coding agents, branches, worktrees, sandboxes, review stages, and merged results.
- **Practical pattern value — 25/25:** Provider abstraction, isolated worktrees, implement-review pipelines, and lifecycle cleanup are directly transferable.
- **Evidence and maturity — 14/20:** An active, documented, packaged, MIT-licensed project meets the active documented-project anchor.
- **Novelty — 12/15:** Combining sandbox providers with branch and merge orchestration is a distinctive harness package.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and a TypeScript quickstart help, but container or cloud sandboxes and Git mutations require care.
## Why it matters
- Treats sandbox setup, agent execution, commits, review stages, and merge-back as one lifecycle.
- Supports Docker, Podman, Vercel, and custom providers behind a shared interface.
## Caveat
The captured README was truncated, and no agent run or branch-merging behavior was exercised in this catalog review.
## Sources
[Repository](https://github.com/mattpocock/sandcastle) · [README](https://github.com/mattpocock/sandcastle/blob/e99f832f26dc9d245c019a9ddd19fa5dee792427/README.md) · [License](https://github.com/mattpocock/sandcastle/blob/e99f832f26dc9d245c019a9ddd19fa5dee792427/LICENSE)
