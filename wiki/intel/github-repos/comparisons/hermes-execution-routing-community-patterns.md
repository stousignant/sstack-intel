---
title: Hermes Execution Routing — Community Patterns
created: 2026-09-09
updated: 2026-10-16
type: comparison
status: active
lifecycle: volatile
confidence: medium
tags: [hermes, execution-routing, kanban, coding-agents, worktrees, community-research]
sources:
  - https://hermes-agent.nousresearch.com/docs/user-guide/features/kanban
  - https://hermes-agent.nousresearch.com/docs/user-guide/features/kanban-worker-lanes
  - https://hermes-agent.nousresearch.com/docs/user-guide/features/goals
  - https://hermes-agent.nousresearch.com/docs/guides/delegation-patterns
  - https://github.com/forcewake/hermes-conductor
  - https://github.com/Salomondiei08/oh-my-hermes
  - https://github.com/mooner92/dev-booth
  - https://github.com/ramdhanhdy/hermes-toolkit
---

# Hermes Execution Routing — Community Patterns

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive finding

Public Hermes practice converges on **composing native primitives**, not on adopting one generic workflow engine:

```text
skill or route-only orchestrator profile
→ native Hermes Kanban for durable dispatch and dependencies
→ named Hermes profile or external coding CLI in an isolated worktree
→ controller/reviewer reruns gates against the real artifact
→ GitHub PR and human-controlled integration
```

`/goal` handles persistent completion inside one session, `delegate_task` handles bounded fan-out, Kanban handles durable cross-profile work, and cron or deterministic scripts handle scheduled mechanics. External CLIs such as Codex and Claude Code are usually workers under Hermes rather than lifecycle authorities. [Source: Hermes official docs and public-community scan, 2026-09-09]

The unresolved boundary is **semantic route selection**. Public systems still use skills, profile instructions, labels, explicit operator choice, or an LLM triage step to decide whether work should be direct, delegated, queued, or decomposed. Determinism starts after that decision: assignment, dependency promotion, worktree isolation, retries, review transitions, shell gates, and completion evidence. No public project convincingly eliminates this semantic judgment without hiding it inside another model call. [Source: public-community scan, 2026-09-09]

## Native routing stack

