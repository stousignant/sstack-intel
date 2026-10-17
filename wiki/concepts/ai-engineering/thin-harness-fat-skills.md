---
title: Thin Harness, Fat Skills
created: 2026-05-23
updated: 2026-08-18
type: concept
tags: [ai, agents, skills, personal-infrastructure]
sources:
  - https://github.com/garrytan/gbrain/blob/master/docs%2Fethos%2FTHIN_HARNESS_FAT_SKILLS.md
  - https://www.youtube.com/watch?v=S_QdQ1G4GlU
status: active
---

# Thin Harness, Fat Skills

> Reference-stack lens: [AI engineering](index.md).

## Definition

Thin harness, fat skills is the architecture pattern of keeping the agent runtime/harness small while moving reusable judgment, procedures, and domain conventions into maintained skill files and source-backed knowledge pages.

## When this pattern is useful

In the documented Hermes-based stack, the harness combines [Hermes Agent](https://github.com/NousResearch/hermes-agent) with capabilities such as terminal, files, cron, delegation, and MCP. Reusable procedures and knowledge can live in:

- Hermes skills for repeatable procedures and verification loops.
- The second-brain wiki for source-backed concepts, tool profiles, and project context.
- [gbrain](https://github.com/garrytan/gbrain) as the query/index layer over that durable corpus.

This avoids giant always-loaded prompts and makes improvements composable: fixing one skill or page should improve every future workflow that uses it.

## Operating rule

Use deterministic CLI/tooling for lookup, sync, graph checks, status, and validation when those operations have repeatable inputs and outputs. Use skills and knowledge pages for adaptive decisions such as what to ingest, synthesize, where to file it, and how to judge quality.

## Refinement: thin the capability scaffolding, not the behavioral contract

"Thin" applies to one axis, not two. What the harness should stop carrying is **capability scaffolding** — telling a competent model how to read a file, how to search, how to sequence obvious steps. What it must keep carrying is the **behavioral and economic contract**: register, output shape, scope boundaries, banned phrasing, and token discipline. That text is the highest-multiplier text in the stack because it is paid on every turn, and no skill can supply it, since a skill is invisible until it is invoked.

Vendors shrinking their own shipped system prompts is evidence about the first axis only. Base capability improved, so the scaffolding became dead weight; that says nothing about whether *your* always-on rules should be thin. If you want specific behavior or specific token economics rather than default behavior, you still have to write it down in the multiplied layer. [Source: [System-prompt engineering source](https://www.youtube.com/watch?v=S_QdQ1G4GlU), promoted 2026-08-18]

Hold this as a tension, not a reversal. The pattern stands — judgment, procedures, and domain conventions still belong in maintained skills and source-backed pages, and giant always-loaded prompts are still the failure mode. The refinement is that a small always-on behavioral core is not prompt bloat, and the test for admitting a rule there is whether it changes behavior on effectively every turn. Anything task-shaped stays fat, discoverable, and out of the harness. See [Harness Engineering](harness-engineering.md) for the mechanisms and the A/B method for evaluating such changes.

## Related

- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Meta-Meta-Prompting](meta-meta-prompting.md)
- [Agent Memory Architecture](agent-memory-architecture.md)
- [Hermes Agent](https://github.com/NousResearch/hermes-agent)
- [gbrain](https://github.com/garrytan/gbrain)
