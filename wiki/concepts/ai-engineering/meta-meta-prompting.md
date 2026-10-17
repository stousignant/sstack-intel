---
title: Meta-Meta-Prompting
created: 2026-05-23
updated: 2026-05-23
type: concept
tags: [ai, agents, skills, personal-infrastructure]
sources:
  - https://x.com/garrytan/status/2053127519872614419
status: active
---

# Meta-Meta-Prompting

> Reference-stack lens: [AI engineering](index.md).

## Definition

Meta-meta-prompting is the pattern of using an AI system to improve the prompts, skills, context pages, and operating procedures that future AI runs will consume. Instead of only asking an agent to complete a task, the system captures the successful method so future agents start one level smarter.

## When this pattern is useful

For a Hermes-based reference stack, one compounding loop is:

1. Use Hermes to solve or inspect a concrete workflow.
2. Extract durable procedure into maintained skills or second-brain pages.
3. Connect those artifacts through [LLM Wiki Pattern](llm-wiki-pattern.md) links and [gbrain](https://github.com/garrytan/gbrain) indexing.
4. Let later Hermes runs load the relevant skill/page before acting.

This keeps the harness thin while placing reusable judgment in [Coding Agent Skill Systems](coding-agent-skill-systems.md), knowledge pages, and verification checklists.

## Practical rule

Do not skillify everything. Capture workflows only when they are repeated, subtle, easy to botch, or expensive to rediscover. One-off task progress belongs in logs or project notes, not assistant memory.

## Related

- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Agent Memory Architecture](agent-memory-architecture.md)
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- personal AI operating system
- [gbrain](https://github.com/garrytan/gbrain)
