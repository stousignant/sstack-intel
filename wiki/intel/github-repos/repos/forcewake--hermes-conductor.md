---
title: forcewake/hermes-conductor
created: 2026-09-09
updated: 2026-09-09
type: repo-intel
source: https://github.com/forcewake/hermes-conductor
category: agent-orchestration
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-09-09
license: MIT
lifecycle: volatile
confidence: medium
tags: [github-repos, hermes, kanban, coding-agents, worktrees, orchestration]
sources:
  - https://github.com/forcewake/hermes-conductor
  - https://github.com/forcewake/hermes-conductor/blob/main/patterns/01-controller-managed-external-worktree-lanes.md
  - https://github.com/forcewake/hermes-conductor/tree/main/skills
---

# forcewake/hermes-conductor

> Opinionated reference-stack evaluation, reviewed 2026-09-09. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — strong Hermes-native controller/worktree/verifier patterns, constrained by a young evidence base and the risk of creating a second execution-state store.
- **Recommendation:** `distill-pattern`—retain its controller-managed worktree lane as a reference; evaluate one bounded T3 pilot only through the explicit Kanban-pilot route, and do not make native Kanban a second canonical backlog.
- **Usage:** `reference-only`.
- **Fit:** high for deterministic execution after route selection.
- **Maturity:** narrow and young; 71 stars and 7 forks when checked on 2026-09-09.
- **License:** MIT.
- **Confidence:** medium because the implementation and demos are public, while production-volume claims are author-reported.

## What it is

Hermes Conductor is a collection of installable Hermes skills, operating patterns, recovery playbooks, and demos for running external coding CLIs under a native Hermes Kanban controller. It is not a separate workflow runtime or dashboard. [Source: repository README, 2026-09-09]

Its operating shape is:

```text
route-only Hermes conductor
→ native Kanban cards and dependencies
→ Claude Code / OpenCode / Codex / other CLI in isolated worktrees
→ controller inspects diff and reruns gates
→ evidence-bearing completion and integration
```

The author reports that the patterns were distilled from **18 production boards, 367 cards, and 566 agent dispatches**. Treat those figures as credible implementation context but not independently verified adoption statistics. [Source: repository README, 2026-09-09]

## Strong patterns

1. **Route-only controller.** The conductor is explicitly forbidden from implementing; this reduces role collapse and keeps verification independent.
2. **No trust in worker self-reports.** The controller inspects the actual worktree diff, reruns commands, and records commit IDs plus command evidence.
3. **One worktree per mutating lane.** Parallel workers never share a writable checkout.
4. **Dependency-aware sequencing.** Parent links are treated as execution dependencies, and dependent work is controller-sequential unless independence is proven.
5. **Stale-base handling.** Newly promoted lanes are checked against the intended base before execution.
6. **Bounded remediation and approval recovery.** The playbooks cover review/fix races, stalled approvals, stale workers, and evidence-free completion.
7. **Runtime replaceability.** Claude Code, Codex, OpenCode, MiMo, or another CLI can serve as the lane executor without taking over lifecycle authority.

[Source: repository README and pattern 01, 2026-09-09]

## Limits

- It does **not** deterministically classify fuzzy requests into SStack T1–T4 tiers; route selection still comes from an operator, labels, or an orchestrator's policy.
- It assumes native Hermes Kanban owns task lifecycle. The reference architecture assigns canonical executable work and status to GitHub Issues and a single project board.
- The structured external-lane runner with budget caps, explicit tool grants, provenance checks, and JSON receipts is described as forthcoming rather than fully published.
- Public production numbers and incident accounts are author assertions; no independent deployment corpus was found.
- A Kanban pilot would create a second execution-state store. It must remain a bounded projection of a canonical GitHub issue, not a parallel backlog.

## Reference-stack fit

The narrow adoptable unit is **pattern 01 plus the verifier boundary**, not the full authority model:

```text
canonical GitHub issue
→ derived Kanban execution card with issue URL and PR completion contract
→ Codex or Hermes profile works in an isolated worktree
→ Hermes controller verifies current-head diff and deterministic gates
→ independent review
→ GitHub PR remains integration truth
```

This complements SStack's existing rule that worker summaries are untrusted until Hermes reproduces the evidence. It could add durability, retries, comments, run history, and review transitions without introducing a separate workflow runtime. The pilot succeeds only if that operational value exceeds the cost of projecting execution state into Kanban. [Reference-stack synthesis, 2026-09-09]

## Comparison

- **Versus Archon:** far lighter; relies on native Hermes Kanban and skills instead of owning a separate workflow runtime/provider/session database.
- **Versus Crewplane/TAKT:** more Hermes-native and better supported by actual Hermes usage, but less declarative and less capable of static workflow validation.
- **Versus `delegate_task`:** durable and restart-aware at the card/run level; heavier than bounded fork/join research or review.
- **Versus a plain Hermes profile:** adds controller discipline, worktree isolation, evidence rules, and recovery playbooks; the profile remains the default Kanban worker shape.

## Related

- [Hermes Kanban documentation](https://hermes-agent.nousresearch.com/docs)
- [Hermes Execution Routing — Community Patterns](../comparisons/hermes-execution-routing-community-patterns.md)
- [Agent Workflows / Coding Harnesses Repo Comparison](../comparisons/agent-workflows-coding-harnesses.md)
- the established architecture and execution boundary
