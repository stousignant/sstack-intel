---
title: Coding Agent Skill Systems
created: 2026-05-22
updated: 2026-09-16
type: concept
tags: [ai, agents, software-engineering, skills]
sources:
  - wiki/concepts/ai-engineering/agentic-coding-systems.md
  - wiki/intel/github-repos/repos/obra--superpowers.md
  - wiki/intel/github-repos/repos/addyosmani--agent-skills.md
  - https://github.com/garrytan/gbrain/blob/master/docs%2Fethos%2FTHIN_HARNESS_FAT_SKILLS.md
  - https://x.com/garrytan/status/2053127519872614419
  - https://www.youtube.com/watch?v=PIdETjcXNIk
  - https://www.youtube.com/watch?v=yBcmIoA-vGs
  - https://www.youtube.com/watch?v=M30gp1315Y4
  - https://www.youtube.com/watch?v=Qn2c_U-cWQs
  - https://www.youtube.com/watch?v=EJyuu6zlQCg
  - https://www.youtube.com/watch?v=dtAJ2dOd3ko
  - https://www.youtube.com/watch?v=mh5XZ-L5SFQ
  - https://www.youtube.com/watch?v=Ah9p7v7nJWg
  - https://steipete.me/posts/just-talk-to-it
  - https://steipete.me/posts/2025/optimal-ai-development-workflow
  - https://github.com/steipete/agent-scripts
  - https://www.youtube.com/watch?v=nQwJVHCtDDY
  - https://www.youtube.com/watch?v=zbmuiaPuiNM
  - wiki/concepts/ai-engineering/skill-graphs.md
  - https://x.com/akshay_pachaar/status/2024848778415755327
  - wiki/intel/github-repos/repos/agenticnotetaking--arscontexta.md
status: active
---

# Coding Agent Skill Systems

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis
Skill systems package repeatable agent behavior into durable, reviewable procedures. They turn agentic coding from ad-hoc prompting into an operating model with triggers, workflows, checks, and known pitfalls.

Garry Tan's "thin harness, fat skills" framing sharpens the rule: put reusable judgment and process in Markdown skills, keep the harness small, and route tasks to the right skill/context with resolvers. The skill is closer to a method call than a loose prompt: the process stays stable while the user supplies different task parameters. [Source: [Thin Harness, Fat Skills](thin-harness-fat-skills.md), 2026-04-11]

His "Meta-Meta-Prompting" article adds the compounding loop: do a useful workflow manually, inspect the output, skillify the repeatable pattern, wire it into the resolver, and improve the skill when quality issues appear. [Source: [Meta-Meta-Prompting](meta-meta-prompting.md), 2026-05-09]

## Boundary

This page is a **child concept** under [Agentic Coding Systems](agentic-coding-systems.md) and a component of [Harness Engineering](harness-engineering.md). It should stay focused on skills, playbooks, resolver behavior, verification loops, and skill maintenance.

Do not make this page carry responsibilities that belong elsewhere:

- project-wide architecture and permission surfaces belong on [Harness Engineering](harness-engineering.md);
- full delivery sequencing belongs on [Agentic Development Lifecycle](agentic-development-lifecycle.md);
- multi-worktree execution belongs on [Parallel Agentic Development](parallel-agentic-development.md);
- portable handoffs belong on [Agent Work Packets](agent-work-packets.md);
- hard security boundaries belong in tools, sandboxes, allowlists, and permissions, not in skills alone.

## Why it matters

For [Agentic Coding Systems](agentic-coding-systems.md), skills are the bridge between general-purpose models and reliable project-specific work. They also fit personal AI operating system because they let the operator reuse community workflows while customizing only the parts that matter.

## Design principles

