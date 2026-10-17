---
# catalog-derived-begin
title: "HKUDS/OpenHarness"
type: "repo-intel"
status: "active"
active: true
source_identity: "HKUDS/OpenHarness"
source: "https://github.com/HKUDS/OpenHarness"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 91
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "9b2efd795c6aa09f88b0c257d269a9e518da6ae7"
readme_path: "README.md"
readme_url: "https://github.com/HKUDS/OpenHarness/blob/9b2efd795c6aa09f88b0c257d269a9e518da6ae7/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/HKUDS/OpenHarness/blob/9b2efd795c6aa09f88b0c257d269a9e518da6ae7/LICENSE"
---
# HKUDS/OpenHarness
## Quick take
A complete, inspectable harness implementation spanning tools, skills, memory, permissions, providers, and multi-agent work.
## Score
**91/100**
- **Harness relevance — 30/30:** Agent loop, tools, permissions, memory, plugins, context, and subagents make this a complete harness.
- **Practical pattern value — 24/25:** Its compact subsystem layout, dry-run readiness check, and permission pipeline are directly transferable.
- **Evidence and maturity — 17/20:** The README documents releases, CI, 114 unit or integration tests, multiple E2E suites, and MIT licensing.
- **Novelty — 11/15:** It combines Claude-style skills and plugins with provider profiles, multi-agent work, and a personal-agent gateway.
- **Risk-adjusted accessibility — 9/10:** MIT, pip installation, and guided setup help, though running broad tools still requires careful permissions.
## Why it matters
- Provides a concrete subsystem map and execution loop for a general-purpose agent runtime.
- Its static dry-run resolves auth, skills, tools, and MCP readiness without executing them.
## Caveat
The broad execution and messaging surface was reviewed only through README claims; auto mode deliberately allows unrestricted actions.
## Sources
[Repository](https://github.com/HKUDS/OpenHarness) · [README](https://github.com/HKUDS/OpenHarness/blob/9b2efd795c6aa09f88b0c257d269a9e518da6ae7/README.md) · [License](https://github.com/HKUDS/OpenHarness/blob/9b2efd795c6aa09f88b0c257d269a9e518da6ae7/LICENSE)
