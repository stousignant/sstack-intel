---
title: Harness Engineering
created: 2026-06-02
updated: 2026-08-30
type: concept
tags: [ai, agents, agentic-coding, harnesses, workflows]
sources:
  - https://www.youtube.com/watch?v=ulNsa0sD8N0
  - https://www.youtube.com/watch?v=efRIrLXoOVA
  - https://www.youtube.com/watch?v=qMnClynCAmM
  - https://arxiv.org/abs/2606.09498
  - wiki/concepts/ai-engineering/loop-engineering.md
  - https://www.youtube.com/watch?v=w285kJY3Xws
  - https://www.youtube.com/watch?v=6eBSHbLKuN0
  - https://www.youtube.com/watch?v=nQwJVHCtDDY
  - https://www.youtube.com/watch?v=zbmuiaPuiNM
  - https://www.youtube.com/watch?v=8ZgpAXe5V5w
  - wiki/intel/github-repos/repos/kunchenguid--axi.md
  - wiki/intel/github-repos/repos/deepseek-ai--deepseek-harness.md
  - https://www.youtube.com/watch?v=1NyOG9z9RT0
  - https://www.youtube.com/watch?v=S_QdQ1G4GlU
  - https://www.youtube.com/watch?v=QBfXiWvM0qc
  - wiki/intel/github-repos/repos/revfactory--harness.md
status: active
---

# Harness Engineering

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

Harness engineering is the discipline of designing the system around an AI model: instructions, context, tools, permissions, hooks, skills, MCP/LSP navigation, memory, subagents, validation, and multi-session workflows. It is the shift from “prompt a coding agent” to “build the repeatable factory that makes agents useful.”

For the reference stack, this is the bridge between Hermes/GBrain as a chat-enabled assistant and Hermes/GBrain as a compounding personal AI infrastructure layer.

## Boundary

This page is the **harness/system-design discipline** for AI agents. It is broader than coding-agent workflow design and narrower than the operator's whole personal AI operating system. Keep it for the substrate around models: instructions, context construction, tool permissions, hooks, validators, logs, memory, model routing, and orchestration.

Related pages stay separate by layer:

- [Agentic Coding Systems](agentic-coding-systems.md) is the parent doctrine for coding-agent ecosystems and software factories.
- [Coding Agent Skill Systems](coding-agent-skill-systems.md) is the skill/playbook layer inside a harness.
- [Parallel Agentic Development](parallel-agentic-development.md) is one execution pattern that needs harness support.
- [Agentic Development Lifecycle](agentic-development-lifecycle.md) is the artifact/process sequence the harness should support.
- [Agent Work Packets](agent-work-packets.md) is one portable artifact type produced by the harness.

## Principles

