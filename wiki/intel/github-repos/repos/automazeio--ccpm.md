---
title: automazeio/ccpm
type: repo-intel
aliases: [ccpm, GitHub repo: automazeio/ccpm]
source: https://github.com/automazeio/ccpm
category: agent-work-orchestration
topics: [github-repo, agent-workflows, github-issues, worktrees, spec-driven-development]
status: deep-analyzed
usefulness_score: 92
recommendation: reference-only
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-09-07
license: MIT
---

# automazeio/ccpm

> Opinionated reference-stack evaluation, reviewed 2026-09-07. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `92/100` — strongly aligned with workflows requiring durable agent execution: PRD → epic → GitHub issues → worktrees → parallel execution → standup/status.
- **Recommendation:** `reference-only`; dated reference-stack judgment, not a recommendation to run CCPM.
- **Usage observed 2026-09-07:** `pattern-in-use`. Pattern influence in the reference stack, not proof of upstream runtime installation.
- **Review candidate:** None. Revisit only as historical comparison evidence.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Directly targets durable agent project execution and coordination overhead in long-running coding/review work. |
| Leverage | 25/25 | Could turn long-running coding/review work into visible issue-backed work streams. |
| Reuse readiness | 18/20 | MIT, skill-pack shape, small repo, shell scripts and docs; needs sandbox before standardizing. |
| Maturity/trust | 12/15 | Active enough and auditable; README eval claims are still project claims, not independently verified. |
| Differentiation | 13/15 | Strong GitHub Issues + worktree contract; overlaps but may sharpen Hermes Kanban. |

## Historical verdict (2026-06-03)

CCPM was the strongest immediate candidate in this batch. Its useful payload was not “another PM tool”; it was a crisp execution contract for agents: requirements become PRDs, PRDs become epics, epics become GitHub issues, and issues run in isolated worktrees with visible status. Those useful ideas can inform specification-driven planning and supervised delivery without retaining CCPM as a runtime.

## Reference-stack relevance

- Converts agent work from chat-memory into durable GitHub artifacts.
- Could improve SStack/Hermes long-running coding missions: owner, issue, worktree, dependency, standup, blocked, next.
- At the time, it looked like a possible benchmark against Hermes Kanban before more custom orchestration was built.

## What it is

CCPM is an Agent Skills-compatible project-management skill system for AI coding agents. It advertises spec-driven development using PRDs, GitHub Issues, and multiple agents running in parallel.

## Evidence checked

- GitHub metadata on 2026-06-03: MIT license, ~8.1k stars, pushed 2026-03-18.
- README sections for workflow, GitHub Issues source-of-truth, parallel execution, install, and skill structure.
- Repomix pack: a temporary Repomix evidence pack — 25 files / ~26k tokens; no suspicious files detected.
- Inspected packed files: `skill/ccpm/SKILL.md`, `references/plan.md`, `references/execute.md`, `references/sync.md`, `references/track.md`, and status scripts.

## Strengths

- GitHub Issues as shared state is simple and team-compatible.
- Worktree-based parallel execution aligns with safe multi-agent coding.
- Status/standup/blocked/next scripts are deterministic and agent-friendly.
- Agent Skills-compatible packaging is directly relevant to SStack shared-skill design.

## Risks / caveats

- GitHub Issues may be too heavyweight for private second-brain actions or local-only tasks.
- README's eval-score claim should be treated as a project claim until reproduced.
- Any adoption would require a reference-stack sandbox; the dated usage observation is not an active comparison task.

## Integration ideas

- CCPM supplies source patterns for work-order shape: parent, child, dependency, worktree, and proof bundle. A native specification bridge and Hermes-first execution can reuse these without importing a second planning runtime.
- The parallel-execution view of that pattern is captured in [Parallel Agentic Development](../../../concepts/ai-engineering/parallel-agentic-development.md); its artifact sequence is covered by [Agentic Development Lifecycle](../../../concepts/ai-engineering/agentic-development-lifecycle.md).

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [garrytan/gstack](garrytan--gstack.md)
- [openai/symphony](openai--symphony.md)
- [microsoft/agentrc](microsoft--agentrc.md)

## Review candidates and context

- Historical reference only: use the PRD → epic → issue → worktree → proof sequence without implying an active adoption or comparison task.
