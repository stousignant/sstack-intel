---
# catalog-derived-begin
title: "browser-use/browser-harness"
type: "repo-intel"
status: "active"
active: true
source_identity: "browser-use/browser-harness"
source: "https://github.com/browser-use/browser-harness"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 86
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "afbcc381b963040c19627d788e40c7e7663171ee"
readme_path: "README.md"
readme_url: "https://github.com/browser-use/browser-harness/blob/afbcc381b963040c19627d788e40c7e7663171ee/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/browser-use/browser-harness/blob/afbcc381b963040c19627d788e40c7e7663171ee/LICENSE"
---
# browser-use/browser-harness
## Quick take
A focused browser-agent harness that lets an agent extend its own helper layer over one CDP connection.
## Score
**86/100**
- **Harness relevance — 28/30:** Direct CDP browser control, helper execution, and MCP exposure form a browser-agent harness.
- **Practical pattern value — 23/25:** The editable helper workspace and single browser-control layer are highly reusable patterns.
- **Evidence and maturity — 14/20:** The project is active and documented with install guidance, but the README gives limited release or test evidence.
- **Novelty — 13/15:** Agents can add missing reusable helpers while the protected harness core remains fixed.
- **Risk-adjusted accessibility — 8/10:** MIT and a concise setup path help, though remote debugging and a real browser expand the trust boundary.
## Why it matters
- Separates a protected browser-control core from an editable workspace of reusable helpers.
- Exposes the same controls through MCP instead of requiring another automation layer.
## Caveat
Connecting an agent to a logged-in real browser creates a sensitive execution surface that README-level review cannot validate.
## Sources
[Repository](https://github.com/browser-use/browser-harness) · [README](https://github.com/browser-use/browser-harness/blob/afbcc381b963040c19627d788e40c7e7663171ee/README.md) · [License](https://github.com/browser-use/browser-harness/blob/afbcc381b963040c19627d788e40c7e7663171ee/LICENSE)
