---
title: nashsu/llm_wiki
type: repo-intel
aliases:
  - LLM Wiki desktop app
  - GitHub repo: nashsu/llm_wiki
source: https://github.com/nashsu/llm_wiki
category: personal-knowledge-management
topics: [github-repo, llm-wiki, knowledge-compiler, desktop-app, tauri, obsidian, rag, knowledge-graph]
updated: 2026-06-07
tags:
  - llm-wiki
  - github-repos
  - tool-intel
  - knowledge-compiler
  - desktop-app
  - tauri
  - obsidian
  - rag
  - knowledge-graph
topic: llm-wiki
role: repo-card
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-24
license: GPL-3.0
stars: 9134
forks: 1116
primary_language: TypeScript
latest_release: v0.4.13
---

# nashsu/llm_wiki

> Reference-stack fit as reviewed 2026-05-24; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

> Topic hub: [LLM-wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md)

## Decision

- **Usefulness score:** `88/100` for the reference stack's Hermes/GBrain/second-brain stack.
- **Recommendation:** `distill-pattern` — this is the strongest concrete LLM Wiki implementation checked so far, but GPL-3.0 and desktop-app assumptions make it better as a reference/pilot than code to directly absorb into Hermes unless copyleft constraints are acceptable.
- **Usage observed 2026-05-24:** `reference-only`.
- **Review candidate:** Pilot it on a throwaway wiki or clone its architecture ideas into a Hermes/GBrain-native CLI pipeline. Do **not** start a big custom project before testing this app and 2-3 adjacent repos.

## What it is

