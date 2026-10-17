---
# catalog-derived-begin
title: "vercel-labs/zerolang"
type: "repo-intel"
status: "active"
active: true
source_identity: "vercel-labs/zerolang"
source: "https://github.com/vercel-labs/zerolang"
source_categories: [["Design Primitives","Tool Design"]]
source_occurrences: [["Design Primitives","Tool Design"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 62
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "eb2ed6c22fe3f6e3152efa0c0d05ffcf1ff4a2c7"
readme_path: "README.md"
readme_url: "https://github.com/vercel-labs/zerolang/blob/eb2ed6c22fe3f6e3152efa0c0d05ffcf1ff4a2c7/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/vercel-labs/zerolang/blob/eb2ed6c22fe3f6e3152efa0c0d05ffcf1ff4a2c7/LICENSE"
---
# vercel-labs/zerolang
## Quick take
Zerolang gives agents graph-level program handles and rejects stale or invalid semantic patches before writing state.
## Score
**62/100**
- **Harness relevance — 20/30:** Provides an agent-oriented semantic editing and validation substrate rather than a general-purpose harness.
- **Practical pattern value — 17/25:** Graph queries, checked patches, stale-state rejection, and explicit projection import/export are reusable patterns.
- **Evidence and maturity — 7/20:** The Apache-2.0 repository documents build and conformance commands, but explicitly describes the language as experimental.
- **Novelty — 15/15:** Making a semantic graph the program database for agent-authored checked edits is unusually differentiated.
- **Risk-adjusted accessibility — 3/10:** An installer exists, but the README warns of breaking changes, rough edges, and security issues.
## Why it matters
- Its query-and-patch interface replaces fragile line edits with compiler-checked structural changes.
- Explicit import and export prevent human-readable projections from silently diverging.
## Caveat
The README calls Zerolang experimental and warns to use isolated workspaces rather than production systems or sensitive data.
## Sources
[Repository](https://github.com/vercel-labs/zerolang) · [README](https://github.com/vercel-labs/zerolang/blob/eb2ed6c22fe3f6e3152efa0c0d05ffcf1ff4a2c7/README.md) · [License](https://github.com/vercel-labs/zerolang/blob/eb2ed6c22fe3f6e3152efa0c0d05ffcf1ff4a2c7/LICENSE)
