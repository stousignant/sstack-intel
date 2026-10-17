---
title: peters/horizon
type: repo-intel
source: https://github.com/peters/horizon
category: terminal-session-control
status: deep-analyzed
usefulness_score: 76
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# peters/horizon

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `76/100` — Promising terminal canvas for many agent sessions; useful UX reference for supervising Claude/Codex/OpenCode lanes.
- **Recommendation:** `watch`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Watch as a terminal/session cockpit; sandbox only if Hermes needs a visual multi-session board outside Discord/TUI.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 19/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 14/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 13/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 10/15 | Unique pattern versus current stack. |
| **Total** | **76/100** | Promising terminal canvas for many agent sessions; useful UX reference for supervising Claude/Codex/OpenCode lanes. |

## Verdict

Horizon is a UI/control-surface candidate, not agent logic. Its infinite terminal canvas could help supervise many agent sessions, but Hermes already has process tracking, Discord delivery, and cron. Watch it as a UX benchmark.

## Reference-stack relevance

- Long-running Hermes workflows need work state and handoffs to survive context limits and restarts.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

GPU-accelerated terminal board that puts all your sessions on an infinite canvas

## Evidence checked

- GitHub metadata: stars `625`, forks `24`, pushed `2026-06-01T08:40:46Z`, archived `False`.
- Topics: ai-agents, claude, codex, developer-tools, egui, gpu, rust, terminal, terminal-emulator, opencode, gemeni-cli, kilocode-cli.
- Upstream evidence: https://github.com/peters/horizon; the following fetched files were inspected at review time.
- Files fetched: README.md, LICENSE, AGENTS.md, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, Rust, CI/release badges, cross-platform claims, AGENTS/CLAUDE docs, agent panel integration.
- Directly targets many terminal/agent sessions on one canvas.
- Could improve human supervision of long-running agents.

## Risks / caveats

- GPU terminal UI is a nice-to-have, not core stack leverage.
- Needs real local smoke test before any adoption claim.
- May duplicate tmux/TUI/Discord surfaces.

## Integration ideas

- Prefer distilling control-plane semantics into Hermes/SStack rather than adopting another runtime by default.
- Any tool that runs shells, agents, worktrees, desktop automation, SSH, provider accounts, or browser/OS control needs disposable-repo sandboxing and auth/filesystem review.
- Reuse the identity, handoff, heartbeat and audit concepts in an existing long-running-work ledger and evaluation suite, not a parallel tracker.

## Alternatives / related repos

- [Agent control planes / dashboards comparison](../comparisons/agent-control-planes-dashboards.md)
- [gastownhall/gastown](gastownhall--gastown.md)
- [generalaction/emdash](generalaction--emdash.md)
- [saltbo/agent-kanban](saltbo--agent-kanban.md)
- [TinyAGI/tinyagi](TinyAGI--tinyagi.md)

## Review guidance

- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
