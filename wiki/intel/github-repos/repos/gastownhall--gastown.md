---
title: gastownhall/gastown
type: repo-intel
source: https://github.com/gastownhall/gastown
category: agent-orchestration
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# gastownhall/gastown

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `88/100` — Strongest multi-agent workspace/ledger pattern in this batch; mine git-backed work state, mailboxes, identities, handoffs, and Beads-style ledgers.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `high`.
- **Review candidate:** Compare Gas Town semantics against Hermes delegation/cron/process state and claim/lease/result-ledger design.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 24/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 15/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 14/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 11/15 | Unique pattern versus current stack. |
| **Total** | **88/100** | Strongest multi-agent workspace/ledger pattern in this batch; mine git-backed work state, mailboxes, identities, handoffs, and Beads-style ledgers. |

## Verdict

Gas Town is the best pattern source in this batch for making long-running multi-agent work durable. It directly addresses context loss, coordination chaos, identities, handoffs, mailboxes, and persistent work state. Do not replace Hermes with it; distill its operational semantics into SStack/Hermes lanes.

## Reference-stack relevance

- The reference-stack goal is for long-running Hermes work to survive context limits, restarts, and multi-agent handoffs.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

Gas Town - multi-agent workspace manager

## Evidence checked

- GitHub metadata: stars `15712`, forks `1463`, pushed `2026-06-01T06:45:15Z`, archived `False`.
- Topics: none.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, LICENSE, SECURITY.md, Dockerfile, docker-compose.yml, AGENTS.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, active Go repo, security policy, Docker/e2e, docs, plugins, CLI, and explicit multi-agent orchestration architecture.
- README directly names common long-running-agent failure modes: restart/context loss, coordination, and missing persistent state.
- Git-backed hooks and Beads-style ledger map cleanly to durable Hermes batch runners.

## Risks / caveats

- Broad workspace manager adoption would duplicate Hermes/SStack decisions.
- Docker template for Claude Code and agent work requires credential/filesystem boundary audit.
- Likely complex; pattern extraction is safer than runtime adoption now.

## Integration ideas

- Prefer distilling control-plane semantics into Hermes/SStack rather than adopting another runtime by default.
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
