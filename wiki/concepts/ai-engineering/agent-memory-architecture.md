---
title: Agent Memory Architecture
created: 2026-05-22
updated: 2026-09-07
type: concept
tags: [ai, memory, agents, second-brain, lifeos, gbrain]
sources:
  - wiki/concepts/ai-engineering/ai-memory-and-knowledge-graphs.md
  - wiki/concepts/ai-engineering/llm-wiki-pattern.md
  - https://github.com/garrytan/gbrain
  - https://x.com/KSimback/status/2058262328496554021
status: active
lifecycle: volatile
confidence: high
last_reviewed: 2026-09-07
review_cadence: monthly
---

# Agent Memory Architecture

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

Agent memory should be layered. Raw evidence, curated knowledge, runtime working memory, cross-agent episodic recall, indexes, task state, personal configuration, and current chat context solve different problems and should not be collapsed into one bucket.

The governing principle is:

> **Centralized access, not centralized ownership.**

Agents should be able to retrieve relevant context across layers, but each durable fact or artifact needs one canonical owner. Generated memory may propose promotion; indexes and sidecars may accelerate recall; neither becomes canonical by convenience.

This page is the durable architecture/rationale surface for the memory, knowledge-graph, and RAG cluster. Executable sequencing belongs in the owning issue system. The broader memory-system thesis remains in [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md), and the retrieval-vs-graph decision lens remains in [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md).

## Architecture boundary

Operational identity and goals, generated working memory, and curated durable knowledge need separate privacy, retention, and publication lifecycles. Runtime trees should not be mounted or mirrored into the knowledge vault. Back up generated state for recovery; promote only reviewed durable deltas.

## Ownership and promotion matrix

| Surface | Canonical role | Retention / promotion |
|---|---|---|
| Authored identity, goals, and configuration | Private operational posture | Durable private lifecycle; reviewed capsules only |
| Generated working memory | Episodic continuity | Expiring state, recoverable backup; reviewed proposals, not direct truth |
| Hermes compact memory | Always-loaded preferences and environment facts | Intentionally small; procedures move to skills, broad knowledge to the vault |
| Session history | Exact conversation and resumable history | Search directly; promote only lasting decisions or lessons |
| Markdown knowledge vault | Human-readable durable knowledge and rationale | Reviewed, versioned; indexed by GBrain |
| GBrain | Search, graph, facts, trajectories, and MCP access | Rebuildable index plus bounded derived metadata; does not replace Markdown |
| Shared skill repository | Portable doctrine, procedures, and projections | Versioned source; runtime projections remain derived |
| GitHub Issues / Projects | Executable work, sequencing, and status | Lessons return to the owning docs or skills after completion |
| Episodic sidecar | Scoped cross-agent recall and explicit handoffs | Non-canonical, namespaced, exportable/deletable; reviewed promotion only |

## Information flows

```text
authored private operational context → reviewed capsule → knowledge vault → GBrain retrieval
generated working memory → bounded promotion proposal → existing owner or discard
shared doctrine + skills → deterministic runtime projection
issue → bounded execution → PR + evidence → warranted durable lesson
```

Backup, promotion, indexing, and canonical ownership are separate operations:

- **Backup** makes restoration possible.
- **Promotion** turns reviewed working material into durable knowledge, procedure, configuration, or work.
- **Indexing** makes an existing source easier to retrieve.
- **Canonical ownership** identifies which source wins when representations disagree.

## Layer model

1. **Raw evidence** — immutable or lightly processed source material in `raw/`, repo intelligence, references, reports, transcripts, and captures. It preserves provenance; it is not the final answer.
2. **Curated knowledge** — synthesized pages in the canonical second-brain. This is the durable human-readable source of truth.
3. **Operational personal configuration** — authored identity/goals/configuration and compact Hermes user memory. These change live agent posture and therefore require stricter privacy and lifecycle boundaries than ordinary wiki pages.
4. **Working and episodic memory** — runtime working memory, current agent context, session stores, and a possible cross-agent sidecar. These optimize continuity and recall; they are not automatically durable truth.
5. **Deterministic health substrate** — Wikic catalog, graph, doctor, summary, vault-policy diagnostics, and path-safe candidate review. These verify and summarize Markdown and can be rebuilt; GBrain/MCP owns downstream sync.
6. **Search / graph / fact index** — GBrain hybrid retrieval, extraction, facts, trajectories, and MCP tools. This accelerates access to curated knowledge; it should not replace the vault.
7. **Procedural memory** — shared skills and repo instructions. Reusable workflows belong here rather than in personal fact stores or knowledge notes.
8. **Executable task state** — GitHub Issues/Projects, with owned specification bridge when work needs deeper decomposition. Historical planning artifacts remain evidence, not active authority. This stays separate so the vault does not regrow into a task database.

## Runtime boundary

Keep private identity continuity and consequential-work controls in a private runtime profile while using shared infrastructure for durable knowledge and procedures. Constrain competing durable graphs, second task boards, duplicated skills/doctrine, duplicate automation, and runtime state mounted into source repositories. The recommended relationship is an opinionated agent profile over shared infrastructure, not a second whole-stack operating system.

## Promotion policy

A weekly process should begin as a report-only **promotion proposal**, not a sync. It should:

