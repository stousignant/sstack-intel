---
title: AI Memory and Knowledge Graphs
created: 2026-05-22
updated: 2026-06-07
type: concept
tags: [ai, memory, knowledge-graphs]
sources:
  - wiki/intel/github-repos/repos/garrytan--gbrain.md
  - wiki/intel/github-repos/repos/Graphify-Labs--graphify.md
  - wiki/intel/github-repos/repos/rohitg00--agentmemory.md
status: active
---

# AI Memory and Knowledge Graphs

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis
AI memory systems become more useful when they combine human-readable Markdown, retrieval, graph relationships, provenance, and recurring maintenance. The durable source of truth should remain readable notes; indexes, embeddings, and graphs are acceleration layers.

This page is the **parent use-case and principles page** for the memory / knowledge graph / RAG cluster. It asks what a memory system should optimize for, and how durable Markdown, GBrain, graph tooling, and maintenance loops can fit together.

## Cluster disposition — 2026-06-07

| Page | Disposition | Boundary |
|---|---|---|
| [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md) | **keep as parent principles / use-case page** | Owns the full-stack memory-system stance: durable Markdown truth, retrieval/graph acceleration, provenance, and maintenance loops. |
| [Agent Memory Architecture](agent-memory-architecture.md) | **keep as architecture page** | Owns the layer model: raw evidence, curated wiki, graph/search indexes, task execution state, and transient chat context. |
| [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md) | **keep as comparison / decision page** | Owns the trade-off between chunk RAG, knowledge graphs, and compiled wiki workflows. |

Default: **clarify, do not merge.** These pages are adjacent layers, not duplicates: one says what memory should do, one says how memory is layered, and one explains retrieval/graph trade-offs.

## Principles

- Markdown remains a durable, human-readable source of truth for a personal assistant stack.
- [LLM Wiki Pattern](llm-wiki-pattern.md) creates the curated knowledge layer before retrieval systems index it.
- [gbrain](https://github.com/garrytan/gbrain) is the local query/index/entity-graph layer over the vault.
- wikic is the deterministic compiler/doctor and vault-policy substrate that proves the Markdown graph is structurally healthy before GBrain is asked to retrieve from it.
- [graphify](https://github.com/Graphify-Labs/graphify) and [llm wiki agent](https://github.com/SamurAIGPT/llm-wiki-agent) graph reports can diagnose isolated pages and weak communities, but they are not the canonical memory store.
- [Agent Memory Architecture](agent-memory-architecture.md) separates raw evidence, synthesized truth, executable task state, and transient chat context so the system does not confuse notes with obligations.
- [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md) is the decision lens when choosing whether a new workflow needs chunk retrieval, typed links/entities, or a compiled wiki page.

## Reuse candidates

- [gbrain](https://github.com/garrytan/gbrain) for hybrid search, graph extraction, entity/fact recall, and brain-first query workflows.
- wikic for deterministic graph health, candidate review, and summary reports; downstream sync remains GBrain/MCP workflow policy.
- [graphify](https://github.com/Graphify-Labs/graphify) for graph visualization and code/doc mapping experiments.
- [llm wiki agent](https://github.com/SamurAIGPT/llm-wiki-agent) for external agent-curated wiki maintenance ideas, not as a canonical corpus owner unless that role is deliberately assigned.
- Agent-memory projects as references before building custom memory layers.

## Open questions

- Which generated graph artifacts belong in the Git vault versus disposable pilot workspaces?
- Should GBrain index every raw file or focus ranking on curated pages first?
- How much automated ingestion is safe before source quality and schema drift become a problem?
- What belongs in durable memory versus GitHub Issues/Projects execution state versus transient Hermes session context?

## Related

- [Agent Memory Architecture](agent-memory-architecture.md)
- [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md)
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- personal AI operating system
- [MCP and Context Tools](mcp-context-tools.md)
- [gbrain](https://github.com/garrytan/gbrain)
- wikic
- [graphify](https://github.com/Graphify-Labs/graphify)
- cleanup/source-layer policy

## Source material

- `wiki/intel/github-repos/repos/garrytan--gbrain.md`
- `wiki/intel/github-repos/repos/Graphify-Labs--graphify.md`
- `wiki/intel/github-repos/repos/rohitg00--agentmemory.md`
