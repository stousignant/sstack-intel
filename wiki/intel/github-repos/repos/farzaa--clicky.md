---
title: farzaa/clicky
type: repo-intel
source: https://github.com/farzaa/clicky
category: desktop-ai-companion
status: deep-analyzed
usefulness_score: 72
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# farzaa/clicky

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `72/100` — Interesting macOS screen-aware AI teacher/companion pattern; repo is open-source legacy while new work is private.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Use as UX inspiration for screen-aware coaching only; do not treat as maintained stack candidate.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 16/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 18/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 12/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 12/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 14/15 | Unique pattern versus current stack. |
| **Total** | **72/100** | Interesting macOS screen-aware AI teacher/companion pattern; repo is open-source legacy while new work is private. |

## Verdict

Clicky is a charming and useful UX reference: an AI buddy that can see your screen, talk, and point. But the README says new work is private, and this open repo is the old codebase. Preserve the pattern, not the product.

## Reference-stack relevance

- Long-running Hermes workflows need work state and handoffs to survive context limits and restarts; companion UX is useful only when it improves that continuity.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

Interesting macOS screen-aware AI teacher/companion pattern; repo is open-source legacy while new work is private.

## Evidence checked

- GitHub metadata: stars `6420`, forks `1220`, pushed `2026-04-28T19:33:33Z`, archived `False`.
- Topics: none.
- Local evidence cache: a disposable source-inspection workspace.
- Files fetched: README.md, LICENSE, AGENTS.md, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, Xcode project, tests, worker, AGENTS/CLAUDE instructions, screen-aware teaching UX.
- Good inspiration for “AI beside the cursor” workflows.
- Open code can show how the companion UX was built.

## Risks / caveats

- New Clicky development is private; public repo may go stale.
- macOS app/screen access has privacy and permission risks.
- Earlier commit removed a hardcoded Anthropic API key, so security hygiene needs caution.

## Integration ideas

- Prefer distilling control-plane semantics into Hermes/SStack rather than adopting another runtime by default.
- Any tool that runs shells, agents, worktrees, desktop automation, SSH, provider accounts, or browser/OS control needs disposable-repo sandboxing and auth/filesystem review.
- Useful concepts include long-running work ledgers and eval suites with identity, handoff, heartbeat and audit evidence.

## Alternatives / related repos

- [Agent control planes / dashboards comparison](../comparisons/agent-control-planes-dashboards.md)
- [gastownhall/gastown](gastownhall--gastown.md)
- [generalaction/emdash](generalaction--emdash.md)
- [saltbo/agent-kanban](saltbo--agent-kanban.md)
- [TinyAGI/tinyagi](TinyAGI--tinyagi.md)

## Review candidates and context

- Candidates above remain non-binding; implementation needs a separately scoped evaluation.
