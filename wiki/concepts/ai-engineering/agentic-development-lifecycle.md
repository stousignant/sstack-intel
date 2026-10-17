---
title: Agentic Development Lifecycle
created: 2026-06-03
updated: 2026-09-29
type: concept
tags: [ai, agents, software-engineering, workflows]
sources:
  - https://www.youtube.com/watch?v=Ah9p7v7nJWg
  - https://www.youtube.com/watch?v=EJyuu6zlQCg
  - https://www.youtube.com/watch?v=nQwJVHCtDDY
  - https://www.youtube.com/watch?v=QBfXiWvM0qc
  - https://claude.com/blog/the-ai-native-sdlc-playbook
status: active
---

# Agentic Development Lifecycle

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

Nontrivial agentic coding should move through durable artifacts instead of one giant prompt. Matt Pocock's seven-phase workflow is the clean default: **idea → research → prototype → PRD → issues/Kanban → execution → QA**. [Source: [2026 03 03 the 7 phases of ai driven development](https://www.youtube.com/watch?v=Ah9p7v7nJWg), 2026-03-03]

## Boundary

This page is the **process sequence** for agentic software work. It should answer “what phase is this work in, and what artifact should exist next?” rather than becoming a general agentic-coding thesis.

Keep adjacent pages separate:

- [Agentic Coding Systems](agentic-coding-systems.md) owns the broader coding-agent doctrine.
- [Harness Engineering](harness-engineering.md) owns the system around agents that makes the lifecycle reliable.
- [Parallel Agentic Development](parallel-agentic-development.md) is an execution-phase specialization for multiple isolated agents.
- [Agent Work Packets](agent-work-packets.md) are handoff/review/research artifacts that can move between lifecycle phases.
- [Coding Agent Skill Systems](coding-agent-skill-systems.md) captures reusable procedures that execute parts of the lifecycle.

The lifecycle is the **artifact sequence**, not a specific orchestrator. The [agent-work orchestration comparison](../../intel/github-repos/comparisons/agent-work-orchestration.md) surveys external ways to schedule and coordinate execution; [OpenAI Symphony](../../intel/github-repos/repos/openai--symphony.md) is one source example centered on run evidence and proof of work. Use [Parallel Agentic Development](parallel-agentic-development.md) for the isolation/concurrency pattern and [Agent Work Packets](agent-work-packets.md) for the portable input and return contract. These are related layers, not competing lifecycle definitions or adoption endorsements.

## Lifecycle

1. **Idea** — capture the intent, problem, user need, bug, or refactor goal.
2. **Research** — when APIs, repo areas, or constraints are unknown, create a sprint-scoped cache the agent can reopen.
3. **Prototype** — when taste, UX, architecture, or feasibility is uncertain, make the unknown concrete before writing a spec.
4. **PRD** — describe the destination: problem, behavior, user stories, and durable decisions.
5. **Issues / Kanban** — turn the destination into vertical slices with blockers and parallelizable work.
6. **Execution** — let agents implement bounded slices, ideally with tests and branch/worktree isolation.
7. **QA** — generate a human-checkable QA plan, inspect the result, and feed defects back into issues.

## Why it matters in agent delivery environments

This lifecycle is a better default than either “just prompt Claude” or “build a heavy process cathedral.” It gives a Hermes-based environment enough structure to route work through skills, scripts, subagents, and verification without turning every task into bureaucracy.

## AFK queue variant

A Matt-style AFK variant of the lifecycle is: **grill-me / design interview → PRD → vertical-slice issues → sandboxed AFK implementation → proof-bundle review → merge/accept/learn**. The important move is not letting agents code sooner; it is preserving strategic human control at the design/spec boundary and making execution reviewable after the work packet runs. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]

Treat this as a queue lifecycle, not a single loop. Items should carry enough scope, constraints, tests, and review expectations for another agent/session to run without reloading the entire parent context. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]

## Lifecycle invariants

Lifecycle labels are claims, not evidence. For recurring agent workflows, derive parent state from canonical child artifacts and reject impossible transitions:

- an epic or spec is not complete while required child issues/checkpoints remain open;
- execution is not accepted without the validation and review artifacts its work packet required;
- a promoted source cannot leave its review draft, watch log, or target-page provenance in a pending state;
- a runtime projection is not current merely because its source manifest changed.