- **The model is not the product.** The product is the model plus the harness that routes work, constrains behavior, validates output, and preserves learnings.
- **Every agent failure should improve the harness.** Missing context becomes rules; repeated workflows become skills; unsafe moves become hooks/permissions; bad validation becomes better checks. [Source: [2026 05 28 harness engineering](https://www.youtube.com/watch?v=ulNsa0sD8N0), 2026-05-28]
- **Progressive disclosure beats giant prompts.** Use lean root instructions, scoped directory rules, and task-specific skills instead of one bloated always-loaded context. [Source: [2026 05 21 anthropic agent harnesses](https://www.youtube.com/watch?v=efRIrLXoOVA), 2026-05-21]
- **Rules are conventions; skills are workflows.** Rules describe how the project works. Skills describe how to perform repeatable work.
- **Separate planning, implementation, validation, and review contexts** for non-trivial work.
- **Use deterministic nodes for deterministic tasks.** Tests, linting, context construction, PR creation, and safety checks should not rely on model memory when a script/hook can enforce them.
- **Promote harness changes like empirical state transitions.** A durable instruction, skill, middleware, or runtime-policy change should name the observed failure cluster, the edit surface, expected behavior change, regression risk, and before/after evidence; [Self-Harness](self-harness.md) is the clean research pattern for this. [Source: [Self-Harness](self-harness.md), 2026-06-08]
- **Design loops, not just prompts.** When work repeats, the harness should specify trigger, context, action authority, verifier, stop condition, durable state, budget, and proof bundle. [Loop Engineering](loop-engineering.md) is the repeatable-feedback-loop slice of harness engineering. [Source: [Loop Engineering source](https://www.youtube.com/watch?v=w285kJY3Xws), 2026-06-13]
- **Improve the controllable harness before chasing model releases.** Better models help, but the operator has more leverage over prompts, skills, tests, architecture, sandboxes, review flows, and work queues than over frontier-model timing. Codebase quality is also a token-spend lever: agent-friendly boundaries, tests, docs, and scripts let cheaper/weaker models succeed with less thrash. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]
- **Review the producing system, not only the produced diff.** Human review is harness observability: if a stronger model finds a bug, security issue, or architectural flaw, ask what check, test, skill, permission, or review artifact should have surfaced it earlier. Removing checkpoints requires sampled audits and feedback into the classifier/reviewer, not blind trust. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]
- **Optimize AX as part of DX.** Agent experience and developer experience overlap: clear scripts, narrow interfaces, typed boundaries, tests, docs, and small change surfaces make both humans and agents faster and safer. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]
- **Keep the coordinator responsive; delegate blocking work.** A top-level coordinator should dispatch execution to isolated workers instead of doing long-running work itself, leaving the control conversation available for new instructions, prioritization, and escalation. Expand autonomy gradually after observing routing quality and conflict behavior. [Source: [L8 Principal's Agentic Engineering Setup review](https://www.youtube.com/watch?v=8ZgpAXe5V5w), 2026-08-13]
- **Reconstruct original intent for pre-merge review, not just the diff.** An independent adversarial reviewer should compare the originating session or work packet, current diff, tests, and current base. Use a different reviewing model where practical to reduce correlated failure; auto-fix narrow technical defects, but escalate product-impacting choices. Kun Chen's reported catch rate is a self-measured source claim, not a general benchmark. [Source: [L8 Principal's Agentic Engineering Setup review](https://www.youtube.com/watch?v=8ZgpAXe5V5w), 2026-08-13; [First Mate](https://github.com/kunchenguid/firstmate) and [No Mistakes](https://github.com/kunchenguid/no-mistakes), checked 2026-08-13]
- **Treat requirements and validation as the new bottlenecks.** Once agents compress implementation time, the leverage shifts to better specs up front and stronger evaluation/review at the end; the harness is where those constraints become repeatable instead of chat-by-chat heroics. [Source: [2026 06 24 google just dropped a masterclass on agentic engineering](https://www.youtube.com/watch?v=zbmuiaPuiNM), 2026-06-25]
- **Manage static vs dynamic context deliberately.** Static context such as root rules and hard guardrails is reliable but expensive; dynamic context such as skills, local conventions, tool lookups, and task-specific docs should carry specialized knowledge through progressive disclosure. [Source: [2026 06 24 google just dropped a masterclass on agentic engineering](https://www.youtube.com/watch?v=zbmuiaPuiNM), 2026-06-25]
- **Treat the project artifact graph as a validated program.** Conventions, epics, specs, issues, checkpoints, and activity logs should have stable types and relationships; a bounded session-start index should expose where they live, while detailed context is retrieved progressively. Lint cross-artifact invariants so an authored status cannot silently disagree with derived reality—for example, a spec cannot be complete while required child work remains open. This is process-layer validation, not a reason to create a second tracker or clone a proprietary context CLI. [Source: [2026 08 20 75m founder reveals his agentic engineering setup](https://www.youtube.com/watch?v=QBfXiWvM0qc), promoted 2026-08-26]
- **Think in CapEx/OpEx, not prompt cleverness.** Vibe coding is low upfront cost but high operational cost when slop and rework burn tokens; agentic engineering has higher upfront harness cost but should lower repeated steering and validation cost once the workflow recurs. [Source: [2026 06 24 google just dropped a masterclass on agentic engineering](https://www.youtube.com/watch?v=zbmuiaPuiNM), 2026-06-25]
- **Make the harness composable rather than patchable, and make model-visible context reconstructable.** DeepSeek Harness is the production-scale worked example: every part is a plugin — model adapter, tool registry, session log, and the agent loop itself — registrations are reversible effects that unwind on unload, and a swappable capability is only complete when its Service Definition, Service Provider, and Consumer all exist, which is why one provider swap relocates Bash, PTY, and LSP together. Its strongest single invariant is **model-visible ⟺ logged**: anything reaching a model request must be reconstructable from the append-only session log, asserted at runtime, so replay, fork, resume, transcripts, and telemetry are projections of one stream instead of parallel bookkeeping. Its enforcement vocabulary is worth copying too — a sandbox reports `full` or `partial` completeness as a fact, and consumers needing an absolute boundary must reject `partial` rather than assume it. [Source: [deepseek ai  deepseek harness](../../intel/github-repos/repos/deepseek-ai--deepseek-harness.md), reviewed 2026-08-16]
- **Treat cache stability as a consequence of reconstructability, not a separate bag of tricks.** If the model-visible request is a pure projection of an append-only event log, replay and cache-prefix stability can share one invariant. When an auxiliary instruction can safely come last, preserve the already-seen system prompt, tool schemas, and conversation bytes, then append the new instruction instead of front-loading a fresh summarizer prompt. DeepSeek Harness's compaction fix is the concrete example: even unused tool definitions remain in place because removing them shifts the prefix. This pattern is conditional, not universal — it is attractive when the same provider/model can reuse the warm prefix, but may lose to a bounded cheap auxiliary summarizer that deliberately avoids replaying the full request. [Source: [2026 08 15 deepseek harness architecture insane software engineering behind it](https://www.youtube.com/watch?v=1NyOG9z9RT0), promoted 2026-08-17]
- **Make optimized state prove itself through an independent reconstruction path.** A cache, materialized view, or live in-memory request should not certify its own correctness. Rebuild the pending request from durable events in a fresh session/object, compare it with the optimized path, and keep at least one credentialed end-to-end check for the external property being claimed, such as positive cache-read tokens after the first request. This is the runtime analogue of reconstructing original intent for independent code review. [Source: [2026 08 15 deepseek harness architecture insane software engineering behind it](https://www.youtube.com/watch?v=1NyOG9z9RT0), promoted 2026-08-17]
- **Govern harness changes with a decision lifecycle and process-focused postmortems.** The same repo requires an Agent Note in every non-trivial change, files each under `proposed` / `implemented` / `rejected` / `archived` with a closed class set, freezes archived notes against edits, and reserves postmortems for bugs that were subtle, systemic, and costly to rediscover — asking why every safety net missed it rather than what the one-line fix was, and linking the guardrail the postmortem motivated. That is the human-and-agent counterpart to [Self-Harness](self-harness.md)'s promotion gate. [Source: [deepseek ai  deepseek harness](../../intel/github-repos/repos/deepseek-ai--deepseek-harness.md), reviewed 2026-08-16]
- **Treat the always-on layer as the behavioral and economic contract, not just capability scaffolding.** A task prompt is paid once; the system prompt, root instructions, and operational rules are multiplied over every turn, which makes them the correct home for register, output shape, scope boundaries, and token discipline. Three cheap mechanisms carry most of that value: an enumerated banned-phrase list instead of a generic "be concise"; **reference points**, short codes such as `D1`/`R1`/`F1` attached to decisions, risks, and findings so agent output becomes addressable in both directions; and **aliases**, always-resident micro-skills such as `SCR` or `FOC` that expand into a full instruction on sight. Two carve-outs the pattern needs and its source does not supply: reference points must not be injected into structured artifacts such as JSON, diffs, or commit messages, and aliases need collision-resistant tokens plus a "not inside a longer string" guard. The boundary against [skills](coding-agent-skill-systems.md) is cost-shaped — an alias is paid on every request and a skill is free until invoked, so alias pure output-shape transforms and leave anything needing procedure or tools as a skill. [Source: [System-prompt engineering source](https://www.youtube.com/watch?v=S_QdQ1G4GlU), promoted 2026-08-18]
- **Hand-author artifacts in proportion to how multiplicative they are, and change them by comparison rather than by feel.** Vibe-prompting a one-off task is cheap; the file that governs every future turn earns slow deliberate authorship. The matching method is an A/B harness: two agent lanes, the same task, one variable changed, re-run after each edit — the missing evaluation loop for system prompts, root rules, and trim passes, which are otherwise judged by reading them. The source's headline result (22s tuned versus 41s stock) is a **single anecdotal run on a non-deterministic system**, and its own counterexamples include 30s versus 30s; treat it as a reason to build the comparison harness, not as evidence to adopt the sections on faith. Always-on text also has an unstated cost — every section is paid in input tokens on every request, so it must buy behavior that recurs on every turn. [Source: [System-prompt engineering source](https://www.youtube.com/watch?v=S_QdQ1G4GlU), promoted 2026-08-18]
- **Test skill value and routing boundaries, not just skill syntax.** For a skill that matters, compare the same realistic prompts with and without the skill, preserve assertion evidence and timing, and test both should-trigger queries and plausible near-miss should-not-trigger queries. For substantial orchestrations, declare the topology and rerun contract up front: pipeline, fan-out/fan-in, expert pool, producer-reviewer, supervisor, or hierarchical delegation; file-based handoffs should distinguish initial, partial-rerun, and clean-rerun paths. `revfactory/harness` is a useful methodology source for these contracts, but its Claude Code Agent Teams dependency and absent CI/releases make it a pattern source rather than an install target. [Source: [revfactory  harness](../../intel/github-repos/repos/revfactory--harness.md), reviewed 2026-08-30]

## AI-layer checklist

- Root repo instructions: purpose, architecture, commands, conventions, gotchas.
- Subdirectory instructions for local patterns.
- Scoped skills for recurring workflows.
- Start hooks for dynamic context: git status, branch, recent commits, issue/task.
- Stop hooks for system evolution: rule updates, skill updates, validation gaps.
- LSP/MCP/code-search tools for large repositories.
- Subagents for exploration, independent validation, security review, and adversarial review.
- Artifact handoffs: plan, diff, validation report, review report, promotion notes.
- Agent-ergonomic tool interfaces: concise output, minimal default schemas, bounded detail with escape hatches, definitive empty/error states, and combined action-plus-observation where it removes predictable turns. [AXI](../../intel/github-repos/repos/kunchenguid--axi.md) is the canonical external reference and evaluation rubric; its project-run benchmarks are inspectable and promising, but transport choice remains task-shaped and performance should be reproduced on the operator's workflows before replacing useful MCP or native-tool surfaces. [Source: [kunchenguid  axi](../../intel/github-repos/repos/kunchenguid--axi.md), reviewed 2026-08-13]

## For the reference stack

Use harness engineering as a filter for AI-infra work: before building another custom surface, ask whether the missing leverage is actually a rule, skill, hook, script, workflow, validator, or tool permission boundary. Prefer stealing proven harnesses such as [Archon](https://github.com/coleam00/Archon) before building a custom orchestration layer.

The immediate loop-engineering application is not a generic orchestrator. Start with one small Hermes/GBrain with shared skills loop that is safe, visible, and useful: for example an AI-infra operator loop that inspects repo/project/brain signals, recommends one highest-leverage maintenance action, and stops with evidence unless the operator authorizes a bounded branch, issue, or note update. [Source: [Loop Engineering](loop-engineering.md), 2026-06-15]

## Related

- [Self-Harness](self-harness.md)
- [Loop Engineering](loop-engineering.md)
- [Agentic Coding Systems](agentic-coding-systems.md)
- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Archon](https://github.com/coleam00/Archon)
- [Parallel Agentic Development](parallel-agentic-development.md)
- [AI Dark Factory](ai-dark-factory.md)
