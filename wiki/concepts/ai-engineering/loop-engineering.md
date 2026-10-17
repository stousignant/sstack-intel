---
title: Loop Engineering
aliases:
  - Closed-loop delegation design
  - Agent loop design
  - Loop Engineering 101
created: 2026-06-15
updated: 2026-09-10
type: concept
status: active
tags: [ai, agents, harnesses, agentic-coding, workflows]
sources:
  - https://www.youtube.com/watch?v=w285kJY3Xws
  - https://www.youtube.com/watch?v=6eBSHbLKuN0
  - wiki/concepts/ai-engineering/harness-engineering.md
  - https://www.youtube.com/watch?v=dMrm2jAyrKM
  - https://www.youtube.com/watch?v=F4a8aMLb678
  - https://www.youtube.com/watch?v=1qGH6NwTj3o
confidence: medium
---

# Loop Engineering

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

Loop engineering is the design of repeatable AI-agent feedback loops: a trigger starts the loop, the agent receives bounded context and authority, tools perform work, validators check results, durable state records progress, and explicit stop conditions decide whether to continue, escalate, or finish.

In a Hermes-based reference stack, the sharper name is **closed-loop delegation design**. The goal is not to write cleverer prompts or spawn more autonomous agents; it is to build inspectable routines that repeatedly convert trusted inputs into verified outputs while preserving human agency.

## Boundary

This page is a child of [Harness Engineering](harness-engineering.md). Harness engineering covers the whole system around agents: context, tools, permissions, hooks, memory, skills, validation, and orchestration. Loop engineering is the specific pattern where those pieces run repeatedly or until a condition is met.

Keep adjacent pages separate:

- [Harness Engineering](harness-engineering.md) — broader substrate around model calls.
- [Agentic Coding Systems](agentic-coding-systems.md) — parent doctrine for coding-agent ecosystems and software factories.
- [AI Dark Factory](ai-dark-factory.md) — high-autonomy loop ceiling; not the default first build.
- [Parallel Agentic Development](parallel-agentic-development.md) — isolated multi-agent execution pattern.
- [Agent Work Packets](agent-work-packets.md) — handoff artifact for loop iterations and agent boundaries.

## Loop anatomy

A production-worthy loop should name these fields before implementation:

| Field | Question | Reference-stack default |
|---|---|---|
| Trigger | What starts the loop? | Cron, GitHub event, Discord command, file change, CI failure, or manual run |
| Intent | What outcome is the loop trying to produce? | One useful state transition, not vague “improvement” |
| Context | What does the agent read? | Repo files, issue body, logs, GBrain/second-brain pages, prior proof bundle |
| Authority | What may it do? | Read-only first; writes/PRs only when bounded; no merge/post/public action without approval |
| Action | What work surface can it mutate? | Branch/worktree, draft note, issue comment, PR, local report |
| Verifier | Who/what checks it? | Tests, lint, typecheck, retrieval proof, second agent/model, or human review |
| Stop condition | When is it done? | Verifiable condition, explicit escalation, budget limit, or “no actionable item found” |
| Trigger class | What kind of trigger starts it? | Event/action, schedule/cron, or human kickoff; each still needs the same goal/verifier contract |
| State store | Where does progress live? | GitHub issue/project, repo state file, second-brain page, GBrain-visible report |
| Budget | How does it avoid runaway cost? | Small cadence, bounded repeat count, token/runtime ceiling, quiet no-op behavior |
| Proof bundle | What evidence is returned? | Diff, commands run, test output, links, paths, retrieval proof, unresolved risks |

## Automation vs loop