Prefer cheap deterministic checks over asking an agent to remember these relationships. Keep GitHub or the existing domain tracker as execution truth; owned specification bridge may prepare the work graph, but lifecycle linting should reconcile state rather than introduce a parallel project-management database. Retired planning systems are history, not active routing. [Source: [2026 08 20 75m founder reveals his agentic engineering setup](https://www.youtube.com/watch?v=QBfXiWvM0qc), promoted 2026-08-26]

## Anthropic's six-stage framing

Anthropic's Applied AI team publishes the same lifecycle in enterprise vocabulary — plan, design, build, test, deploy, maintain — and adds two things the phase list above does not carry. [Source: [The AI-Native SDLC Playbook](https://claude.com/blog/the-ai-native-sdlc-playbook), 2026-08-21]

**The lifecycle is a loop, and each stage's exit criterion is a committed artifact the next stage reads.** `intent.md` → `spec.md` → `plan.md` → the diff and its tests → the PR and its review findings → the incident record, which is written back as the next `intent.md`. The chain of commits is also the audit trail: who asked for what, what the agent produced, who approved it. The reason for markdown in the early stages is specific — a non-engineer and an agent can both read and act on the same file. [Source: [The AI-Native SDLC Playbook](https://claude.com/blog/the-ai-native-sdlc-playbook), 2026-08-21]

**Controls form a ladder by binding strength, and the lifecycle should place each rule on the right rung.** `CLAUDE.md` is context, skills are advisory, hooks are deterministic, and managed settings cannot be overridden by the engineer at all. A policy that must always hold needs something deterministic behind the skill that states it. [Source: [The AI-Native SDLC Playbook](https://claude.com/blog/the-ai-native-sdlc-playbook), 2026-08-21]

Scale the artifact count to the number of real handoffs. Five committed files per change exists to survive a product manager, an analyst, a designer, an engineer, QA, and a release manager. Solo or near-solo work has one or two handoffs and should carry one or two artifacts — the invariant is that each stage leaves something the next stage can read, not that every named file exists.

## Testing the configuration, not just the code

The QA phase has a second object once agents write the diff: the configuration that steers the agent. Changes to `CLAUDE.md`, skills, or hooks should be regression-tested the way code is — a suite of real tasks with their accepted outcomes, run on config change, with the pass rate gating the merge, and every production incident becoming a permanent case. The suite is live: as models improve, cases stop discriminating and must be replaced. [Source: [The AI-Native SDLC Playbook](https://claude.com/blog/the-ai-native-sdlc-playbook), 2026-08-21]

Two verification mechanisms are distinct and both belong in the lifecycle. The **feedback loop** runs throughout the task so the session fixes its own mistakes before a human sees them. The **verifier subagent** is a fresh context window invoked once the session believes it is done, so the verdict is not coloured by the assumptions that produced the code. And the loop needs protecting from the agent inside it: a hook that blocks edits to test files during a fix task, with the failing test written and committed before the fix. [Source: [The AI-Native SDLC Playbook](https://claude.com/blog/the-ai-native-sdlc-playbook), 2026-08-21]

## The reviewer ceiling

Parallel sessions and autonomous loops raise throughput into a fixed human review capacity, which is the lifecycle's real constraint once build is cheap. Add streams only while review is keeping up. [Source: [The AI-Native SDLC Playbook](https://claude.com/blog/the-ai-native-sdlc-playbook), 2026-08-21]

Note the unresolved tension in the source: it wants human attention concentrated at gates *and* wants more parallel streams, and it does not say what to do when the gate queue becomes the new bottleneck — the same failure mode it opens by describing. Treat reviewer capacity as the budget the rest of the lifecycle spends against.

## Skill mapping

- Idea clarification: `grill-me` / design-tree interviewing.
- Research: sprint-scoped research cache.
- Prototype: throwaway prototype skill.
- PRD: write PRD skill.
- Issues: PRD-to-issues / vertical-slice decomposition.
- Execution: implementation agent with TDD, preferably sandboxed for AFK work.
- QA: review, proof bundle, thermonuclear review, manual QA checklist, and feedback into the producing harness.

## Related

- [Agentic Coding Systems](agentic-coding-systems.md)
- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Agent Work Packets](agent-work-packets.md)
- [The AI-Native SDLC Playbook (Anthropic)](https://claude.com/blog/the-ai-native-sdlc-playbook)
