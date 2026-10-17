---
title: MCP and Context Tools
created: 2026-05-22
updated: 2026-05-22
type: concept
tags: [ai, mcp, context]
sources:
  - wiki/intel/github-repos/repos/upstash--context7.md
  - wiki/intel/github-repos/repos/punkpeye--awesome-mcp-servers.md
  - wiki/intel/github-repos/repos/CodeGraphContext--CodeGraphContext.md
status: active
---

# MCP and Context Tools

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis
MCP/context tools reduce hallucination and repeated context loading by giving agents current docs, tools, and structured project knowledge on demand. They are the tool-access layer beside [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md): memory answers what the user/project already knows, while MCP/context tools fetch or operate on the current world.

## Use cases

- Live library documentation via [context7](https://github.com/upstash/context7).
- Codebase graph context via CodeGraphContext-like tools and [graphify](https://github.com/Graphify-Labs/graphify).
- Tool access through MCP servers instead of custom one-off integrations.
- Brain/query access through [gbrain](https://github.com/garrytan/gbrain) once the vault is indexed.
- Agent workflows inside [Agentic Coding Systems](agentic-coding-systems.md) and [Coding Agent Skill Systems](coding-agent-skill-systems.md).

## Decision rule

Before building a custom integration, compare MCP servers or context tools that may cover the required capability (the original rule of thumb was 80% of the need). Custom glue is justified when it connects existing tools for a concrete workload and costs less to maintain than reimplementing commodity access.

## Related

- [context7](https://github.com/upstash/context7)
- [gbrain](https://github.com/garrytan/gbrain)
- [graphify](https://github.com/Graphify-Labs/graphify)
- [Agentic Coding Systems](agentic-coding-systems.md)
- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- personal AI operating system
- [LLM Wiki Pattern](llm-wiki-pattern.md)

## Source material

- `wiki/intel/github-repos/repos/upstash--context7.md`
- `wiki/intel/github-repos/repos/punkpeye--awesome-mcp-servers.md`
- `wiki/intel/github-repos/repos/CodeGraphContext--CodeGraphContext.md`
