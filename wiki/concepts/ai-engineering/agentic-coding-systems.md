---
title: Agentic Coding Systems
created: 2026-05-22
updated: 2026-09-07
type: concept
tags: [ai, agents, software-engineering]
sources:
  - wiki/intel/github-repos/repos/garrytan--gstack.md
  - wiki/intel/github-repos/repos/AndyMik90--Aperant.md
  - wiki/intel/github-repos/repos/openclaw--openclaw.md
  - https://www.youtube.com/watch?v=PIdETjcXNIk
  - https://www.youtube.com/watch?v=2KcITKKJikA
  - https://www.youtube.com/watch?v=yBcmIoA-vGs
  - https://www.youtube.com/watch?v=M30gp1315Y4
  - https://www.youtube.com/watch?v=E5-QK3CDVQM
  - https://www.youtube.com/watch?v=Ah9p7v7nJWg
  - https://www.youtube.com/watch?v=dtAJ2dOd3ko
  - https://www.youtube.com/watch?v=mh5XZ-L5SFQ
  - https://steipete.me/posts/just-talk-to-it
  - https://steipete.me/posts/2025/optimal-ai-development-workflow
  - https://github.com/steipete/agent-scripts
  - https://www.youtube.com/watch?v=nQwJVHCtDDY
  - https://www.youtube.com/watch?v=zbmuiaPuiNM
status: active
---

# Agentic Coding Systems

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis
Agentic coding systems are converging on reusable skills, task decomposition, context management, verification loops, and human-in-the-loop review. The best systems do not rely on a single clever prompt; they combine durable instructions, tool access, tests, review, and memory.

## Canonical map

This is the **parent doctrine page** for coding-agent systems: what the ecosystem is becoming, why it matters, and how a reference stack can compose the relevant capabilities. It should not absorb every adjacent implementation pattern. The child pages below stay separate because they answer different questions.

| Concept | Role in the hierarchy | Default routing |
|---|---|---|
| [Harness Engineering](harness-engineering.md) | System-design discipline around agents: tools, permissions, hooks, validators, logs, memory, orchestration, and skills | Use when the question is “what system makes agents reliable?” |
| [Loop Engineering](loop-engineering.md) | Repeatable agent feedback-loop design: triggers, durable state, verifiers, stop conditions, and proof bundles | Use when the question is “what recurring agent routine should run until a condition is met?” |
| [Coding Agent Skill Systems](coding-agent-skill-systems.md) | Workflow capsules and reusable operating doctrine for agents | Use when the question is “what repeated procedure should become a skill/playbook?” |
| [Agentic Development Lifecycle](agentic-development-lifecycle.md) | End-to-end artifact flow from idea to research/prototype/PRD/issues/execution/QA | Use when the question is “where does this work sit in the delivery lifecycle?” |
| [Parallel Agentic Development](parallel-agentic-development.md) | Execution pattern for multiple agents using isolated worktrees/environments and fresh-context validation | Use when the question is “can multiple agents safely work at once?” |
| [Agent Work Packets](agent-work-packets.md) | Portable context/task handoff artifact for another session or agent | Use when the question is “what exactly should the next agent know and return?” |

Disposition for the semantic refactor: **keep all six pages**. Merge would reduce navigability because the overlap is architectural adjacency, not duplicate content.

## Recurring architecture

