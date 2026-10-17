---
title: msitarzewski/agency-agents
type: repo-intel
source: https://github.com/msitarzewski/agency-agents
category: agent-persona-library
status: deep-analyzed
usefulness_score: 68
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# msitarzewski/agency-agents

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `68/100` — Large persona/agent library; useful discovery only, but too broad/persona-heavy for SStack defaults.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Sample only if a specific specialist-agent pattern is needed; do not import personalities wholesale.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 15/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 17/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 14/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 14/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 8/15 | Unique pattern versus current stack. |
| **Total** | **68/100** | Large persona/agent library; useful discovery only, but too broad/persona-heavy for SStack defaults. |

## Verdict

Agency Agents is a giant specialist-agent/persona library. It may contain useful role patterns, but workflows that need reliability benefit more from procedures, evaluations, and operating semantics than from large collections of personalities. Reference-only.

## Workload fit

- Long-running Hermes work benefits from continuity across context limits, restarts, and multi-agent handoffs.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

A complete AI agency at your fingertips - From frontend wizards to Reddit community ninjas, from whimsy injectors to reality checkers. Each agent is a specialized expert with personality, processes, and proven deliverables.

## Evidence checked

- GitHub metadata: stars `107116`, forks `17665`, pushed `2026-06-02T23:06:50Z`, archived `False`.
- Topics: none.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, LICENSE, SECURITY.md, root-contents.json, recent-commits.json.

## Strengths

- MIT, security policy, broad categories, active maintenance, examples/scripts.
- Could provide inspiration for specialist roles if the operator designs agent teams.
- Deliverable-focused framing is better than generic prompts.

## Risks / caveats

- Massive persona surface creates prompt sprawl and style conflicts.
- High stars do not prove quality of individual agents.
- Personality-driven agents can reduce consistency unless tightly scoped.

## Integration ideas

- Prefer distilling useful control-plane semantics into existing agent procedures rather than adopting another runtime by default.
- Any tool that runs shells, agents, worktrees, desktop automation, SSH, provider accounts, or browser/OS control needs disposable-repo sandboxing and auth/filesystem review.
- Useful design concepts include a long-running work ledger and eval suite with identity, handoff, heartbeat and audit evidence.

## Alternatives / related repos

- [Agent control planes / dashboards comparison](../comparisons/agent-control-planes-dashboards.md)
- [gastownhall/gastown](gastownhall--gastown.md)
- [generalaction/emdash](generalaction--emdash.md)
- [saltbo/agent-kanban](saltbo--agent-kanban.md)
- [TinyAGI/tinyagi](TinyAGI--tinyagi.md)

## Review candidates and context

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
