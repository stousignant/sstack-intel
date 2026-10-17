---
# catalog-derived-begin
title: "ruvnet/metaharness"
type: "repo-intel"
status: "active"
active: true
source_identity: "ruvnet/metaharness"
source: "https://github.com/ruvnet/metaharness"
source_categories: [["Reference Implementations","Generators & Meta-Harnesses"]]
source_occurrences: [["Reference Implementations","Generators & Meta-Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 89
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "d5833dc6512ac1adeeef91a331c29055cd8a4dbb"
readme_path: "README.md"
readme_url: "https://github.com/ruvnet/metaharness/blob/d5833dc6512ac1adeeef91a331c29055cd8a4dbb/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/ruvnet/metaharness/blob/d5833dc6512ac1adeeef91a331c29055cd8a4dbb/LICENSE"
---
# ruvnet/metaharness
## Quick take
A harness factory that scaffolds repo-aware agents, skills, MCP tools, memory, governance, provenance, and release controls for multiple hosts.
## Score
**89/100**
- **Harness relevance — 30/30:** A generator for repo-specific agent harnesses with skills, MCP, memory, governance, release gates, and optional evolution.
- **Practical pattern value — 23/25:** Repo-derived scaffolds, capability boundaries, signed provenance, sandboxed variation, host adapters, and promotion gates offer many transferable patterns.
- **Evidence and maturity — 14/20:** Active MIT monorepo documents packages and validation claims, but it is young and several ambitious components remain experimental or gated.
- **Novelty — 15/15:** A factory that emits branded harnesses and can govern measured self-variation is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** The npx entrypoint helps access, while the broad package surface, experimental options, and generated security policy demand careful review.
## Why it matters
- It treats the harness itself as a versioned product that can be generated, tested, promoted, and rolled back.
- Its fail-closed host boundaries and evidence-gated evolution are valuable patterns even without adopting the full generator.
## Caveat
The README covers a very broad and fast-moving feature set; several performance and autonomous-variation claims are explicitly experimental or blocked on future gates.
## Sources
[Repository](https://github.com/ruvnet/metaharness) · [README](https://github.com/ruvnet/metaharness/blob/d5833dc6512ac1adeeef91a331c29055cd8a4dbb/README.md) · [License](https://github.com/ruvnet/metaharness/blob/d5833dc6512ac1adeeef91a331c29055cd8a4dbb/LICENSE)
