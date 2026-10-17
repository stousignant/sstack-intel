---
title: agno-agi/dash
type: repo-intel
source: https://github.com/agno-agi/dash
category: self-learning-data-agent
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: Apache-2.0
---

# agno-agi/dash

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `80/100` — Useful self-learning data-agent reference with six context layers, evals, docs, Docker, and terminal/Slack/UI surfaces.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `high`.
- **Review candidate:** Mine its context-layer/evals/knowledge-loading patterns for GBrain/briefing/data-agent workflows; do not adopt as separate data-agent runtime yet.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 22/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 15/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 13/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 9/15 | Unique pattern versus current stack. |
| **Total** | **80/100** | Useful self-learning data-agent reference with six context layers, evals, docs, Docker, and terminal/Slack/UI surfaces. |

## Verdict

Dash is a serious data-agent example rather than just a dashboard: it has context layering, evals, Docker, docs, sample data, and multiple chat surfaces. For data-agent workloads, its grounding and evaluation patterns are worth comparing; where GBrain already owns indexing/query, Dash should not create a competing canonical knowledge layer.

## Workload fit

- Long-running agent work needs continuity across context limits, restarts, and multi-agent handoffs.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

A self-learning data agent built with systems engineering principles. It grounds answers in 6 layers of context and improves with every query.

## Evidence checked

- GitHub metadata: stars `2076`, forks `234`, pushed `2026-04-08T11:50:51Z`, archived `False`.
- Topics: none.
- Local evidence cache: a disposable source-inspection workspace.
- Files fetched: README.md, LICENSE, pyproject.toml, requirements.txt, Dockerfile, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- Apache-2.0, Docker/compose, docs, evals, knowledge folder, pyproject/requirements, Slack/terminal/AgentOS surfaces.
- Self-learning and context-layer framing maps to GBrain/briefing quality improvements.
- Concrete enough to inspect beyond README claims.

## Risks / caveats

- Requires OpenAI key and service stack to run.
- Could duplicate GBrain/second-brain data-agent responsibilities.
- Agno/AgentOS dependency may add platform assumptions.

## Integration ideas

- Prefer distilling control-plane semantics into existing agent procedures when they solve a demonstrated need, rather than adopting another runtime by default.
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
