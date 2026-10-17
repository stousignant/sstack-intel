---
# catalog-derived-begin
title: "upstash/context7"
type: "repo-intel"
status: "active"
active: true
source_identity: "upstash/context7"
source: "https://github.com/upstash/context7"
source_categories: [["Design Primitives","Context Delivery & Compaction"]]
source_occurrences: [["Design Primitives","Context Delivery & Compaction"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 78
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "5a7039bf9d06ad131582f293a3d87a73c786e4d4"
readme_path: "README.md"
readme_url: "https://github.com/upstash/context7/blob/5a7039bf9d06ad131582f293a3d87a73c786e4d4/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/upstash/context7/blob/5a7039bf9d06ad131582f293a3d87a73c786e4d4/LICENSE"
---
# upstash/context7
## Quick take
A CLI and MCP context service that resolves libraries and injects current, version-specific documentation into coding-agent prompts.
## Score
**78/100**
- **Harness relevance — 20/30:** Version-specific documentation retrieval is a substantial context-delivery component for coding harnesses.
- **Practical pattern value — 23/25:** Library resolution, version targeting, CLI skills, and MCP retrieval are directly reusable context patterns.
- **Evidence and maturity — 18/20:** Active metadata, npm packages, extensive docs, and broad client support provide strong implementation evidence.
- **Novelty — 10/15:** Automatic version-aware source documentation injection is a distinctive context specialization.
- **Risk-adjusted accessibility — 7/10:** MIT licensing and one-command setup help, but API service reliance and private backend components limit inspectability.
## Why it matters
- Addresses stale API knowledge with an explicit resolve-then-query tool boundary.
- Supports both skill-driven CLI retrieval and native MCP integration across many clients.
## Caveat
The repository excludes the private API, parsing, and crawling backends, and community-contributed documentation is not guaranteed accurate.
## Sources
[Repository](https://github.com/upstash/context7) · [README](https://github.com/upstash/context7/blob/5a7039bf9d06ad131582f293a3d87a73c786e4d4/README.md) · [License](https://github.com/upstash/context7/blob/5a7039bf9d06ad131582f293a3d87a73c786e4d4/LICENSE)
