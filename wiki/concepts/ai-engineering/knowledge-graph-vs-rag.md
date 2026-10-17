---
title: Knowledge Graph vs RAG
created: 2026-05-22
updated: 2026-09-07
type: concept
tags: [ai, rag, knowledge-graphs, second-brain]
sources:
  - wiki/concepts/ai-engineering/ai-memory-and-knowledge-graphs.md
  - wiki/concepts/ai-engineering/llm-wiki-pattern.md
  - https://github.com/garrytan/gbrain
status: active
---

# Knowledge Graph vs RAG

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis
RAG retrieves chunks at query time; a wiki/graph compiles relationships ahead of time. For the reviewed second-brain architecture, the best approach is usually not either/or: use [LLM Wiki Pattern](llm-wiki-pattern.md) to create human-readable synthesis, then use [gbrain](https://github.com/garrytan/gbrain) and graph tooling to retrieve and traverse it.

This page is the **comparison and decision page** for the memory / knowledge graph / RAG cluster. It should stay narrower than [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md) and more tactical than [Agent Memory Architecture](agent-memory-architecture.md).

## Cluster disposition — 2026-06-07

Disposition: **keep as comparison / decision lens.** Do not merge into the architecture page. Use this comparison when a workload needs better chunk retrieval, a typed graph/entity model, or a compiled wiki/synthesis pass.

## Tradeoffs

| Approach | Strength | Weakness | Best fit |
|---|---|---|---|
| Chunk RAG | Fast to index messy corpora; cheap first-pass recall | Re-derives context each query; weak provenance, weak boundaries, and weak relationship memory | Search raw and source-heavy material and find candidate evidence. |
| Knowledge graph | Captures entities, typed relationships, backlinks, and traversal paths | Requires curation, schema discipline, link maintenance, and conflict handling | Represent wiki/entities/people/companies/wiki/tools/concepts, timeline relationships, and durable claims. |
| LLM wiki / compiled Markdown | Human-readable, reviewable, compounding synthesis | Needs agent discipline, source boundaries, and deterministic validation | Turn raw sources into durable pages before relying on retrieval. |
| Hybrid GBrain layer | Combines keyword/vector recall, graph extraction, and fact memory over Markdown | Quality is capped by source/vault quality; raw dumps can still swamp useful retrieval | Query the curated vault, surface facts/entities, and route agents to the right page. |

## Decision rule

- If the problem is **finding evidence**, use RAG/hybrid search through [gbrain](https://github.com/garrytan/gbrain).
- If the problem is **remembering relationships**, add explicit links/entities/timeline conventions and verify with wikic plus downstream GBrain extraction.
- If the problem is **understanding**, write or improve a curated wiki/concept/tool/project page through [LLM Wiki Pattern](llm-wiki-pattern.md).
- If the problem is **execution state**, do not encode it as memory: route it to GitHub Issues/Projects. Use owned specification bridge for deeper planning; Retired planning systems are history, not active routing.

## Recommendation for a curated Markdown brain

Start with curated Markdown and explicit Obsidian-style links. Add [gbrain](https://github.com/garrytan/gbrain) for hybrid search and graph extraction after the wiki spine is dense enough. Use `wikic --profile vault-policy` as the structural acceptance gate. Use [graphify](https://github.com/Graphify-Labs/graphify) and [llm wiki agent](https://github.com/SamurAIGPT/llm-wiki-agent) graph reports to diagnose weak connectivity, not as replacements for clear concept pages.

## Related

- [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md)
- [Agent Memory Architecture](agent-memory-architecture.md)
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- [gbrain](https://github.com/garrytan/gbrain)
- wikic
- [graphify](https://github.com/Graphify-Labs/graphify)
- personal AI operating system
