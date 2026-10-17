---
title: microsoft/playwright-mcp
type: repo-intel
aliases:
  - playwright-mcp
  - GitHub repo: microsoft/playwright-mcp
source: https://github.com/microsoft/playwright-mcp
category: browser-automation
topics: [github-repo, mcp, playwright, browser-automation, computer-use, agent-tools]
status: deep-analyzed
usefulness_score: 88
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: Apache-2.0
---

# microsoft/playwright-mcp

> Reference-stack fit as reviewed 2026-05-28; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `88/100` — official, very active, Apache-licensed MCP browser automation server with the right abstraction for structured web interaction; not a replacement for Hermes' built-in browser tools, but worth a bounded sandbox as an alternate MCP surface.
- **Recommendation:** `adopt-now` for a sandbox / tactical MCP experiment, not global always-on installation yet.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Test it on one real web QA/research workflow and compare token cost, determinism, screenshots, console/network access, and ergonomics against the current Hermes browser toolset.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 23/25 | MCP-native, local `npx` install path, works with Codex/Claude/Cursor-style clients, and maps to Hermes web QA/browser workflows. |
| Leverage | 22/25 | Could improve deterministic browser interaction, form workflows, and web-app verification without requiring vision. |
| Reuse readiness | 19/20 | Published as `@playwright/mcp`, one-command config, Dockerfile, TypeScript declarations, active release `v0.0.75`. |
| Maturity/trust | 14/15 | Microsoft-owned, Apache-2.0, Playwright-backed, active pushes/releases, tests listed in package scripts, MSRC security policy. |
| Differentiation | 10/15 | Strong standardization and ecosystem fit, but overlaps with Hermes' existing browser tools and Playwright CLI/skills. |

## Verdict

Playwright MCP is the strongest near-term browser-control candidate in this batch. The key distinction is not “more browser automation” — Hermes already has that — but an **official MCP contract around Playwright accessibility snapshots** that could become useful when Hermes needs a persistent browser context, client-portable setup, or standardized MCP server config. Keep it bounded: sandbox first, then only add it to Hermes if it beats the current built-in browser tools on a real task.

## Reference-stack relevance

- Browser/web-app QA is a recurring Hermes use case: inspect page state, click through flows, detect console/network failures, and verify UI behavior.
- It offers a standard MCP integration surface for other agents while preserving Playwright's robust browser substrate.
- The README explicitly contrasts MCP with CLI+SKILLS: MCP is better for persistent exploratory loops; CLI+skills may be better for high-throughput coding agents. That distinction maps well to Hermes' tool-budget trade-offs.

## What it is

`microsoft/playwright-mcp` is a Model Context Protocol server that exposes browser automation through Playwright. It lets LLMs interact with pages via structured accessibility snapshots instead of raw screenshots or vision-model interpretation.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: TypeScript, Apache-2.0, ~33.1k stars, ~2.7k forks, not archived, pushed 2026-05-28, latest release `v0.0.75` on 2026-05-07.
- README: states accessibility-tree automation, deterministic tool application, no vision model requirement, and `npx @playwright/mcp@latest` setup for many MCP clients including Codex.
- `package.json`: package `@playwright/mcp` v0.0.75, Node >=18, bin `playwright-mcp`, dependencies on Playwright 1.61 alpha packages, scripts for Playwright tests and Docker test path.
- `SECURITY.md`: Microsoft coordinated vulnerability disclosure / MSRC process.

## Strengths

- Official Microsoft / Playwright ecosystem project with permissive Apache license.
- Very low setup friction: `npx @playwright/mcp@latest` in MCP config.
- Avoids pixel/vision ambiguity for many pages by using accessibility snapshots.
- Works across many MCP clients, making it a useful compatibility baseline.
- Good fit for self-healing tests, exploratory web automation, and long-running browser workflows where state matters.

## Risks / caveats

- Tool schema and accessibility trees can be verbose; README itself warns CLI+SKILLS may be more token-efficient for coding agents.
- Browser automation can leak session state if pointed at logged-in or sensitive pages; use explicit task scope.
- It should not be installed as a broad always-on Hermes rule until compared with existing browser tools and token costs.
- Depending on alpha Playwright packages may mean fast-moving behavior; pin versions for any serious workflow.

## Integration ideas

- Add a sandbox MCP config for a separate Hermes/Codex profile and run one web QA task side-by-side with current browser tools.
- Use as the browser layer for deterministic verification tasks: open app, inspect accessibility tree, interact, check console/network, screenshot on failure.
- If useful, capture a Hermes skill that chooses between built-in browser tools, Playwright MCP, and direct Playwright CLI depending on task shape.

## Alternatives / related repos

- [pasky/chrome-cdp-skill](pasky--chrome-cdp-skill.md) — live logged-in Chrome session via CDP; more personal-stateful, higher privacy risk.
- [bytedance/UI-TARS-desktop](bytedance--UI-TARS-desktop.md) — multimodal GUI/desktop operator; heavier, wiki/vision/model-dependent.
- [wonderwhy-er/DesktopCommanderMCP](wonderwhy-er--DesktopCommanderMCP.md) — local filesystem/terminal MCP, not primarily browser automation.

## Review candidates and context

- Candidate: sandbox Playwright MCP against a real browser QA/research workflow before extending the browser tool surface.
