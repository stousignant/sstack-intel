---
title: Parallel Agentic Development
created: 2026-06-02
updated: 2026-10-01
type: concept
tags: [ai, agents, software-engineering, worktrees, validation]
sources:
  - https://www.youtube.com/watch?v=rFGlJ4oIlhw
  - https://steipete.me/posts/just-talk-to-it
  - https://steipete.me/posts/2025/optimal-ai-development-workflow
  - https://github.com/steipete/agent-scripts
status: active
---

# Parallel Agentic Development

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

Parallel agentic development means running multiple focused coding agents at once, each with a scoped artifact contract and isolated environment. It is not “open five terminals and pray.” It requires issue-as-spec, worktree isolation, runtime/data isolation, fresh-context validation, and self-healing updates to the AI layer.

## Boundary

This page is the **parallel execution pattern**, not the whole delivery lifecycle. It starts only after work is issue-shaped enough for independent agents and it ends with reviewable proof bundles, PRs/diffs, or explicit handoff artifacts.

Keep it as a child of [Agentic Development Lifecycle](agentic-development-lifecycle.md) and [Harness Engineering](harness-engineering.md): lifecycle decides when parallel work is appropriate; harness engineering supplies isolation, validation, logs, permissions, and cleanup. [Agent Work Packets](agent-work-packets.md) provide the portable context contract for each agent stream.

## Reference loop

1. Planning pass decomposes work into issues/tickets.
2. Each issue gets a dedicated worktree and environment.
3. Agent implements against that issue and produces a PR/diff.
4. Validator reviews PR vs issue in a fresh context.
5. Optional adversarial review uses a different model/agent.
6. Failures update rules, skills, tests, hooks, or workflow nodes.
7. Cleanup merges or removes worktrees, ports, database branches, and stale branches.

## Operational requirements

- Unique ports per worktree.
- Isolated database branch/copy per worktree.
- Dependency setup during worktree creation.
- Clear secret handling and `.env` boundaries.
- PR queue policy to avoid human review pileup.
- Validation proof bundle: issue, diff, tests, logs/screenshots if relevant, risk notes.

## Durable multi-session work state

Parallel execution creates a second problem the loop above does not solve: once several sessions run at once, "what is happening across all of them" has no owner. Two open-source patterns answer different halves, and the useful move is layering them rather than picking one.

Historically, [automazeio/ccpm](../../intel/github-repos/repos/automazeio--ccpm.md) supplied a **workflow pattern**: PRD → epic → GitHub issues → worktrees → standup/status, so cross-session state was answerable from issue state rather than from memory. Treat CCPM as a historical workflow reference, not a reference-stack adoption endorsement; this page owns the parallel-execution/isolation slice. [gastownhall/gastown](../../intel/github-repos/repos/gastownhall--gastown.md) supplies the **durability** pattern: git-backed work state, mailboxes, identities, and handoff ledgers, so that standup is persistent rather than a one-shot report regenerated per session.

A third approach attacks it from the validation side instead of the orchestration side: derive each checkpoint's status from rules and flag it against the *authored* status, so drift is detected rather than narrated. That belongs to [Agentic Development Lifecycle](agentic-development-lifecycle.md) under lifecycle invariants; it is complementary here, not an alternative.

Runners-up considered and not adopted: `generalaction/emdash` (control-plane UI for supervising parallel agents), `multica-ai/multica` (chat-first "agents as teammates", custom license), `saltbo/agent-kanban` (agent task-board semantics). Recorded so the comparison is not re-run.

For workloads spanning concurrent sessions, a shared priority/status interface can reduce handoff reconstruction. In this reference stack, GitHub Issues/Projects remain execution truth; any durable work-state layer reconciles against them rather than becoming a second tracker. [Architecture synthesis, 2026-08-22; see [Agent Memory Architecture](agent-memory-architecture.md) for working-memory boundaries.]

## Workload-conditional guidance

For Hermes/GBrain coding, this pattern fits after work is issue-shaped and independently reviewable. Begin with a small number of isolated worktrees; if PR review becomes the bottleneck, strengthen validation or review capacity before adding agents.

Peter Steinberger's public workflow is a useful counterexample to rigid worktree dogma: he reports running 3–8 agents in a 3×3 terminal grid, often in the same folder, but manages this with blast-radius judgment, atomic commits, visible terminal output, and active interruption when tasks drift. For the reference stack, the deeper lesson is not “copy same-folder parallelism”; it is **scope parallel work by blast radius and rollback cost**. Default to isolated worktrees for repo mutations, but do not turn isolation into ceremony when the task is tiny, visible, and supervised. [Source: [peter steinberger ai development methodology](https://steipete.me/posts/just-talk-to-it), 2026-06-14]

## Related

- [Agentic Coding Systems](agentic-coding-systems.md)
- [Harness Engineering](harness-engineering.md)
- [AI Dark Factory](ai-dark-factory.md)
- [Archon](https://github.com/coleam00/Archon)
