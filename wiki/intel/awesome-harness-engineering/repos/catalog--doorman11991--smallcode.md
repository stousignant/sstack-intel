---
# catalog-derived-begin
title: "Doorman11991/smallcode"
type: "repo-intel"
status: "active"
active: true
source_identity: "Doorman11991/smallcode"
source: "https://github.com/Doorman11991/smallcode"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 86
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "624970cce81657fd2751ee7f11ba85f35f2bb5c3"
readme_path: "README.md"
readme_url: "https://github.com/Doorman11991/smallcode/blob/624970cce81657fd2751ee7f11ba85f35f2bb5c3/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/Doorman11991/smallcode/blob/624970cce81657fd2751ee7f11ba85f35f2bb5c3/LICENSE"
---
# Doorman11991/smallcode
## Quick take
SmallCode redesigns a terminal coding harness around the context and tool-use limits of 8B–35B local models.
## Score
**86/100**
- **Harness relevance — 30/30:** Implements a complete terminal coding-agent loop optimized for small local models.
- **Practical pattern value — 25/25:** Budgeted context, forgiving tool parsing, decomposed TODOs, routed schemas, and patch editing are directly reusable.
- **Evidence and maturity — 14/20:** The active MIT project documents npm and binary installs, architecture, fallbacks, and benchmark claims.
- **Novelty — 10/15:** Adapting the full loop to unreliable tool use and small context windows is a distinctive combination.
- **Risk-adjusted accessibility — 7/10:** It is easy to install and can run locally, but native optional dependencies and model quality affect capabilities.
## Why it matters
- Uses context caps, history compression, routed tool schemas, and search-and-replace editing to reduce model load.
- Includes verification and decomposition mechanisms rather than assuming frontier-model reliability.
## Caveat
The README warns that models at or below 4B struggle with multi-step tool use, and optional native dependencies may fall back to simpler JSON memory.
## Sources
[Repository](https://github.com/Doorman11991/smallcode) · [README](https://github.com/Doorman11991/smallcode/blob/624970cce81657fd2751ee7f11ba85f35f2bb5c3/README.md) · [License](https://github.com/Doorman11991/smallcode/blob/624970cce81657fd2751ee7f11ba85f35f2bb5c3/LICENSE)
