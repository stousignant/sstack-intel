---
title: pasky/chrome-cdp-skill
type: repo-intel
aliases:
  - chrome-cdp-skill
  - chrome-cdp
  - GitHub repo: pasky/chrome-cdp-skill
source: https://github.com/pasky/chrome-cdp-skill
category: browser-automation
topics: [github-repo, chrome, cdp, browser-automation, agent-skills, live-session]
status: deep-analyzed
usefulness_score: 86
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT
---

# pasky/chrome-cdp-skill

> Reference-stack evaluation as reviewed 2026-05-28; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `86/100` — unusually small, dependency-light live-Chrome control skill that solves a different problem than Playwright MCP: inspect and act on an already-open human browser session.
- **Recommendation:** `adopt-now` for a tightly permissioned sandbox / skill-port experiment; do not expose live logged-in Chrome broadly by default.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Port or sandbox the skill in a disposable scratch workspace or test profile, then verify whether live-tab inspection materially beats launching an isolated browser for debugging and “what am I looking at?” tasks.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 24/25 | Directly maps to Hermes/PAI desire for real-browser inspection, console/network checks, screenshots, and live page state. |
| Leverage | 22/25 | Useful for debugging logged-in web apps and pages already open in an operator workflow. |
| Reuse readiness | 18/20 | Tiny skill directory, Node 22+, no npm install, CLI commands are explicit and skill-friendly. |
| Maturity/trust | 10/15 | MIT and clear implementation, but young single-purpose project with limited release history. |
| Differentiation | 12/15 | Distinct from Playwright: persistent daemon per tab and live Chrome access instead of isolated browser automation. |

## Verdict

This is the sharpest “small tool” in the desktop/browser batch. It should not become a default permissionless superpower — live Chrome means logged-in accounts and sensitive state — but the design is exactly the kind of minimal CLI+skill Hermes can steal: explicit command surface, persistent per-tab CDP daemon, accessibility snapshots, HTML, screenshots, JS eval, network timing, and raw CDP passthrough.

## Workload fit

- It gives Hermes a path to inspect already-open pages, including logged-in GitHub/Gmail/internal pages, without relaunching a blank browser context; live-session access requires explicit, narrow permission.
- It matches the PAI/Hermes “verify in browser before guessing” loop: screenshot, accessibility snapshot, console/network timings, then code analysis.
- The skill itself is a good authoring reference: clear trigger language, prerequisite gate, command list, coordinate caveats, and safety tips.

## What it is

`chrome-cdp-skill` is a lightweight agent skill plus Node CLI that connects directly to a local Chrome/Chromium-family browser through the Chrome DevTools Protocol. It discovers tabs, opens a persistent daemon per target tab, and offers commands such as `list`, `shot`, `snap`, `html`, `eval`, `nav`, `net`, `click`, `type`, `loadall`, and `evalraw`.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: JavaScript, MIT, ~3.1k stars, ~192 forks, not archived, latest release `v1.0.2` on 2026-03-13, pushed 2026-03-18.
- README: live Chrome session access, no browser automation framework, no separate browser instance, Node 22+, remote debugging toggle, and command list.
- `skills/chrome-cdp/SKILL.md`: explicit skill description says use only on explicit user approval after being asked to inspect/debug/interact with an open Chrome page.
- `skills/chrome-cdp/scripts/cdp.mjs`: raw CDP over WebSocket, per-tab persistent daemon, runtime dir with restrictive umask on Unix, timeout constants, browser auto-detection, target-prefix checks.
- `package.json`: `pi-chrome-cdp` v1.0.2, MIT, files limited to `skills/` and README.

## Strengths

- Tiny, understandable implementation surface; no Puppeteer/Playwright dependency.
- Distinctive live-session access: useful exactly when re-login or clean browser state is the problem.
- Persistent daemon model avoids repeated Chrome debugging prompts and target enumeration problems.
- Skill text already encodes a useful consent boundary.
- Good fit as a Hermes skill/reference even if not installed wholesale.

## Risks / caveats

- Live logged-in Chrome access is a high-trust tool; it can read and act inside sensitive sessions.
- Requires Chrome remote debugging enabled, which itself broadens local attack surface.
- Node 22+ required; not as drop-in as Playwright MCP's Node 18 path.
- Young repo with limited maintenance history compared with Microsoft Playwright MCP.

## Integration ideas

- Create a Hermes-local `chrome-cdp` skill variant that is gated by explicit user request and never auto-runs on sensitive pages.
- Use for “inspect my current tab,” “debug this web app I have open,” or “check console/network on the page I am seeing” tasks.
- Keep isolated Playwright/browser tooling for repeatable automation; reserve CDP live-session access for stateful human-browser contexts.

## Alternatives / related repos

- [microsoft/playwright-mcp](microsoft--playwright-mcp.md) — official isolated browser automation MCP, safer default for repeatable web tasks.
- [bytedance/UI-TARS-desktop](bytedance--UI-TARS-desktop.md) — full multimodal GUI operator; broader but much heavier.
- [wonderwhy-er/DesktopCommanderMCP](wonderwhy-er--DesktopCommanderMCP.md) — local desktop/file/terminal MCP rather than browser-tab-specific CDP.

## Review guidance

- Review candidate: evaluate a consent-gated Hermes skill port for live Chrome inspection.