- Use skills for repeated workflows, not one-off facts.
- Keep project conventions in repository instructions when possible.
- Pair skill execution with verification: tests, lint, graph reports, or review.
- Use [MCP and Context Tools](mcp-context-tools.md) like [context7](https://github.com/upstash/context7) when a skill depends on current external APIs.
- Record durable outcomes in the wiki through [LLM Wiki Pattern](llm-wiki-pattern.md) when the workflow changes the brain.
- Prefer thin global instructions plus good resolver descriptions over one giant always-loaded prompt; repeated workflows should graduate into skills after a few inspected manual examples. [Source: [Thin Harness, Fat Skills](thin-harness-fat-skills.md), 2026-04-11]
- Treat skill maintenance as the compounding unit: a fix to one focused skill should improve every workflow that composes it. [Source: [Meta-Meta-Prompting](meta-meta-prompting.md), 2026-05-09]

## Skill portability and peer agents

A useful skill-system pattern from the Pi-to-Pi video is **skill parity by focused peers**: one agent owns the existing skill/provider context, another owns the new provider implementation, and they communicate only when parity questions arise. This avoids stuffing both providers, both docs sets, and all implementation details into one context window. [Source: [Pi-to-Pi source](https://www.youtube.com/watch?v=PIdETjcXNIk), 2026-05-29]

For the reference stack, this suggests a reusable workflow: when porting a skill from service A to service B, create a feature inventory for A, have the B-focused agent drive implementation, then use the A-focused agent as a verifier for missing features, semantic mismatches, and unsafe assumptions. The output should still land as reviewed Markdown skills and proof bundles, not hidden chat lore.


## Skills, expertise files, and safety boundaries

IndyDevDan’s multi-agent team pattern reframes skills as part of an **agent expertise substrate**: role prompts, shared skills, domain notes, session logs, and persistent mental models let specialist agents compound instead of starting cold every time. This is valuable for Hermes only if expertise files stay inspectable and curated; stale mental models are hidden state, not magic. [Source: [One Agent Is Not Enough review](https://www.youtube.com/watch?v=M30gp1315Y4), 2026-05-29]

The Bash-safety video adds the counterweight: skills and prompts are **behavioral controls**, not security boundaries. A skill that says “do not delete production data” is useful, but the hard boundary must come from tool permissions, sandboxing, allowlists, or explicit tools. Treat skills as guidance layered on top of capability control. [Source: [Delete the Bash Tool review](https://www.youtube.com/watch?v=yBcmIoA-vGs), 2026-05-29]


## Skills vs customization

The Hermes/OpenClaw interview adds a useful constraint: customization is not the skill; useful work is the skill. Skills should capture repeated leverage after the workflow has proven value, not become a hobby layer for endlessly tuning the agent. A good skill turns a repeated manual pattern into inspectable operating doctrine with triggers, steps, checks, and pitfalls. [Source: [Hermes Agent: The New OpenClaw? review](https://www.youtube.com/watch?v=Qn2c_U-cWQs), 2026-05-31]

For recurring work, the first routing question is whether the solution belongs in a script, a cron job, or a skill. Deterministic mechanics should usually become code or scheduled jobs; judgment, triage, domain heuristics, and review protocols belong in skills. [Source: [Hermes Agent: The New OpenClaw? transcript](https://www.youtube.com/watch?v=Qn2c_U-cWQs), 2026-05-31]

## Harness engineering update

Cole Medin's harness-engineering framing clarifies the boundary: skills are one part of a larger [harness](harness-engineering.md), alongside rules, hooks, MCP/LSP tools, worktrees, validators, logs, and orchestration. Skills should not carry every responsibility. Use skills for repeatable judgment/workflows; use hooks/scripts for deterministic checks; use tool permissions for hard safety boundaries; use scoped repo instructions for project conventions. [Source: [Harness Engineering review](https://www.youtube.com/watch?v=ulNsa0sD8N0), 2026-05-28]

For large codebases, prefer progressive disclosure: lean root instructions, directory-specific rules, and path/task-scoped skills. A thousand-line always-loaded skill/rule file is usually a context-management failure, not maturity. [Source: [Anthropic harnesses review](https://www.youtube.com/watch?v=efRIrLXoOVA), 2026-05-21]

Google's AI-SDLC framing, via Cole Medin, makes the same point economically: static context is reliable but expensive, while dynamic skills let a lightweight generalist agent become a temporary planner, reviewer, implementer, or domain specialist on demand. Treat skills as progressive disclosure for specialized process knowledge, not as a dumping ground for every fact the agent might someday need. [Source: [2026 06 24 google just dropped a masterclass on agentic engineering](https://www.youtube.com/watch?v=zbmuiaPuiNM), 2026-06-25]


## Matt Pocock / compact engineering skills

Matt Pocock's skill corpus adds a grounded implementation layer: useful skills are compact process capsules, not giant prompts. The core set worth mining into owned skill repository is `grill-me` for design-tree interviewing, PRD writing, PRD-to-issues with vertical slices and blockers, agentic TDD, architecture-improvement passes, `/handoff`, and ambitious structural review. [Source: [2026 03 16 5 claude code skills i use every single day](https://www.youtube.com/watch?v=EJyuu6zlQCg), 2026-03-16]

Two design rules matter most for Hermes: first, agents should inspect the repo before asking the human for facts that are locally retrievable; second, skills should create or update artifacts that survive context resets — PRDs, issues, handoffs, review notes, and QA plans. [Source: [2026 05 21 handoff is my new favourite skill](https://www.youtube.com/watch?v=dtAJ2dOd3ko), 2026-05-21]

For review, add an ambition dial. Standard review catches correctness and regression issues; thermonuclear/structural review is allowed to propose decompositions, type-boundary fixes, canonical helper reuse, and agent-navigable architecture improvements. False positives are acceptable when labeled; missed structural opportunities are more costly. [Source: [2026 05 28 can cursors hardcore review skill stop the slop](https://www.youtube.com/watch?v=mh5XZ-L5SFQ), 2026-05-28]

## Procedure skills, ability skills, and stateful workspaces

Matt’s 2026 workflow interview sharpens the most important operating distinction: **procedure skills** are invoked deliberately by the human, while **ability skills** sit ambiently in the model’s option space. For high-stakes Reference-stack work, default to procedure skills because they preserve human routing/control and avoid leaking many skill descriptions into context. Ability-style skills should earn their place through observed failures, not collection-building. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]

A practical maintenance loop follows from that: periodically test agents from a near-blank slate, observe what they actually fail to do, then add back only the smallest skill/plugin/MCP surface that fixes a real repeated failure. “More skills” is not maturity if it bloats context or hides control flow. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]

The `teach` demo also expands the definition of a skill: a strong skill can be a **stateful local workspace**, creating mission files, lesson artifacts, records, quizzes, and checkpoints that survive context resets. That pattern is directly reusable for shared skills that need durable learning/work state rather than one-shot prompt behavior. [Source: [2026 06 18 matt pococks agentic engineering workflow just copy him](https://www.youtube.com/watch?v=nQwJVHCtDDY), 2026-06-23]

## Peter Steinberger / shared agent operations

Peter Steinberger's `agent-scripts` repo is a concrete example of skill systems as maintainer infrastructure rather than prompt decoration. The useful pattern is a canonical shared rules/skills/scripts repo, downstream pointer files instead of copy-pasted instructions, small validation hooks, short skill descriptions for routing, helper scripts under the owning skill, and a maintainer-orchestrator skill that encodes queue classification, permission boundaries, worker monitoring, and decision-ready owner asks. [Source: [Peter Steinberger’s agent-scripts](https://github.com/steipete/agent-scripts), 2026-06-14]

For Hermes/owned skill repository, steal the contract, not the personal corpus: centralize reusable doctrine, keep repo-specific rules local, validate skills near commit boundaries, and treat five-minute polling as a status/orchestration loop that surfaces blockers and prepared decisions — not as blanket permission for agents to mutate, merge, or release. [Source: [steipete agent scripts skill distillation 2026 06 13](https://github.com/steipete/agent-scripts), 2026-06-13]

## Upstream skill overlays and drift

The agent-skills ecosystem currently supports skill scopes, plugin namespacing, visibility controls, local skill folders, and plugin distribution, but not a mature first-class “inherit upstream skill and override section” model. The safe operating pattern is therefore: keep upstream/plugin skills pristine, put local behavior in companion/replacement skills, and preserve unavoidable direct edits as explicit patch records rather than invisible file mutations. [Source: [Agent Skill Overlays and Upstream Drift](agent-skill-overlays-and-upstream-drift.md), 2026-06-15]

For an owned skill repository with Hermes, upstream-looking skill files should be treated as installed/runtime artifacts, not the durable surface for operator-specific policy. Durable local doctrine belongs in `<owned-prefix>-*` overlays with `metadata.owner.overlay_for` / `overlay_type`; small direct deltas belong in `patches/hermes-skills/`; larger divergence should be an explicit fork/vendor decision. [Source: [Agent Skill Overlays and Upstream Drift](agent-skill-overlays-and-upstream-drift.md), 2026-06-15]

## Skill graphs and the knowledge/procedure boundary

The “skill graph” framing is useful when it means progressive disclosure across a large, non-linear domain, but it should not collapse knowledge nodes and operating procedures into one undifferentiated graph. The default remains one stable root skill with directly linked references; a full graph should be exceptional and must prove root triggering, path selection, required-node coverage, safe stopping, and task success against that shallow baseline. [Source: [Skill Graphs](skill-graphs.md), 2026-09-16]

For the reference stack, skills remain the procedural control plane while the second-brain/GBrain holds the large knowledge graph and Wikic verifies Markdown integrity. Ars Contexta is a strong pattern source for maps, contextual links, descriptions, and graph maintenance, but its implementation is a knowledge graph operated by skills—not a native dependency graph among skills. [Source: [agenticnotetaking  arscontexta](../../intel/github-repos/repos/agenticnotetaking--arscontexta.md), 2026-09-16]

## Related

- [Agentic Coding Systems](agentic-coding-systems.md)
- [Agent Skill Overlays and Upstream Drift](agent-skill-overlays-and-upstream-drift.md)
- [Skill Graphs](skill-graphs.md)
- [MCP and Context Tools](mcp-context-tools.md)
- [context7](https://github.com/upstash/context7)
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- personal AI operating system
- software engineering career
