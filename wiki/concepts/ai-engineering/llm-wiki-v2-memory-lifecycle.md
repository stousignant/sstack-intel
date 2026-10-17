---
title: LLM Wiki v2 memory lifecycle
aliases:
  - LLM Wiki v2
  - memory lifecycle for LLM Wiki
source: https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2
type: concept
topics: [llm-wiki, memory, knowledge-graph, lifecycle, self-improving-agents]
updated: 2026-06-07
tags:
  - llm-wiki
  - memory
  - knowledge-graph
  - lifecycle
  - self-improving-agents
topic: llm-wiki
role: child-concept
status: active
last_reviewed: 2026-06-07
raw_source: https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2
lifecycle: volatile
confidence: medium
review_cadence: quarterly
---

# LLM Wiki v2 memory lifecycle

> Reference-stack lens: [AI engineering](index.md).

> Concept hub: [AI engineering](index.md)

Rohit Garg's extension to [Karpathy's LLM Wiki pattern](llm-wiki-pattern.md) argues that a persistent wiki needs lifecycle machinery once it grows beyond a small hand-guided vault. The core upgrade is: **compiled knowledge should have confidence, age, provenance, contradiction handling, and promotion/forgetting behavior.**

## Cluster disposition — 2026-06-07

Disposition: **keep as a child/reference concept under [LLM Wiki Pattern](llm-wiki-pattern.md).**

This page should not merge into the main LLM-wiki pattern page because it captures a distinct scaling layer: confidence scoring, supersession, retention/decay, typed links, event hooks, and quality controls. It informs [gbrain](https://github.com/garrytan/gbrain) fact/query behavior and Hermes skill-repository advisor design; `wikic` remains deterministic and does not implement an LLM advisor. This page is not itself a tool profile or implementation runbook.

## Core additions beyond Karpathy's original

### Confidence scoring

Facts should not all be treated as equally valid. A claim should carry signals like:

- number of supporting sources;
- recency of confirmation;
- contradiction status;
- source authority;
- access/reinforcement history.

For systems using GBrain and Hermes, this maps to memory quality: record not only that "X is true," but why it is believed, where it came from, and whether it has decayed.

### Supersession

When new information contradicts older information, don't leave both floating. The newer claim should explicitly supersede the old claim while preserving the history.

Useful page-level pattern:

```yaml
supersedes:
  - old_claim_id_or_page
superseded_by: null
confidence: 0.86
last_confirmed: 2026-05-24
sources:
  - ...
```

### Forgetting / retention curves

A wiki that never forgets becomes a junk drawer. Rohit suggests decay curves inspired by Ebbinghaus:

- transient bugs decay fast;
- architecture decisions decay slowly;
- frequently accessed or newly confirmed facts get reinforced;
- stale facts are deprioritized rather than necessarily deleted.

Durable user preferences belong in persistent memory; task progress and stale session artifacts should remain in session history rather than permanent context.

### Consolidation tiers

The proposed memory pipeline:

1. **Working memory** — recent observations, raw and untrusted.
2. **Episodic memory** — session summaries compressed from observations.
3. **Semantic memory** — cross-session facts consolidated from episodes.
4. **Procedural memory** — reusable workflows/patterns extracted from repeated facts.

One possible mapping for a Hermes/second-brain stack is:

- Discord/session transcripts → working/episodic.
- second-brain pages/GBrain facts → semantic.
- Hermes skills → procedural.
- MEMORY/USER profile → tiny high-confidence active context only.

## Typed knowledge graph

Karpathy's original relies on Markdown pages and wikilinks. Rohit's v2 says links should become typed relationships:

- `uses`
- `depends_on`
- `contradicts`
- `caused`
- `fixed`
- `supersedes`
- `owned_by`
- `blocks`

The graph does not replace readable pages; it augments them for traversal and impact analysis. Example: "what breaks if we upgrade Redis?" should start from the Redis node and traverse `uses`/`depends_on` relationships.

## Search stack

Recommended retrieval stack:

1. BM25 / lexical search.
2. Vector search.
3. Graph traversal.
4. Reciprocal rank fusion across results.

This supports using GBrain as an indexed/query layer over a canonical Markdown corpus when that separation fits the system's ownership model.

## Automation hooks

Rohit's v2 makes the LLM Wiki event-driven:

- new source → auto-ingest, extract entities, update graph/index;
- session start → load relevant context;
- session end → compress session and file insights;
- query → decide whether answer is worth crystallizing;
- memory write → check for contradictions and supersession;
- schedule → lint, consolidate, retention decay.

A nightly/self-improvement loop should not only summarize sessions; it should decide what gets promoted to memory, skill, or second-brain page.

## Quality controls

The wiki should score generated content for:

- source citations;
- structure;
- consistency with existing pages;
- contradiction handling;
- whether the page is useful enough to keep.

Low-quality content should be flagged or rewritten. This is the missing guardrail in most vibe-built LLM Wiki implementations.

## Privacy / governance

Before ingesting into the wiki:

- strip credentials/API keys/tokens;
- distinguish private vs shared knowledge;
- keep an audit trail of operations;
- make bulk operations reversible.

Discord/Hermes/second-brain workflows can contain private plans, credentials, and sensitive personal context, so ingestion boundaries need to account for those risks.

## Implementation spectrum

Rohit's phased model:

1. **Minimal viable wiki:** raw + wiki + index + schema.
2. **Lifecycle:** confidence, supersession, retention.
3. **Structure:** entities + typed graph.
4. **Automation:** hooks for ingest/lint/context injection.
5. **Scale:** hybrid search + quality scoring + consolidation.
6. **Collaboration:** sync, shared/private scopes, work coordination.

## Capability-led integration guidance

Do not build a giant app first. Add missing lifecycle pieces to an existing agent/index workflow: preserved evidence, source summaries, entity/concept synthesis, provenance/confidence, deterministic write validation, diff review, separately authorized downstream indexing, and periodic lint/consolidation.

## Related

- [LLM Wiki Pattern](llm-wiki-pattern.md)
- [gbrain](https://github.com/garrytan/gbrain)
- wikic
- [nashsu  llm_wiki](../../intel/github-repos/repos/nashsu--llm_wiki.md)
- Raw source: https://gist.github.com/rohitg00/2067ab416f7bbe447c1977edaaa681e2
