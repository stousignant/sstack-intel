---
# catalog-derived-begin
title: "browser-use/bux"
type: "repo-intel"
status: "active"
active: true
source_identity: "browser-use/bux"
source: "https://github.com/browser-use/bux"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 71
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "f17c1b31d6688dd92e745ade650e00d46b4dc4da"
readme_path: "README.md"
readme_url: "https://github.com/browser-use/bux/blob/f17c1b31d6688dd92e745ade650e00d46b4dc4da/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/browser-use/bux/blob/f17c1b31d6688dd92e745ade650e00d46b4dc4da/LICENSE"
---
# browser-use/bux
## Quick take
Browser Use Box is a deployable pattern for a persistent Claude Code browser operator controlled through Telegram on a user-owned host.
## Score
**71/100**
- **Harness relevance — 25/30:** Packages Claude Code, persistent browser automation, messaging, and session context into an operating agent.
- **Practical pattern value — 18/25:** The service layout, Telegram interface, persistent browser, and editable CLAUDE.md provide reusable deployment patterns.
- **Evidence and maturity — 13/20:** The active MIT project has setup and architecture documentation but little README-level test or release evidence.
- **Novelty — 9/15:** Combines familiar VPS, Telegram, Claude Code, and browser components into a persistent operator.
- **Risk-adjusted accessibility — 6/10:** A single installer helps, but remote credentials, a VPS, browser access, and long-lived agent permissions raise risk.
## Why it matters
- It shows how to package browser state, agent context, messaging, and service supervision into a small always-on system.
- The editable session context and idempotent installer expose clear customization boundaries.
## Caveat
The README does not provide strong test evidence, and an always-on browser agent with Telegram and cloud credentials needs careful permission and secret isolation.
## Sources
[Repository](https://github.com/browser-use/bux) · [README](https://github.com/browser-use/bux/blob/f17c1b31d6688dd92e745ade650e00d46b4dc4da/README.md) · [License](https://github.com/browser-use/bux/blob/f17c1b31d6688dd92e745ade650e00d46b4dc4da/LICENSE)