A cross-platform Tauri desktop app that operationalizes [Karpathy's LLM Wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md): raw documents go in, the system incrementally builds a persistent interlinked Markdown wiki instead of re-deriving answers from raw chunks every query.

Live metadata checked 2026-05-24:

- Repo: <https://github.com/nashsu/llm_wiki>
- Stars/forks: 9,134 / 1,116
- Latest release: `v0.4.13`, published 2026-05-24
- Stack: Tauri v2, React 19, TypeScript, Vite, Rust backend, LanceDB optional vector search
- License: GPL-3.0 text in `LICENSE` despite GitHub JSON reporting `Other`

## Reference-stack relevance

This repo is a shipped example of a product-shaped knowledge layer: source ingestion, auto wiki generation, graph browsing, review queue, web clipper, local API, and multi-provider LLM config. It overlaps with workflows that use second-brain/GBrain/Hermes to compound knowledge rather than lose work in chat history.

The big difference: this repo is a **desktop app** that owns the UX and project format. Where Hermes is already the agent runtime and Obsidian/Git Markdown the canonical vault, the highest-leverage path is likely **not** adopting the whole app as-is, but extracting design patterns into a Hermes/GBrain-native workflow.

## Architecture observed

### Project structure

The repo defines an LLM Wiki project as:

```text
my-wiki/
├── purpose.md
├── schema.md
├── raw/
│   ├── sources/
│   └── assets/
├── wiki/
│   ├── index.md
│   ├── log.md
│   ├── overview.md
│   ├── entities/
│   ├── wiki/concepts/
│   ├── sources/
│   ├── queries/
│   ├── synthesis/
│   └── comparisons/
├── .obsidian/
└── .llm-wiki/
```

This maps cleanly onto the reference stack's desired second-brain layout: raw-source preservation, generated semantic pages, source summaries, synthesis pages, and an explicit schema/operating manual.

### Ingestion pipeline

The ingestion code (`src/lib/ingest.ts`) uses a staged LLM workflow that emits explicit file blocks:

```text
---FILE: wiki/concepts/foo.md---
...
---END FILE---
```

Notable engineering details:

- LLM output parser handles CRLF, marker whitespace/case variants, fenced-code false positives, and malformed blocks.
- `isSafeIngestPath()` rejects paths outside `wiki/`, absolute paths, `..`, Windows drive paths, control chars, and reserved names. This matters because source documents can prompt-inject the LLM into writing arbitrary files.
- It maintains source identity and source summary slugs, caches ingests, merges sources, and has tests for parsing and path safety.

This is a strong pattern for any Hermes-native implementation: the LLM can generate structured edits, but a deterministic parser/validator decides what touches disk.

### Search and retrieval

README describes retrieval as:

- tokenized keyword search + graph expansion by default;
- optional vector search with independent endpoint/API key/model;
- LanceDB embedded vector DB;
- README claims benchmark recall improved from 58.2% to 71.4% with vector search enabled.

`src/lib/embedding.ts` implements a standard chunk/embed/upsert/search path with chunk-level max pooling and matched chunks for future UI. It also has explicit error surfacing and auto-halving for oversized embedding requests.

### Graph layer

`src/lib/wiki-graph.ts` builds a graph from Markdown wikilinks, computes link counts, filters out query nodes, and uses Louvain community detection via graphology. This is simpler than Rohit Garg's proposed typed knowledge graph, but it is already useful for navigation and health checks.

### Local API and agent integration

The app exposes a local HTTP API on loopback port `19828`:

- `GET /api/v1/health`
- `GET /api/v1/projects`
- `GET /api/v1/projects/{id}/files`
- `GET /api/v1/projects/{id}/files/content`
- `POST /api/v1/projects/{id}/search`
- `GET /api/v1/projects/{id}/graph`
- `POST /api/v1/projects/{id}/sources/rescan`

Security posture in `src-tauri/src/api_server.rs`:

- health is unauthenticated;
- other endpoints require API enabled + authorization unless explicitly allowed unauthenticated;
- token can come from app settings or `LLM_WIKI_API_TOKEN`;
- accepts `x-llm-wiki-token`, `Authorization: Bearer`, or query token, with UI warning that query tokens leak;
- has rate limiting and max body size;
- chat endpoint is not implemented server-side yet because chat/RAG lives in the WebView.

This is important for Hermes: the agent could talk to a running LLM Wiki app via HTTP, but the more native version would expose equivalent GBrain/Hermes tools directly.

### LLM providers

The app supports OpenAI, Anthropic, Google, Ollama, Azure, Custom, Claude Code CLI, and Codex CLI. The user does **not** need Copilot specifically. This answers the earlier concern: a Copilot-specific script is the wrong dependency for the reference stack. The LLM Wiki pattern can run through Hermes, API providers, Claude/Codex CLIs, Ollama, or a custom OpenAI-compatible endpoint.

## Best ideas to steal

1. **Raw/wikified/generated separation** — raw sources immutable, wiki generated, schema controls behavior.
2. **`purpose.md` + `schema.md` as first-class control files** — the schema is the product.
3. **Deterministic edit boundary** — LLM emits candidate file blocks; code validates paths and parses robustly before writing.
4. **Source summary pages** — every raw source gets a canonical source page, then concept/entity pages link back to it.
5. **Human review queue** — LLM can flag uncertain creates/deep research/skips asynchronously instead of blocking ingest.
6. **Local HTTP API** — lets other agents query/search/rescan without GUI coupling.
7. **Web clipper pipeline** — Readability + Turndown is the right extraction layer for articles.
8. **Optional vector search** — start lexical/graph-first; embeddings are additive, not required.
9. **Graph insights/community detection** — useful for surfacing clusters, gaps, orphan pages.
10. **Deletion/cascade cleanup** — source deletion should remove source summaries, update references, preserve shared entities.
11. **Big context budget controls** — practical UX for LLMs with different context sizes.
12. **Tests around LLM-output parsing** — this is where knowledge compilers break quietly.

## Weaknesses / risks

- **GPL-3.0:** Direct code reuse can infect downstream distribution. Fine for private experiments; risky for Hermes core unless intentional.
- **Desktop-first architecture:** the reference stack's workflow is Discord → Hermes → Markdown vault/GBrain. A GUI app may become a parallel brain unless carefully integrated.
- **Chat API missing:** External agents can search/read/rescan, but not yet ask the app to run its full chat/RAG pipeline through the API.
- **Graph is mostly wikilink-derived:** It lacks typed relationships/confidence/supersession from [llm-wiki-v2-memory-lifecycle](../../../concepts/ai-engineering/llm-wiki-v2-memory-lifecycle.md).
- **LLM writes are still prompt-shaped:** Strong validation exists for paths, but factual quality requires review/lint/second-pass verification.
- **Binary/heavy footprint:** Tauri + Rust + Node + bundled PDFium is heavier than a Hermes CLI skill/daemon.

## Reference-stack fit

### Use directly if

- A fast GUI pilot of the LLM Wiki workflow is useful.
- Generated wiki quality needs comparison against GBrain/Hermes ingestion.
- An extra app can be evaluated on a sandbox vault/project when its UX is part of the question.

### Do not use directly if

- The canonical second-brain vault must remain controlled by Hermes/GBrain.
- Discord/Hermes is the required main interface.
- System memory/consolidation must feed directly into agent behavior.

### Recommended integration shape

Build or adapt a **Hermes/GBrain-native knowledge compiler** that borrows the patterns, not the app:

1. raw-source ingestion from URL/PDF/YouTube/GitHub/session summaries.
2. deterministic extractors (Readability/Turndown, YouTube transcript, repo repomix, PDF OCR as needed).
3. LLM-generated file-block proposals.
4. deterministic parser/validator + git diff before writes.
5. wiki pages in the canonical second-brain vault.
6. GBrain index/sync for retrieval.
7. cron/autopilot lint/consolidation.
8. optional local HTTP endpoint/MCP for other agents.

## Adjacent repos discovered for follow-up

GitHub search for `llm wiki` on 2026-05-24 surfaced a fast-moving mini-ecosystem:

- `SamurAIGPT/llm-wiki-agent` — 2,728 stars, Python, agent-first implementation.
- `atomicstrata/llm-wiki-compiler` — 1,283 stars, TypeScript, "knowledge compiler" framing.
- `Astro-Han/karpathy-llm-wiki` — 916 stars, agent skills-compatible.
- `kytmanov/obsidian-llm-wiki-local` — 649 stars, local/Ollama/Obsidian angle.
- `AgriciDaniel/claude-obsidian` — 5,456 stars, Claude + Obsidian companion.
- `nvk/llm-wiki` — 461 stars, parallel multi-agent research and artifact generation.

Before starting a custom project in this category, compare `nashsu/llm_wiki` with the six adjacent repositories listed above.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-24.
- Shallow upstream clone inspected in disposable storage.
- README and project structure inspected.
- Key files inspected: `package.json`, `src-tauri/Cargo.toml`, `src-tauri/tauri.conf.json`, `src/lib/ingest.ts`, `src/lib/embedding.ts`, `src/lib/wiki-graph.ts`, `src/lib/llm-client.ts`, `src/lib/llm-providers.ts`, `src-tauri/src/api_server.rs`.
- Repo size snapshot: 329 files; ~42k TypeScript lines, ~13.8k TSX lines, ~10.5k Rust lines, plus bundled binary assets.
- Recent commit observed: `70d5579 2026-05-25 Update DeepSeek model presets`.

## Review candidates and guidance

- Review candidate: Pilot `nashsu/llm_wiki` on a sandbox project using a local/Ollama or configured provider; do not point it at the canonical vault first.
- Review candidate: Analyze `SamurAIGPT/llm-wiki-agent`, `atomicstrata/llm-wiki-compiler`, `AgriciDaniel/claude-obsidian`, and `kytmanov/obsidian-llm-wiki-local` before custom build.
- Review candidate: Draft a Hermes/GBrain-native LLM Wiki compiler spec: CLI commands, schema, validation, git diff workflow, GBrain sync hooks, and Discord UX.
