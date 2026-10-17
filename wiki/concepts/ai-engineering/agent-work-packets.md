---
title: Agent Work Packets
created: 2026-06-03
updated: 2026-09-29
type: concept
tags: [ai, agents, context-engineering, workflows]
sources:
  - https://www.youtube.com/watch?v=dtAJ2dOd3ko
  - https://www.youtube.com/watch?v=E5-QK3CDVQM
status: active
---

# Agent Work Packets

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

An agent work packet is a scoped, portable artifact that lets another agent or session continue a bounded task without inheriting the whole parent context. Matt Pocock's `/handoff` skill is the simplest form: a Markdown packet for a fresh session. Sandcastle generalizes the idea into code: backlog issue + prompt + sandbox + branch + role. [Sources: [2026 05 21 handoff is my new favourite skill](https://www.youtube.com/watch?v=dtAJ2dOd3ko), [2026 04 30 i open sourced my own afk software factory](https://www.youtube.com/watch?v=E5-QK3CDVQM)]

Packets describe the **input and handoff contract** for a worker; proof-of-work describes what its run returns. [OpenAI Symphony](../../intel/github-repos/repos/openai--symphony.md) is a concrete orchestration reference for collecting CI, PR/review, and other run evidence. Keep that output evidence linked to the packet's success criteria rather than treating a completed run as proof by itself.

## Boundary

This page is the **portable context artifact** pattern. It should not become a backlog, project plan, or lifecycle page. A work packet is useful when another agent/session needs a bounded slice of context, success criteria, non-goals, pointers, and a return contract.

Related boundaries:

- [Agentic Development Lifecycle](agentic-development-lifecycle.md) says when a packet is needed.
- [Parallel Agentic Development](parallel-agentic-development.md) uses one packet per isolated stream.
- [Coding Agent Skill Systems](coding-agent-skill-systems.md) may define packet templates and generation/review procedures.
- [Harness Engineering](harness-engineering.md) decides how packets are produced, logged, verified, and cleaned up.

## Packet fields

- Parent goal and child goal.
- Current state and relevant decisions.
- Pointers to artifacts, files, issues, branches, transcripts, or logs.
- Non-goals and boundaries.
- Suggested skills/tools.
- Known risks, secrets to avoid, and permission constraints.
- Expected return contract: patch, review, prototype, research summary, issue list, or handoff-back.

## When to use

- The current session is getting too large or off-scope.
- A child agent should do research, prototyping, implementation, review, or QA independently.
- Different agents/tools need to interoperate through Markdown rather than hidden chat state.
- A backlog item needs to become executable by an AFK or sandboxed agent.

## Design rules

- Compact the relevant slice; do not duplicate the whole world.
- Prefer pointers over pasted artifacts when the next agent can read the source.
- Redact secrets and avoid ambient credentials.
- Include a concrete next action and a clear done condition.
- Make packets disposable unless they become durable source/provenance.

## Related

- [Agentic Coding Systems](agentic-coding-systems.md)
- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Agentic Development Lifecycle](agentic-development-lifecycle.md)
- [sandcastle](https://www.youtube.com/watch?v=E5-QK3CDVQM)