- Structured skills, slash commands, or playbooks: see [Coding Agent Skill Systems](coding-agent-skill-systems.md).
- Planning before implementation and verification after implementation.
- Requirements/specification and validation are becoming the hard parts as agents compress implementation time; agentic coding systems should invest in better upfront work packets and downstream quality gates, not just faster code generation.
- Parallel agents where task boundaries are clean.
- Agentic engineering as harness/system design: build the repeatable software factory around models, not just prompts to a coding assistant.
- Loop engineering as the repeatable unit inside the harness: design the trigger, state, authority, verifier, and stop condition before letting agents run unattended.
- Capability control over prompt obedience: prompts/skills help behavior, but security boundaries come from what tools the agent can actually reach.
- Persistent specialist agents with bounded domains, shared logs, and accumulated expertise files for complex codebases.
- Peer-to-peer agent messaging when agents need to exchange focused context directly, especially across devices, models, authority boundaries, or verifier roles.
- Context tools like [context7](https://github.com/upstash/context7) and [MCP and Context Tools](mcp-context-tools.md) to reduce hallucinated APIs.
- Memory/query layers like [gbrain](https://github.com/garrytan/gbrain) to reuse project-specific knowledge.

## Peer-to-peer agent communication

IndyDevDan’s Pi-to-Pi demo adds a useful distinction: peer-to-peer agent communication is a primitive beside orchestrator/worker delegation, not a replacement for it. Use orchestration when the problem decomposes into bounded subtasks with a clear owner; use peer-to-peer messaging when two agents have different local authority, model strengths, tools, or context windows and need to coordinate without routing every detail through a bottleneck. [Source: [Pi-to-Pi source](https://www.youtube.com/watch?v=PIdETjcXNIk), 2026-05-29]

The durable design rule is: **a focused agent is a safer agent**. Instead of loading one giant context with every API, production constraint, sandbox provider, and verification task, split the work into specialized agents and give them a narrow message contract. This is especially valuable for production/dev handoffs where one agent can inspect sensitive state and return only redacted, reproducible slices. [Source: [Pi-to-Pi source](https://www.youtube.com/watch?v=PIdETjcXNIk), 2026-05-29]

Caveat: peer-to-peer systems need explicit end states, budget limits, and loop prevention. Agent count and communication bounces raise cost linearly, so “more agents” is only good when specialization reduces error or unlocks local authority. [Source: [Pi-to-Pi source](https://www.youtube.com/watch?v=PIdETjcXNIk), 2026-05-29]

## Agentic engineering and software factories

IndyDevDan’s “agentic engineering” frame is useful because it moves the locus of leverage from **using agents** to **owning the system that makes agents useful**. The senior-engineer opportunity is not prompt fluency; it is building harnesses, workflows, validation loops, API/CLI access, and repeatable factories that turn intent into reliable output. [Source: [Agentic Engineering review](https://www.youtube.com/watch?v=2KcITKKJikA), 2026-05-29]

The practical rule: **build factories, not features**. If a task will recur, design the agent workflow that produces plans, changes, tests, reviews, notes, or releases repeatedly. Always-on agents should be gated by useful-token economics: do not scale cron/daemon agents until the workflow demonstrably creates more value than it costs. [Source: [Agentic Engineering transcript](https://www.youtube.com/watch?v=2KcITKKJikA), 2026-05-29]

## Capability control and Bash safety

Coding-agent safety should be assessed by reachable capabilities, not intended behavior. Prompt instructions, system prompts, and skills are useful friction, but they are not hard boundaries over long contexts and thousands of tool calls. Bash is especially risky because it is a universal adapter: an agent with shell can reach cloud CLIs, package scripts, inline interpreters, test runners, database tools, and arbitrary local scripts. [Source: [Delete the Bash Tool review](https://www.youtube.com/watch?v=yBcmIoA-vGs), 2026-05-29]

Use a trust ladder: prompt guidance < system prompt < blacklist < whitelist < no Bash / explicit tools only. Production-adjacent agents should default toward allowlisted commands or explicit tools; blacklists are only damage-control baselines. The key test is whether an allowed command can indirectly execute arbitrary code. [Source: [Delete the Bash Tool transcript](https://www.youtube.com/watch?v=yBcmIoA-vGs), 2026-05-29]

## Agent experts and multi-team coding

“One agent in a terminal” is a transitional interface for larger systems. The durable architecture is orchestrator → team leads → specialist workers, with the human talking to one legible interface while the system fans out planning, implementation, validation, security, and domain-specific work. [Source: [One Agent Is Not Enough review](https://www.youtube.com/watch?v=M30gp1315Y4), 2026-05-29]

Specialist agents become more valuable when their expertise compounds: role-specific prompts, skills, tools, permissions, shared session logs, and persistent “mental model” files. Domain locking is a trust mechanism, not bureaucracy: planner agents can read broadly without writing; DevOps agents own infra; validators provide separate perspectives instead of builders checking their own work. [Source: [One Agent Is Not Enough transcript](https://www.youtube.com/watch?v=M30gp1315Y4), 2026-05-29]

## Cole Medin / harness-driven coding

Cole Medin's recent Archon and dark-factory videos reinforce the same direction from another angle: the valuable skill is **[Harness Engineering](harness-engineering.md)**, not raw prompting. A harness packages rules, tools, hooks, skills, worktrees, validators, logs, model routing, and approval gates around coding agents so the system can execute repeatably. [Source: [Harness Engineering review](https://www.youtube.com/watch?v=ulNsa0sD8N0), 2026-05-28]

Archon makes agent workflows explicit as versioned YAML DAGs with deterministic and agent nodes. When a workflow needs inspectable branching and gates, compare [Archon](https://github.com/coleam00/Archon)'s artifact contract with native Hermes delegation before building custom orchestration. [Source: [Archon harnesses review](https://www.youtube.com/watch?v=qMnClynCAmM), 2026-04-09]

The industry comparison sharpens the boundary: GitHub Agentic Workflows and GitLab Duo custom flows are the nearest coding-platform analogues, Microsoft Conductor is the nearest generic deterministic graph runner, and the real incumbent is CI/CD plus coding-agent glue. Archon's distinct value is repository-native composition of provider portability, isolated worktrees, deterministic gates, and resumable human approval. See [archon industry alternatives](../../intel/github-repos/comparisons/archon-industry-alternatives.md). [Source: architecture synthesis, 2026-08-30]

The dark-factory concept is the autonomy ceiling: issue intake, triage, implementation, validation, merge/deploy, regression, and issue generation with little or no human intervention. For the reviewed Hermes/GBrain stack, this belongs in sandboxes first. Autonomy scales only when governance, scope limits, capability boundaries, independent validation, and rollback are stronger than the agent's urge to declare success. [Source: [Dark Factory review](https://www.youtube.com/watch?v=6woc6ii-zoE), 2026-04-16]

Peter Steinberger's public `agent-scripts`/OpenClaw-adjacent workflow adds a practical middle layer between one-off coding agents and a dark factory: a root maintainer orchestrator that reads GitHub queues, classifies autonomous vs owner-needed work, delegates bounded repo workers, polls only when continuous orchestration is requested, and asks for exact decisions after proof is ready. For the reviewed stack, this is the sane shape of “always-on agents”: read-only queue/status polling first, review-gated implementation next, and merge/release only after explicit authorization and proof. [Source: [Peter Steinberger’s agent-scripts](https://github.com/steipete/agent-scripts), 2026-06-14]

Parallel coding requires [Parallel Agentic Development](parallel-agentic-development.md) discipline: issue-as-spec, one worktree/environment per agent, PR-as-validation-artifact, fresh-context review, and self-healing updates to the AI layer after defects. More agents without isolation and validation just creates faster chaos. [Source: [Parallel worktrees review](https://www.youtube.com/watch?v=rFGlJ4oIlhw), 2026-04-23]

[Loop Engineering](loop-engineering.md) is the current practical name for the “factories, not prompts” slice of this doctrine. The useful pattern is closed-loop delegation: a scheduler or event starts a bounded agent routine, durable context/state is loaded from repos/GitHub/GBrain/second-brain, one agent acts, another verifier or deterministic check judges, and the loop stops on proof or escalates to a human decision. The first implementation should be one small infrastructure-operations loop, not a broad autonomous factory. [Source: [Loop Engineering source](https://www.youtube.com/watch?v=w285kJY3Xws), 2026-06-13; [Mastering Claude Code review](https://www.youtube.com/watch?v=6eBSHbLKuN0), 2025-05-22]


## Matt Pocock / skill-first software factories

Matt Pocock's recent videos reinforce that agentic coding is becoming a workflow-design problem. The useful stack is lifecycle artifacts plus scoped execution: idea, research cache, prototype, PRD, vertical-slice issues, execution, QA, and then handoffs or review packets when work branches. [Source: [Agentic Development Lifecycle](agentic-development-lifecycle.md), 2026-06-03]

Sandcastle is a concrete example of this direction: GitHub issues feed a planner, implementers run in sandboxed branches, reviewers apply project standards, and a merger agent integrates results. The durable lesson is not to let AFK agents loose; give them sandbox boundaries, backlog truth, branch isolation, explicit review, and merge governance. [Source: [2026 04 30 i open sourced my own afk software factory](https://www.youtube.com/watch?v=E5-QK3CDVQM), 2026-04-30]

Handoff documents add the human-scale version of the same pattern: make work portable between sessions and agents without dragging the entire parent context along. This turns context management into explicit [Agent Work Packets](agent-work-packets.md) rather than hidden chat sediment. [Source: [2026 05 21 handoff is my new favourite skill](https://www.youtube.com/watch?v=dtAJ2dOd3ko), 2026-05-21]

## Queues over infinite loops

Matt’s workflow interview adds a useful correction to loop hype: for real development, many AFK coding systems should be modeled as **queues of scoped work packets**, not one infinite autonomous loop. Issues or tasks are explored, scoped, labeled for implementation, run in sandboxes, reviewed with proof artifacts, and removed from the queue only after merge/acceptance. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]

For a stack using GitHub Issues/Projects as backlog truth, Hermes and an owned specification bridge can produce and verify work packets while sandboxed workers execute without inheriting cockpit authority. The human checkpoint should move later only after proof bundles and sampled review establish that the producing system is trustworthy. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]

## For the reviewed Hermes/GBrain reference stack

- **Reuse existing agent stacks where possible.** Build only the orchestration or integration layer that is unique to the target system.
- Use Hermes as the reference cockpit and GBrain as the source-backed index, without making either a competing canonical store.
- Use source-layer policy and deterministic graph checks as a proving ground for agent-maintained knowledge work.
- Make Hermes more autonomous only where repeated workflows have clear value/ROI, not because “always-on agents” sound appealing; production/credential-adjacent agents must not have ambient Bash.
- Treat loop design as the escalation path for recurring work: prove one safe, inspectable loop before building generic orchestration.
- Harden tool permissions before expanding autonomy; merge/release only follows explicit authorization and proof.
- Evaluate persistent expert roles for planner/builder/validator/librarian/DevOps work, with explicit path permissions and inspectable logs.
- Evaluate sandboxed execution patterns such as [sandcastle](https://www.youtube.com/watch?v=E5-QK3CDVQM) before building custom Hermes orchestration for unattended execution and isolated branches.
- Use [Agent Work Packets](agent-work-packets.md) for handoff/review/research/prototype branches so parent sessions stay focused.
- Add peer messaging when verifier diversity, cross-device context, or distinct authority boundaries make direct coordination cheaper than a central relay.
- Evaluate Archon-style DAGs and worktree-based parallelism before designing custom orchestration.

## Related

- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Loop Engineering](loop-engineering.md)
- [Agentic Development Lifecycle](agentic-development-lifecycle.md)
- [Agent Work Packets](agent-work-packets.md)
- [sandcastle](https://www.youtube.com/watch?v=E5-QK3CDVQM)
- [MCP and Context Tools](mcp-context-tools.md)
- personal AI operating system
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- [gbrain](https://github.com/garrytan/gbrain)
- [context7](https://github.com/upstash/context7)
- software engineering career
- [agent-work-orchestration](../../intel/github-repos/comparisons/agent-work-orchestration.md)
- [Archon industry alternatives and positioning](../../intel/github-repos/comparisons/archon-industry-alternatives.md)

## Source material

- `wiki/intel/github-repos/repos/garrytan--gstack.md`
- `wiki/intel/github-repos/repos/AndyMik90--Aperant.md`
- `wiki/intel/github-repos/repos/openclaw--openclaw.md`
- https://www.youtube.com/watch?v=PIdETjcXNIk
- https://www.youtube.com/watch?v=2KcITKKJikA
- https://www.youtube.com/watch?v=yBcmIoA-vGs
- https://www.youtube.com/watch?v=M30gp1315Y4
