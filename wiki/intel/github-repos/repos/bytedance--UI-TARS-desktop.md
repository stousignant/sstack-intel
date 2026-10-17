---
title: bytedance/UI-TARS-desktop
type: repo-intel
aliases:
  - UI-TARS-desktop
  - Agent TARS
  - UI-TARS Desktop
  - GitHub repo: bytedance/UI-TARS-desktop
source: https://github.com/bytedance/UI-TARS-desktop
category: computer-use
topics: [github-repo, multimodal-agent, computer-use, gui-agent, browser-use, mcp, desktop-control]
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: Apache-2.0
---

# bytedance/UI-TARS-desktop

> Opinionated reference-stack evaluation, reviewed 2026-05-28. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `80/100` — strongest open-source GUI/vision-agent reference in this batch, but too heavy and model-/desktop-permission-dependent to adopt as a default Hermes runtime component.
- **Recommendation:** `distill-pattern`; watch for GUI-agent patterns and sandbox only if a real visual-computer-use task appears.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Extract the operator abstraction, event-stream/debugging UX, sandbox/runtime settings, and human-like GUI loop patterns into Hermes/PAI design notes; avoid adding another daily agent runtime.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 18/25 | Relevant to PAI/Hermes visual computer-use ambitions, but heavier than current local text/browser/tool workflows. |
| Leverage | 20/25 | Could unlock tasks that APIs/DOM tools cannot, especially visual apps and desktop workflows. |
| Reuse readiness | 14/20 | CLI, web UI, desktop app, SDK, Homebrew cask, docs; but model service config and desktop permissions raise setup cost. |
| Maturity/trust | 14/15 | ByteDance-backed, Apache-2.0, large active repo, tests/lint/secretlint infrastructure. |
| Differentiation | 14/15 | Distinct multimodal GUI-agent stack with operator abstractions and event streaming. |

## Verdict

UI-TARS/Agent TARS is not the next thing to wire into Hermes, but it is the best reference here for **visual computer-use architecture**. The immediate Hermes path should stay narrower: Playwright for DOM-accessible web, Chrome CDP for live browser inspection, native local tools for files/shell. UI-TARS becomes relevant when the task requires interacting with arbitrary desktop or browser UI where DOM/API access is unavailable.

## Reference-stack relevance

- It shows what a full multimodal GUI agent stack looks like: CLI, web UI, desktop app, SDK, local/remote operators, MCP integration, and event-stream debugging.
- It maps to future PAI/Hermes capabilities around “operate the computer like a human,” but without forcing that heavy path into today's workflow.
- The operator abstraction is useful even if Hermes never runs UI-TARS directly.

## What it is

`UI-TARS-desktop` is ByteDance's open-source multimodal AI agent stack. It currently ships Agent TARS — a CLI/Web UI multimodal agent for terminal, browser, and product workflows — plus UI-TARS Desktop, a native GUI agent app based on the UI-TARS model and local/remote computer/browser operators.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: TypeScript, Apache-2.0, ~35.6k stars, ~3.6k forks, not archived, pushed 2026-05-18, latest release `v0.3.0` on 2025-11-04.
- README: Agent TARS + UI-TARS Desktop split, CLI/Web UI, GUI Agent/Vision, MCP tools, local/remote computer/browser operators, Event Stream Viewer and runtime settings in v0.3.0 news.
- `package.json`: pnpm monorepo, Node >=20, scripts for UI-TARS desktop dev, tests, lint, coverage, secretlint, changesets, turbo.
- `docs/quick-start.md`: desktop app permissions, single-monitor caveat, remote operator discontinuation notice, local operator setup requiring UI-TARS model service config.
- `docs/sdk.md`: `@ui-tars/sdk` GUIAgent / Operator abstraction with screenshot → model prediction → execute loop; supports NutJS, web, and mobile operator shapes.

## Strengths

- Broadest visual computer-use coverage in the batch.
- Clear operator abstraction that can be learned from independently of the app.
- Event-stream/debugging and runtime-settings ideas are directly relevant to transparent agent control.
- Apache-2.0 and serious monorepo hygiene: tests, linting, secretlint, workspaces.
- Large adoption signal and active development.

## Risks / caveats

- Heavy desktop permissions: accessibility, screen recording, browser/desktop control.
- Local operator depends on model service configuration; not a trivial no-credential smoke test.
- Remote operator service was scheduled for discontinuation in the docs, so cloud/free paths should not be trusted as stable.
- Single-monitor caveat in quickstart; not robust enough to treat as dependable daily runtime without testing.
- Full visual agents are slower/riskier than DOM/API/CLI tools when those structured interfaces exist.

## Integration ideas

- Distill the operator interface into a Hermes design note: screenshot/read state, model/action prediction, execute, stream events, human interrupt.
- Use as a benchmark when evaluating future visual-computer-use features in Hermes or PAI.
- Only sandbox on a non-sensitive machine/profile with explicit goal and permissions; do not point it at personal accounts by default.

## Alternatives / related repos

- [microsoft/playwright-mcp](microsoft--playwright-mcp.md) — better first choice for structured web pages.
- [pasky/chrome-cdp-skill](pasky--chrome-cdp-skill.md) — better first choice for current logged-in browser tab inspection.
- [agent0ai/agent-zero](agent0ai--agent-zero.md) — broader visual coworking/runtime reference already analyzed.
- [OpenHands/OpenHands](OpenHands--OpenHands.md) — coding-agent runtime benchmark, not visual GUI-first.

## Review candidates and context

- Non-binding candidate: distill GUI-agent operator/event-stream patterns into Hermes/PAI design notes; sandbox only when a real visual desktop task appears.
