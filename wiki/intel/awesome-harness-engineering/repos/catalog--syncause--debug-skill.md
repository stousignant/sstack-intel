---
# catalog-derived-begin
title: "Syncause/debug-skill"
type: "repo-intel"
status: "active"
active: true
source_identity: "Syncause/debug-skill"
source: "https://github.com/Syncause/debug-skill"
source_categories: [["Design Primitives","Debugging & Developer Experience"]]
source_occurrences: [["Design Primitives","Debugging & Developer Experience"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 60
score_confidence: low
availability: available
last_reviewed: 2026-09-08
observed_revision: "4a410212e8ff620cb3057d30ba90ca925843ed24"
readme_path: "README.md"
readme_url: "https://github.com/Syncause/debug-skill/blob/4a410212e8ff620cb3057d30ba90ca925843ed24/README.md"
metadata_observed: 2026-09-08
license_url: null
---
# Syncause/debug-skill
## Quick take
An agent skill that requires runtime traces and cited facts before proposing or reporting a bug fix.
## Score
**60/100**
- **Harness relevance — 20/30:** An evidence-gathering debugging skill and MCP server are substantial developer-experience harness components.
- **Practical pattern value — 17/25:** The reproduce, collect runtime facts, cite evidence, and report repair sequence is reusable.
- **Evidence and maturity — 10/20:** The README provides integrations and setup guidance, but no license evidence, tests, or releases were captured.
- **Novelty — 10/15:** Mandatory runtime-fact citation turns debugging from prompt advice into an evidence-constrained workflow.
- **Risk-adjusted accessibility — 3/10:** Installation is easy, but it automatically depends on an external MCP package and has no captured license.
## Why it matters
- Encodes a strong reproduce-to-evidence-to-repair workflow for coding agents.
- Provides setup paths across major coding-agent hosts through a shared MCP dependency.
## Caveat
No license file or test evidence was captured, and the claimed automatic tracing and zero-configuration behavior depends on a separate MCP package.
## Sources
[Repository](https://github.com/Syncause/debug-skill) · [README](https://github.com/Syncause/debug-skill/blob/4a410212e8ff620cb3057d30ba90ca925843ed24/README.md)
