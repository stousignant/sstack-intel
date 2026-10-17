---
# catalog-derived-begin
title: "cloudflare/computer"
type: "repo-intel"
status: "active"
active: true
source_identity: "cloudflare/computer"
source: "https://github.com/cloudflare/computer"
source_categories: [["Security, Sandbox & Permissions"]]
source_occurrences: [["Security, Sandbox & Permissions"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 77
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "e1cbbf5f82021a13d96dc5676f34098c2a472963"
readme_path: "README.md"
readme_url: "https://github.com/cloudflare/computer/blob/e1cbbf5f82021a13d96dc5676f34098c2a472963/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/cloudflare/computer/blob/e1cbbf5f82021a13d96dc5676f34098c2a472963/LICENSE"
---
# cloudflare/computer
## Quick take
A preview computer substrate that unifies durable workspace state with container, shell-isolate, and JavaScript execution backends.
## Score
**77/100**
- **Harness relevance — 24/30:** Supplies durable filesystem and execution backends that can serve as an agent harness's computer layer.
- **Practical pattern value — 22/25:** A single runtime interface over container, shell-isolate, and JavaScript-isolate backends is directly reusable architecture.
- **Evidence and maturity — 11/20:** MIT project includes examples and benchmark documentation, but the README explicitly labels it preview-only with unstable APIs.
- **Novelty — 14/15:** SQLite-authoritative state projected into multiple lazy execution backends is unusually differentiated.
- **Risk-adjusted accessibility — 6/10:** Examples aid evaluation, while Cloudflare-specific Durable Objects, Workers, FUSE, and preview status raise setup and change risk.
## Why it matters
- Its one authoritative filesystem with pluggable runtimes is a strong state/execution separation pattern.
- The MCP, long-context, artifact, and side-by-side runtime examples expose several harness integration shapes.
## Caveat
The project explicitly says it is preview-only, API-unstable, and unsuitable for production; the forward-looking specification may exceed current code.
## Sources
[Repository](https://github.com/cloudflare/computer) · [README](https://github.com/cloudflare/computer/blob/e1cbbf5f82021a13d96dc5676f34098c2a472963/README.md) · [License](https://github.com/cloudflare/computer/blob/e1cbbf5f82021a13d96dc5676f34098c2a472963/LICENSE)
