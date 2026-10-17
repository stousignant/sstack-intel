---
title: LLM Wiki Pattern
created: 2026-05-22
updated: 2026-06-07
type: concept
tags:
  - llm-wiki
  - ai
  - knowledge-management
  - second-brain
  - knowledge-compiler
sources:
  - https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
  - https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2
  - wiki/intel/github-repos/repos/nashsu--llm_wiki.md
  - wiki/intel/github-repos/repos/SamurAIGPT--llm-wiki-agent.md
  - wiki/intel/github-repos/repos/atomicstrata--llm-wiki-compiler.md
topic: llm-wiki
role: core-concept
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
---

# LLM Wiki Pattern

> Reference-stack lens: [AI engineering](index.md).

> Concept hub: [AI engineering](index.md)

## Working synthesis

The LLM Wiki pattern compiles raw sources into durable, interlinked Markdown so future questions start from accumulated synthesis instead of rediscovering context. It is the "compiled knowledge" alternative to vanilla RAG: raw sources remain immutable, but an LLM incrementally maintains a human-readable wiki of source summaries, entities, concepts, contradictions, comparisons, and synthesis pages.

For the reviewed Hermes/GBrain reference stack, the pattern should sit between ingestion channels — GitHub repos, articles, YouTube, PDFs, Discord/session summaries — and query layers like [gbrain](https://github.com/garrytan/gbrain). Hermes proposes reviewed source-to-synthesis edits; domain-local routers expose curated knowledge before GBrain indexes it. Historical folder recipes are not current filing policy.

## Cluster disposition — 2026-06-07

This page is the **canonical concept** for the LLM-wiki pattern in the reviewed reference collection. Keep it as the high-level architecture: raw and source evidence becomes curated, linked, human-readable Markdown before retrieval or graph tooling is expected to answer questions well.

Boundaries:

- Archived implementation designs are lineage, not a separate compiler to build by default; use the existing deterministic integrity layer.
- [LLM Wiki v2 memory lifecycle](llm-wiki-v2-memory-lifecycle.md) is a child/reference concept about confidence, supersession, decay, typed links, and automation once the wiki scales.
- wikic is the deterministic compiler/doctor and vault-policy substrate. Judgment-heavy advice remains in Hermes/shared skills.
- [gbrain](https://github.com/garrytan/gbrain) is the AI/index/query/graph layer over the canonical Markdown vault.
- [llm wiki agent](https://github.com/SamurAIGPT/llm-wiki-agent) and [llm wiki compiler](https://github.com/atomicstrata/llm-wiki-compiler) are external reference/sandbox tools, not active canonical owners of this vault.

So the default disposition is **keep, clarify, and cross-link** rather than merge/delete.

## Core architecture

Karpathy's original pattern has three layers:

1. **Raw sources** — immutable evidence: articles, papers, transcripts, repos, PDFs, images, logs.
2. **The wiki** — LLM-generated Markdown pages: summaries, entities, concepts, comparisons, overview, synthesis.
3. **The schema** — instructions such as `AGENTS.md`, `CLAUDE.md`, or a skill that tells the LLM how to ingest, query, lint, update, cite, and maintain the wiki.

The schema is not decoration. It is the control surface that turns a generic model into a disciplined wiki maintainer.

## Operations

- **Ingest:** read one or more sources, preserve provenance, summarize source, update relevant entity/concept pages, update index/log, flag contradictions.
- **Query:** search curated wiki first, then synthesize answers with citations. Valuable answers can be crystallized back into the wiki.
- **Lint:** periodically check contradictions, stale claims, missing links, orphan pages, duplicate entities, weak pages, source gaps, and broken citations.

## Design rules

- Keep raw sources immutable in source-specific `raw/` folders when possible.
- Do not make every source file a perfect wiki page. Raw files are evidence; curated pages are the knowledge product.
- Preserve source URLs and local raw paths in page frontmatter or evidence sections.
- Prefer incremental compounding over one-shot summaries.
- Use deterministic validators for LLM-generated writes: path safety, Markdown/frontmatter sanity, duplicate detection, and git diff review.
- Use [LLM Wiki v2 memory lifecycle](llm-wiki-v2-memory-lifecycle.md) for confidence, supersession, decay, and consolidation tiers as the wiki scales.
- Use [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md) / [gbrain](https://github.com/garrytan/gbrain) as retrieval and graph layers after the human-readable wiki exists.

## Reference-stack implementation boundary

Use the Markdown/Git vault as canonical knowledge, GBrain as the derived index/query layer, and Hermes as the agent/runtime layer. Keep ingestion, extraction, proposed edits, deterministic validation, versioned publication, and downstream indexing separate. Scheduling or live sync requires its own authority; a concept recommendation does not activate it.

## Build vs adopt: capability gap and integration cost

Default recommendation: **do not build a big custom app yet.** First compare and pilot existing projects:

- [nashsu  llm_wiki](../../intel/github-repos/repos/nashsu--llm_wiki.md) — strongest desktop implementation checked so far; great pattern source, GPL-3.0 caution.
- `SamurAIGPT/llm-wiki-agent` — agent-first workflow candidate.
- `atomicstrata/llm-wiki-compiler` — compiler framing; the pattern need not require Copilot.
- `AgriciDaniel/claude-obsidian` — Claude + Obsidian companion; worth inspecting for vault-native UX.
- `kytmanov/obsidian-llm-wiki-local` — local/Ollama/Obsidian angle.

Build only after confirming which pieces existing tools fail to cover for Hermes/GBrain-native usage.

## Related

- [LLM Wiki v2 memory lifecycle](llm-wiki-v2-memory-lifecycle.md)
- wikic
- [nashsu  llm_wiki](../../intel/github-repos/repos/nashsu--llm_wiki.md)
- personal AI operating system
- [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md)
- [Agent Memory Architecture](agent-memory-architecture.md)
- [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md)
- [llm wiki agent](https://github.com/SamurAIGPT/llm-wiki-agent)
- [llm wiki compiler](https://github.com/atomicstrata/llm-wiki-compiler)
- [markit](https://github.com/Michaelliv/markit)
- [gbrain](https://github.com/garrytan/gbrain)
- [graphify](https://github.com/Graphify-Labs/graphify)
- cleanup/source-layer policy

## Source material

- Karpathy original raw copy: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- Rohit Garg v2 raw copy: https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2
- Deep repo analysis: `wiki/intel/github-repos/repos/nashsu--llm_wiki.md`

## Source promotion notes — 2026-05-30

The original LLM Wiki idea and Rohit Garg’s v2 production lessons were synthesized here on 2026-05-30: compile messy sources into interlinked Markdown; prevent rot with explicit ingestion, deduplication, linking, and maintenance workflows. The operational implication is a reviewed source → synthesis → deterministic graph verification → downstream index loop, not merely raw capture storage.
