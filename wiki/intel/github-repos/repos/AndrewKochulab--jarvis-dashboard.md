---
title: AndrewKochulab/jarvis-dashboard
type: repo-intel
source: https://github.com/AndrewKochulab/jarvis-dashboard
category: obsidian-agent-dashboard
status: deep-analyzed
usefulness_score: 70
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# AndrewKochulab/jarvis-dashboard

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `70/100` — Obsidian/DataviewJS dashboard for Claude Code/fleet visibility; useful UI inspiration, lower maturity.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Mine dashboard modules/metrics ideas for second-brain/Hermes reporting; avoid copying DataviewJS wholesale into canonical vault.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 16/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 13/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 8/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 13/15 | Unique pattern versus current stack. |
| **Total** | **70/100** | Obsidian/DataviewJS dashboard for Claude Code/fleet visibility; useful UI inspiration, lower maturity. |

## Verdict

J.A.R.V.I.S. Dashboard is relevant to Obsidian-based workflows that need visibility into agent work. Its small, personal, dashboard-heavy scope makes it a UI/metric reference rather than a core dependency.

## Reference-stack relevance

- Long-running agent workflows need work state and handoffs to survive context limits and restarts; dashboard ideas are useful only when they improve that visibility.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

A modular, fully configurable DataviewJS dashboard for Obsidian — monitor Claude Code sessions in   real-time, manage AI agent fleets, track 30-day analytics, and boost productivity with focus timer,   quick capture, and more.

## Evidence checked

- GitHub metadata: stars `51`, forks `12`, pushed `2026-03-13T11:38:24Z`, archived `False`.
- Topics: ai-agents, claude-code, dashboard, dataviewjs, javascript, obsidian, obsidian-md, obsidian-plugin, pomodoro-timer, productivity, ios, ios-app, macos, macos-app.
- Inspected upstream repository: [source](https://github.com/AndrewKochulab/jarvis-dashboard); capture location omitted.
- Files fetched: README.md, LICENSE, root-contents.json, recent-commits.json.

## Strengths

- MIT, Obsidian/DataviewJS focus, Claude Code session monitoring, analytics, focus timer, multi-platform companion folders.
- Directly maps to second-brain dashboards and mobile visibility ideas.
- Shows what an agent fleet dashboard could look like inside Obsidian.

## Risks / caveats

- Low stars/small repo; maturity uncertain.
- DataviewJS dashboards can become brittle and hard to index with GBrain.
- May mix productivity widgets with operational telemetry.

## Integration ideas

- Prefer distilling control-plane semantics into Hermes/SStack rather than adopting another runtime by default.
- Any tool that runs shells, agents, worktrees, desktop automation, SSH, provider accounts, or browser/OS control needs disposable-repo sandboxing and auth/filesystem review.
- Useful concepts include a long-running work ledger and eval suite with identity, handoff, heartbeat and audit evidence.

## Alternatives / related repos

- [Agent control planes / dashboards comparison](../comparisons/agent-control-planes-dashboards.md)
- [gastownhall/gastown](gastownhall--gastown.md)
- [generalaction/emdash](generalaction--emdash.md)
- [saltbo/agent-kanban](saltbo--agent-kanban.md)
- [TinyAGI/tinyagi](TinyAGI--tinyagi.md)

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
