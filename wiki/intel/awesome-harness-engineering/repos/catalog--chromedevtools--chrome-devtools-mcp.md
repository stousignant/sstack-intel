---
# catalog-derived-begin
title: "ChromeDevTools/chrome-devtools-mcp"
type: "repo-intel"
status: "active"
active: true
source_identity: "ChromeDevTools/chrome-devtools-mcp"
source: "https://github.com/ChromeDevTools/chrome-devtools-mcp"
source_categories: [["Design Primitives","Skills & MCP"]]
source_occurrences: [["Design Primitives","Skills & MCP"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 82
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "6e53015a16423e3758a14d82c494cfcb4c07c3ea"
readme_path: "README.md"
readme_url: "https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/6e53015a16423e3758a14d82c494cfcb4c07c3ea/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/6e53015a16423e3758a14d82c494cfcb4c07c3ea/LICENSE"
---
# ChromeDevTools/chrome-devtools-mcp
## Quick take
An official MCP bridge that gives coding agents live Chrome inspection, automation, debugging, and performance tooling.
## Score
**82/100**
- **Harness relevance — 20/30:** The MCP server is a substantial browser-control and debugging component for coding-agent harnesses.
- **Practical pattern value — 25/25:** Live inspection, console analysis, performance traces, tool references, and browser-subagent integration are directly transferable capabilities.
- **Evidence and maturity — 20/20:** The project has official ChromeDevTools ownership, npm distribution, changelog and troubleshooting documentation, and active support.
- **Novelty — 10/15:** Exposing full Chrome DevTools debugging and performance insight through MCP is a distinctive integration.
- **Risk-adjusted accessibility — 7/10:** Apache-2.0 and npx configuration ease evaluation, but the server exposes browser data and enables usage statistics by default.
## Why it matters
- Provides a mature browser-tool surface and explicit browser-subagent integration guidance.
- Combines automation with console, source-map, and performance-trace evidence useful for verification loops.
## Caveat
It can inspect or modify sensitive browser data, supports only Chrome variants, and sends usage statistics unless explicitly disabled.
## Sources
[Repository](https://github.com/ChromeDevTools/chrome-devtools-mcp) · [README](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/6e53015a16423e3758a14d82c494cfcb4c07c3ea/README.md) · [License](https://github.com/ChromeDevTools/chrome-devtools-mcp/blob/6e53015a16423e3758a14d82c494cfcb4c07c3ea/LICENSE)
