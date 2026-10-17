---
title: MemPalace/mempalace
type: repo-intel
aliases:
  - mempalace
  - GitHub repo: MemPalace/mempalace
source: https://github.com/MemPalace/mempalace
category: memory-management
topics: [github-repo, memory, mcp, semantic-search, chromadb, claude-code]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT
---

# MemPalace/mempalace

> Reference-stack evaluation as reviewed 2026-05-28. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — highly relevant memory/retrieval reference with strong benchmark claims, but direct adoption risks creating a parallel memory truth store beside Hermes/GBrain/second-brain.
- **Recommendation:** `distill-pattern` — benchmark/retrieve patterns are worth studying; sandbox only on copied transcripts or project files.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Include MemPalace in the same bounded memory-sidecar bakeoff as Engram if current Hermes/GBrain recall pain becomes concrete.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Local-first AI memory and MCP align well, but Chroma/semantic store overlaps GBrain and session_search. |
| Leverage | 21/25 | Could improve recall over raw transcripts if benchmark claims transfer to representative workload data. |
| Reuse readiness | 17/20 | PyPI/uv install, CLI, docs, tests, benchmarks, MCP integrations; Python deps are heavier than Engram. |
| Maturity/trust | 13/15 | Very popular and active, MIT, security file, benchmarks/tests present; scam-domain warning is a real operational signal. |
| Differentiation | 11/15 | Verbatim + palace hierarchy + benchmark files are useful, but not obviously superior to current GBrain/session layers without a bakeoff. |

## Verdict

MemPalace is worth knowing about, but not worth making canonical today. Its best near-term value is as a **benchmark and retrieval-design reference**: verbatim storage, scoped hierarchy, reproducible LongMemEval results, and `wake-up` style context loading. Direct adoption should be blocked until a sandbox comparison proves it beats Hermes session_search/GBrain on representative recall tasks without fragmenting memory ownership.

## Reference-stack relevance

- It directly targets AI memory continuity and Claude Code session retention.
- Its “verbatim first” stance suits workflows that preserve source phrasing rather than relying only on lossy summaries.
- The scoped wing/room/drawer model may inform second-brain or GBrain UX.
- The benchmark harness could inspire retrieval evals for GBrain.

## What it is

A Python local-first AI memory CLI/package that stores conversation history verbatim and retrieves it with semantic search. README says the default backend is ChromaDB with a pluggable backend interface, supports mining project files and Claude Code sessions, and offers `search` / `wake-up` commands.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 52,980 stars, 6,991 forks, Python, MIT, pushed 2026-05-27, not archived.
- README: local-first memory, ChromaDB backend, `uv tool install mempalace`, `mempalace mine`, `mempalace search`, `mempalace wake-up`, benchmark claims.
- Root contents: `mempalace/`, `benchmarks/`, `tests/`, `docs/`, `hooks/`, `integrations/`, `pyproject.toml`, `uv.lock`, `SECURITY.md`, `LICENSE`, `.claude-plugin/`, `.codex-plugin/`.

## Strengths

- Strong benchmark and test posture compared with many memory repos.
- Verbatim storage avoids summary drift.
- Explicit scam-domain warning shows attention to supply-chain/user safety.
- Easy isolated install with `uv tool install mempalace`.

## Risks / caveats

- Very high stars/forks relative to project age/description should not be treated as proof of quality; rely on local bakeoff.
- ChromaDB/Python dependency stack is heavier than a SQLite/FTS sidecar.
- Another vector store can become a duplicate truth layer if not limited to sandbox or read-only imported transcripts.

## Integration ideas

- Use benchmark methodology to shape GBrain retrieval evals.
- Sandbox `mempalace mine <copied-transcript-directory>` only on copied/non-sensitive exports, never directly on canonical private data until reviewed.
- Distill wing/room/drawer scoping into GBrain/second-brain retrieval UX if it improves mental model.

## Alternatives / related repos

- [Gentleman-Programming/engram](Gentleman-Programming--engram.md) — leaner SQLite/FTS/MCP memory sidecar.
- [garrytan/gbrain](garrytan--gbrain.md) — active canonical index/query layer.
- [NevaMind-AI/memU](NevaMind-AI--memU.md) — proactive/shadow-memory pattern source already reviewed.

## Review candidates and context

- Candidate: a copied-data memory-sidecar bakeoff alongside Engram, Hermes session search and GBrain.
