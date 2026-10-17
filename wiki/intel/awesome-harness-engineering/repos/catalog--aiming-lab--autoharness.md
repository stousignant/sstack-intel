---
# catalog-derived-begin
title: "aiming-lab/AutoHarness"
type: "repo-intel"
status: "active"
active: true
source_identity: "aiming-lab/AutoHarness"
source: "https://github.com/aiming-lab/AutoHarness"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 86
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "3561e468f9ca9f9bf282512e695bd32e4e90fef4"
readme_path: "README.md"
readme_url: "https://github.com/aiming-lab/AutoHarness/blob/3561e468f9ca9f9bf282512e695bd32e4e90fef4/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/aiming-lab/AutoHarness/blob/3561e468f9ca9f9bf282512e695bd32e4e90fef4/LICENSE"
---
# aiming-lab/AutoHarness
## Quick take
AutoHarness is a young but broad governance wrapper and agent loop spanning permissions, context budgets, audit trails, and multi-agent profiles.
## Score
**86/100**
- **Harness relevance — 30/30:** Implements a full agent loop and governance pipeline around model calls and tool execution.
- **Practical pattern value — 22/25:** Constitutions, risk classification, permissions, output rails, budgets, audit logs, and profiles are transferable.
- **Evidence and maturity — 13/20:** README documents a v0.1.0 release and 958 claimed tests, but the project is very new.
- **Novelty — 12/15:** Unifies governance, context, cost, persistence, and multi-agent controls behind a client wrapper.
- **Risk-adjusted accessibility — 9/10:** MIT licensing and a two-line Python wrapper make initial evaluation straightforward.
## Why it matters
- The staged governance pipeline is a compact reference for intercepting tool calls before and after execution.
- Its constitution and profile approach makes policy explicit rather than burying it in prompts.
## Caveat
The evidence is README-level and the repository was created shortly before review, so its large test claim and enhanced-mode breadth do not establish field maturity.
## Sources
[Repository](https://github.com/aiming-lab/AutoHarness) · [README](https://github.com/aiming-lab/AutoHarness/blob/3561e468f9ca9f9bf282512e695bd32e4e90fef4/README.md) · [License](https://github.com/aiming-lab/AutoHarness/blob/3561e468f9ca9f9bf282512e695bd32e4e90fef4/LICENSE)