The useful boundary from the Matthew Berman video is: **automation runs a sequence; a loop decides whether the goal has been reached and whether another pass is warranted.** A cron job, GitHub event handler, or human kickoff can all trigger useful automation, but it becomes loop engineering only when the system also has a goal, verifier, stop/escalation condition, durable state, and budget/no-op behavior. Cadence alone is not enough: “run every 30 minutes” still needs a contract that says what proof ends a run and what evidence justifies continuing. [Source: [Only the best are using them...](https://www.youtube.com/watch?v=dMrm2jAyrKM), 2026-06-08]

## Finite goals vs standing concerns

A finite goal has a finish line; a **standing concern** maintains an evolving condition such as “keep these records aligned” or “watch this question.” In Hermes, compose the latter as a profile supplying stable role and policy, `/loop` revisiting the concern, Kanban holding bounded work it discovers, and `/goal` pursuing each finite closure. Every cycle still needs explicit authority, evidence, escalation, budget, and quiet no-op behavior.

Prefer standing concerns whose work happens in inspectable systems and leaves a checkable result or retry path. Stronger models may need less method scaffolding, but they do not remove the need for intent, boundaries, verification, or human judgment on consequential actions. [Source: [GPT-6 Astra Doesn't Need Your Instructions Anymore](https://www.youtube.com/watch?v=1qGH6NwTj3o), 2026-09-10]


## Loop archetypes

The Matthew Berman loop-examples video is useful as a catalog of loop shapes, not as proof that every workflow should become autonomous. The reusable pattern is: **define the quality bar, rank gaps, fix the highest-leverage gap, rerun the same check, and repeat until no critical gaps remain**. The safest archetypes have a cheap deterministic verifier; the riskier ones use LLM-as-judge and should stay bounded, review-oriented, and budget-capped. [Source: [7 INSANE loops you need to try right now](https://www.youtube.com/watch?v=F4a8aMLb678), 2026-06-19]

| Archetype | Loop goal | Verifier class | Reference-stack example |
|---|---|---|---|
| Performance/regression sweep | Every target stays under a measurable threshold | Deterministic metric | Only use when the repo/app has repeatable measurements; report proof and stop on budget. |
| Documentation drift sweep | Docs reflect recent code/system changes | LLM-as-judge plus diff review | Good as a draft PR/report loop; keep human review before canonical docs mutate broadly. |
| Logging/error sweep | Important paths have useful logs; production errors are traced/fixed | Mixed: logs/tests/PR checks | Candidate when recurring errors have a safe, attributable fix path; otherwise report and stop. |
| SEO/GEO or retrieval-quality audit | Critical discoverability/answer-quality gaps are gone | Tooling score, eval set, or LLM judge | Translate to GBrain/Hermes retrieval evals: run fixed queries, capture evidence, patch highest-leverage gap, rerun. |
| Full product evaluation | Scenarios meet an explicit quality bar | Mostly LLM-as-judge | Treat as an exploration/review loop, not unattended execution; require scenario set, rubric, evidence, and runtime cap. |

The anti-pattern is open-ended feature construction: “loop until the product/feature is done” outsources taste and scope to the model, which is exactly where loops become expensive agent soup.

## Principles

- **Prompts live inside loops.** The prompt still matters, but it is only one component inside trigger/context/action/verification/state.
- **State must outlive chat.** Durable state belongs in repos, GitHub Issues/Projects, second-brain pages, GBrain-indexed reports, or explicit state files. Chat context is not a reliable loop memory.
- **Separate maker and checker.** The agent that drafts a change should not be the only judge of whether the change is correct.
- **Stop on proof, not vibes.** “Make this better” is not a loop. “Tests pass, lint clean, PR opened, retrieval verified, or human decision needed” is a loop.
- **Start small and boring.** A daily report loop with no write authority is a better first loop than an unattended software factory.
- **Autonomy must pay rent.** A loop is worth running only if it saves time, reduces cognitive load, improves decisions, or produces usable assets more reliably than manual prompting.
- **Human agency stays in the design.** The dangerous failure mode is cognitive surrender: using loops to avoid understanding the work rather than to multiply judgment.

## Hermes implementation note

For Hermes specifically, distinguish the runtime primitives before designing a loop:

- `/goal` is immediate bounded continuation in the current session.
- Plain cron is scheduled independent work.
- `/loop` is cron-backed recurring mission control with previous-tick context, duplicate-output suppression, no-progress auto-pause, optional dynamic cadence, and optional post-run `--verify` feedback.

Consult the public Hermes loop documentation for runtime semantics; this concept is not local configuration authority. The important design rule is that long-hours autonomy should be repeated bounded ticks plus durable state, not a single oversized model/tool turn.

## Daniel Moka “Loop Engineering 101” infographic

Daniel Moka's infographic is useful as a compact checklist for making loop engineering operational:

- **Loop-ready work has an automatic definition of done.** Good candidates repeat often, can be checked automatically, and make bad attempts cheap to discard.
- **Closed loops beat open loops for production work.** Open loops explore; closed loops constrain the agent with goals, steps, and validation checks so each pass improves rather than merely consumes tokens.
- **A good loop has six wired parts:** automations as the heartbeat, worktrees for isolation, skills/rules for durable project knowledge, connectors to real tools, subagents for maker/checker separation, and memory outside chat.
- **Single-agent loops are the default.** Fleet/orchestrated loops are justified only when one agent cannot solve the job; otherwise they add overhead and coordination failure.
- **The quality gate is non-negotiable.** Use checks the agent cannot argue with: compiler, type system, tests, lint, analyzers, CI, and other deterministic verifiers.
- **Self-learning belongs in curated artifacts.** When a loop repeats a mistake, promote the lesson into `RULES.md`, skills, tests, CI, or second-brain doctrine; do not let the loop auto-fill noisy memory.
- **Keep human merge authority.** A good coding loop can reproduce, fix, verify, and ping; it should not merge/ship on its own without explicit approval.

For a Hermes-based system, the translation is: **automate the reproduce-fix-verify grind, but retain human approval and merge control until the gate is demonstrably trustworthy for that workload.** [Source: Daniel Moka, “Loop Engineering 101” infographic, reviewed 2026-06-19; independently accessible public copy not verified.]

## Workload-conditional application

For a recurring infrastructure workflow, a low-risk loop can inspect bounded repo/issue/knowledge signals, select one worthwhile maintenance action or no-op, return evidence and a suggested next step, and draft only within authorized surfaces. A Hermes implementation can reuse native scheduling, skills, source-backed queries, repo inspection, and GitHub work state when those primitives cover the workload; authority, budget, stop conditions, and external-side-effect gates remain explicit on every tick.

## Source notes

The derivative video [The Creator of Claude Code Doesn't Write Prompts Anymore. He Writes Loops.](https://www.youtube.com/watch?v=w285kJY3Xws) gives the compact loop thesis: keystroke → prompt → loop; `/loop` as rhythm; `/goal` as finish line; and the rules of maker/checker separation, verifiable stop conditions, and state in repo rather than chat.

The official Anthropic video [Mastering Claude Code in 30 minutes](https://www.youtube.com/watch?v=6eBSHbLKuN0) grounds the idea in concrete harness practices: codebase Q&A before editing, planning and approval for big changes, team tools/MCP, project context files, slash commands, verification through tests/screenshots/simulators, permissions, SDK/CLI automation, and parallel isolated sessions.

## Related

- [Harness Engineering](harness-engineering.md)
- [Agentic Coding Systems](agentic-coding-systems.md)
- [AI Dark Factory](ai-dark-factory.md)
- [Parallel Agentic Development](parallel-agentic-development.md)
- [Agent Work Packets](agent-work-packets.md)
- [Hermes Agent](https://github.com/NousResearch/hermes-agent)
- [hermes loops](https://hermes-agent.nousresearch.com/docs/reference/cli-commands)