1. inspect only changed, allowlisted working-memory artifacts since a durable cursor;
2. exclude logs, observability, security telemetry, state registries, signals, and run intermediates;
3. search GBrain and the filesystem before proposing a new page;
4. prefer updating an existing canonical artifact;
5. classify each candidate as vault knowledge, USER fact, compact Hermes memory, owned skill, repo instruction, GitHub issue, or discard;
6. cap output to a small reviewable set and measure acceptance, duplicates, and noise;
7. make no direct canonical edits until repeated report-only runs prove high quality.

Encrypted backup of the full USER/MEMORY tree is an orthogonal recovery control and should include a real restore rehearsal.

## Cross-agent episodic memory hypothesis

The missing capability may be cross-agent episodic recall and explicit handoff—not another document knowledge graph. Benchmark existing products before custom development.

A bounded trial should disable automatic capture/recall initially, use explicit store/search, prohibit whole-vault and sensitive identity ingestion, and prove isolation, correction, deletion/export, provenance, latency, and measurable value over GBrain/session search.

Supermemory, Honcho, Mem0, Hindsight, OpenViking, and local providers are candidates with different integration and deployment trade-offs. Graphiti and Cognee are architectural references that may duplicate GBrain. Letta is an agent runtime rather than merely a memory sidecar. Candidate fit is not adoption or installed-state evidence.

## External architecture cross-check — Kevin Simback

[Kevin Simback’s Hermes Agent Memory Guidebook](https://x.com/KSimback/status/2058262328496554021) provides a useful three-layer product map: native Hermes memory, one optional official `MemoryProvider`, and community extensions that either compete for that slot or occupy another ontological role. His most useful distinction for this architecture is that GBrain is additive rather than a `MemoryProvider` substitute. [Source: Kevin Simback, X article, 2026-05-23](https://x.com/KSimback/article/2058262328496554021)

This supports the current ownership model rather than replacing it. Simback’s taxonomy explains **where products plug in**; this page still governs **which system owns each data class, how it is retained, and how knowledge is promoted**. [Source: [kevin simback hermes agent memory guidebook](https://x.com/KSimback/status/2058262328496554021), 2026-08-29]

The practical adoption gate is also aligned: if an added memory layer increases latency, cost, contradiction, or context pressure without a demonstrable improvement in real work after a bounded trial, remove it. Apply that test to the cross-agent episodic-memory hypothesis before adopting Supermemory or any alternative. [Source: Kevin Simback, X article, 2026-05-23](https://x.com/KSimback/article/2058262328496554021)

## Open gap — repo-scoped memory

Principal-centric or global memory does not automatically answer “why did we do it this way in this codebase?” Shared skills are cross-repo, and GitHub Issues hold task state rather than a complete decisions history. Check whether repo-scoped decisions already have an owner before adding another store.

The candidate pattern is a repo-scoped decisions/lessons log that compounds per project, fed by existing SessionEnd/PreCompact hooks and promoted through the normal curation tiers rather than read directly as truth. Two refinements are worth carrying if it is ever piloted: type the artifacts with parse-friendly prefixes instead of keeping a freeform log, and give each artifact type a matching skill that teaches the agent its structure.

This is a **gap statement, not an adopted design.** It would need to satisfy the promotion policy above, and the obvious failure mode is that a per-repo log becomes a fourth competing truth store. The reference implementation seen in the wild (a separate project-management repo per engagement, with a validator flagging authored-versus-derived drift) is described in [Agentic Development Lifecycle](agentic-development-lifecycle.md) under lifecycle invariants. [Architecture synthesis; source example: Cole Medin video analysis, captured 2026-08-11]

## Design rules

- Long-lived claims graduate from conversation or working memory into their canonical source with provenance.
- Search indexes and generated graphs are rebuildable; curated Markdown remains the durable knowledge artifact.
- A memory sidecar may improve recall but must remain scoped, inspectable, exportable, and deletable.
- GitHub Issues/Projects own execution state; vault pages own durable knowledge and rationale.
- Wikic proves structural health; GBrain retrieves and reasons over the graph; shared skills own judgment-heavy procedures.
- No cloud ingestion of intimate USER, health, finance, or family material without an explicit privacy decision.
- No automatic capture surface becomes authoritative merely because it has more data.
- Use [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md) before adding retrieval infrastructure: weak synthesis calls for better pages; lookup calls for indexing; relationships call for typed links/entities; cross-agent continuity may justify an episodic sidecar.

## Rejected defaults

- **Track live LifeOS MEMORY in owned skill repository:** rejected because it creates a shadow brain, runtime/Git coupling, destructive-clean hazards, permanent churn, and privacy-scan gaps.
- **Put USER and MEMORY inside the second-brain:** rejected because operational identity/runtime state and curated knowledge have different privacy, retention, validation, and publication lifecycles.
- **Create a separate Git repo for raw MEMORY as the first solution:** rejected as the default because moving the same generated shadow graph to another repo changes blast radius but not ownership ambiguity. Use encrypted backup; consider allowlisted snapshots only if a concrete audit requirement appears.
- **Automatically promote all weekly memories:** rejected because generated notes are proposals, not truth.
- **Replace GBrain/second-brain with a memory product:** rejected unless a future benchmark demonstrates a clear capability gap and a safe migration path.

## Related

- [AI Memory and Knowledge Graphs](ai-memory-and-knowledge-graphs.md)
- [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md)
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- personal AI operating system
- [gbrain](https://github.com/garrytan/gbrain)
- wikic
- [MCP and Context Tools](mcp-context-tools.md)
- [kevin simback hermes agent memory guidebook](https://x.com/KSimback/status/2058262328496554021)