| Need | Hermes primitive | Deterministic boundary | Model-driven boundary |
|---|---|---|---|
| Small work in the current conversation | Direct Hermes tools | Tool effects and explicit verification | Planning and tool choice |
| Bounded parallel reasoning or review | `delegate_task` | Child isolation, batch concurrency, result delivery | Parent chooses delegation and writes child contracts; child execution |
| Persistent single-session completion | `/goal` | Turn budget and shell quality gates | Goal judge and next actions |
| Durable cross-profile work | [Hermes Kanban](https://hermes-agent.nousresearch.com/docs/user-guide/features/kanban) | Task lifecycle, explicit assignee, dependency promotion, atomic claims, retries, review state, run history | Optional decomposition and worker execution |
| Scheduled mechanics | Cron / `no_agent` | Scheduling; script-only execution when `no_agent` | Prompted cron jobs remain agent-driven |
| Coding execution | Hermes profile, Codex, Claude Code, Cursor, OpenCode | Worktree/process boundary and controller-run gates | Implementation choices inside the worker |

## Public methods and projects

### Native Kanban plus controller verification

[forcewake/hermes-conductor](../repos/forcewake--hermes-conductor.md) is the strongest public Hermes-specific operating pattern found. It uses a route-only conductor, one worktree per mutating lane, external coding CLIs as replaceable executors, dependency-ordered Kanban cards, and controller-run verification. The author reports 18 production boards, 367 cards, and 566 dispatches; these numbers are useful but self-reported. [Source: forcewake/hermes-conductor README, 2026-09-09]

`keepConcentration/hermes-kanban-fleet` assigns native Kanban cards directly to a Nous-backed orchestrator, Cursor ACP generalist, or Claude Code ACP coder. `mooner92/dev-booth` goes further and deterministically seeds a fixed 21-stage coding DAG into native Kanban. These prove that Kanban can serve as an execution kernel while profiles or external runtimes remain replaceable. [Source: respective repositories, 2026-09-09]

### Opinionated skill/profile distributions

`Salomondiei08/oh-my-hermes` is the largest visible workflow-layer signal found in this scan. Its CTO profile routes work through native Kanban to Product, Designer, Builder, Reviewer, Security, and Ops roles; skills choose Hermes, Claude Code, or Codex and enforce release approvals. It is useful prior art, but it makes Kanban the roadmap/task authority and overlaps heavily with the shared-skill source, so wholesale adoption would conflict with the reference stack’s GitHub source-of-truth boundary. [Source: Oh My Hermes README, 2026-09-09]

`magnus919/hermes-profiles` provides a Hermes-native SDD phase sequence—Inception, Specify, Review, Plan, Review, Tasks, Review, Implement, Review, Verify—with explicit review outcomes. This is methodology over profiles and Kanban, not an independent workflow runtime. [Source: hermes-profiles SDD profile and review skill, 2026-09-09]

### Deterministic scripts around Kanban

`ramdhanhdy/hermes-toolkit` combines Python/shell card creation, concurrency guards, post-run gates, heartbeats, crash detection, and retries with native Kanban. Public operator reports likewise use systemd, launchd, cron, or small scripts for deterministic mechanics while Hermes handles interpretation and remediation. [Source: hermes-toolkit and public operator reports, 2026-09-09]

### Mission-control interfaces

Minions, Hermes War Room, Hermy HQ, and PatterStage mainly add visibility, approval, or dispatch UX. They do not solve semantic route classification. Some preserve native Kanban; others add their own queue or database and therefore need source-of-truth scrutiny. [Source: public repositories, 2026-09-09]

### External lifecycle owners

Paperclip, Temporal, AgentPlane, and Microsoft Conductor can own more formal durable workflow state while Hermes executes bounded episodes. This is a minority path justified by replay, long waits, signals, or stronger workflow semantics—not the community default. One detailed Paperclip user report describes eventually deleting Paperclip and migrating to native Hermes Kanban after a prolonged failure loop. [Source: public integrations and user report, 2026-09-09]

## Negative evidence

No credible public operating evidence was found for:

- Hermes plus TAKT;
- Hermes plus Crewplane;
- a shipped Hermes–Archon integration;
- broad production use of `hermes-dynamic-workflows` for deterministic coding delivery.

`hermes-dynamic-workflows` is a real Hermes-native dynamic fan-out plugin, but its model-generated Python, weak process-restart recovery, and lack of enforced plan → implement → review → verify semantics make it a research/audit fan-out tool rather than a delivery controller. [Source: repository/source audit, 2026-09-09]

## What an end-to-end pilot must establish

Verify the complete native Kanban → profile/coding worker → independent review → integration lifecycle before claiming end-to-end operation. Manually verified completion or duplicate-dispatch avoidance demonstrates only parts of that contract. When a separate canonical backlog remains authoritative, test stale derived-card detection and reconciliation explicitly. These are evaluation requirements, not results from a private board or evidence of an adopted deployment.

## Implication for the reference stack

The evidence supports evaluating native Kanban as a **derived execution ledger**, not adopting it as a second backlog:

```text
Existing issue/project tracker = canonical commitment, priority, and delivery status
Hermes Kanban card        = bounded execution attempt and handoff history
Hermes/controller         = routing and independent verification authority
Codex/profile worker      = replaceable implementation lane
GitHub PR                 = integration and final evidence surface
```

The candidate pattern is to distill Hermes Conductor's controller-managed worktree lane: every execution card links to its canonical GitHub issue, receives an explicit assignee and workspace, emits evidence, enters independent review, and cannot complete merely because the worker claims success. This is an evaluation proposal, not an adopted reference stack decision. Any pilot must measure whether the derived Kanban state reduces reconstruction and failure recovery enough to justify the duplicate execution ledger. [Source: synthesis, 2026-09-09]

## Evidence quality

- **High:** official Hermes docs/source for primitive behavior; public repository code for concrete integration shape.
- **Medium:** detailed first-person operator reports and Hermes Conductor's production claims.
- **Low:** stars, README claims, tutorials, and proposals without independent run evidence.
- GitHub Discussions are disabled for the main Hermes repository; public usage evidence is representative, not exhaustive.
- Private dotfiles, Discord conversations, and unpublished company deployments are mostly invisible.

## Related

- [hermes kanban](https://hermes-agent.nousresearch.com/docs/user-guide/features/kanban)
- [forcewake/hermes conductor](../repos/forcewake--hermes-conductor.md)
- [agent workflows coding harnesses](agent-workflows-coding-harnesses.md)
- [archon industry alternatives](archon-industry-alternatives.md)

The reusable boundary is separation of methodology, execution attempts and canonical commitments; private operating-state bindings are not dependencies of this comparison.