---
title: saltbo/agent-kanban
type: repo-intel
source: https://github.com/saltbo/agent-kanban
category: agent-task-board
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: FSL-1.1-ALv2
---

# saltbo/agent-kanban

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — Best task-board/control semantics: agent identities, skills, teams, self-assignment, CI coverage, and runtime circuit-breaker hints.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `high`.
- **Review candidate:** Distill agent identity/load/skill/team/board semantics into Hermes long-running task ledger; avoid direct adoption because of FSL and hosted/Cloudflare shape.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 22/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 12/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 14/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 11/15 | Unique pattern versus current stack. |
| **Total** | **82/100** | Best task-board/control semantics: agent identities, skills, teams, self-assignment, CI coverage, and runtime circuit-breaker hints. |

## Verdict

Agent Kanban is close to what Hermes long-running work needs conceptually: mission control, agent identities, skills, load, self-organization, and task state. The Functional Source License and Cloudflare app shape argue against direct adoption, but the semantics are worth mining.

## Reference-stack relevance

- The target requirement is long-running Hermes work that survives context limits, restarts, and multi-agent handoffs.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

An agent-first task board, Mission control for your AI workforce.

## Evidence checked

- GitHub metadata: stars `322`, forks `26`, pushed `2026-05-23T13:31:04Z`, archived `False`.
- Topics: agent-orchestration, ai-agents, ai-coding-agent, claude-code, cloudflare-pages, codex, developer-tools, ed25519, gemini-cli, kanban, multi-agent, task-management.
- Upstream evidence: https://github.com/saltbo/agent-kanban; the following fetched files were inspected at review time.
- Files fetched: README.md, LICENSE, package.json, AGENTS.md, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- Agent-first task board, CI/coverage/release badges, tests/specs, docs, agents/skills folders, AGENTS/CLAUDE guidance.
- Explicit cryptographic identity/role/loadable-skills/team framing.
- Strong conceptual fit for durable Discord-started Hermes tasks.

## Risks / caveats

- FSL-1.1 future-license model is not clean MIT/Apache reuse.
- Cloudflare Workers/D1 app may be overbuilt for local Hermes.
- Agents creating/assigning tasks need guardrails to avoid runaway work.

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
