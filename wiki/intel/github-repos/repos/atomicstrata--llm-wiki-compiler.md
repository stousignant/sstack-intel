---
title: atomicstrata/llm-wiki-compiler
type: repo-intel
aliases:
  - llm-wiki-compiler
  - llmwiki
  - GitHub repo: atomicstrata/llm-wiki-compiler
source: https://github.com/atomicstrata/llm-wiki-compiler
category: llm-wiki-second-brain
topics: [github-repo, llm-wiki, second-brain, knowledge-compilation, markdown, obsidian, mcp]
updated: 2026-06-07
tags:
  - llm-wiki
  - github-repos
  - tool-intel
  - second-brain
  - knowledge-compilation
  - markdown
  - obsidian
  - mcp
topic: llm-wiki
role: repo-card
status: deep-analyzed
usefulness_score: 88
recommendation: adopt-now
usage: sandboxed
score_confidence: high
last_reviewed: 2026-05-24
license: MIT
---

# atomicstrata/llm-wiki-compiler

> Opinionated reference-stack evaluation, reviewed 2026-05-24. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

> Topic hub: [LLM Wiki Pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md)

## Decision

- **Usefulness score:** `88/100` — high stack fit and strong reuse readiness as a bounded LLM-wiki compiler, with safety limits around the canonical vault.
- **Recommendation:** `adopt-now`
- **Usage observed 2026-05-24:** `sandboxed`. Temporary ingest/lint smoke; the completed compile experiment is described below.
- **Review candidate:** run a bounded disposable scratch sandbox with 5–10 copied non-sensitive notes or repo-intelligence sources; use `compile --review`; compare generated pages against curated notes before anything touches the canonical vault.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Directly matches the compile-once/interlinked-Markdown direction while preserving Obsidian/GBrain as canonical layers. |
| Leverage | 22/25 | Could reduce manual synthesis time for repo-intelligence and selected second-brain source batches. |
| Reuse readiness | 18/20 | Installable CLI, smoke-tested, review mode, linting, MCP/server surface; Node >=24 is the main friction. |
| Maturity/trust | 12/15 | MIT, recently released, broad tests; still young and model/provider quality remains unproven on representative target corpora. |
| Differentiation | 12/15 | More operational than a generic RAG/wiki idea because it has review queues, hash-based compilation, linting, exports, and MCP. |
| **Total** | **88/100** |  |

## Verdict

**Adopt for sandboxed experiments now; do not make it the canonical brain.** `llm-wiki-compiler` is a TypeScript CLI that ingests URLs/files/session exports, incrementally compiles sources into Obsidian-friendly interlinked Markdown, and supports review queues, linting, exports, a local viewer, and MCP. It is most useful as a bounded compiler for copied source sets, not as a replacement for canonical Markdown knowledge or an established retrieval/index layer.

## Workload fit

- It is a concrete, usable implementation of the compile-once LLM-wiki idea: `sources/` → concept pages → wikilinks → query/save → richer wiki.
- It complements an existing toolchain: an Obsidian/Git vault can remain canonical, GBrain can index/query-curate, Hermes can orchestrate, and `llmwiki` can compile selected source folders in a bounded workspace.
- It can accelerate the GitHub-stars project: raw README/docs/repomix excerpts could be compiled into temporary wiki pages, then distilled into curated repo notes.
- It has useful operating patterns for Hermes workflows: hash-based incremental compilation, review candidates, deterministic linting, portable exports, and MCP exposure.

## Reuse / inspiration potential

- **Direct reuse:** yes, as a sandbox CLI via `npx` or global install; use copied source sets only.
- **Pattern to borrow:** two-phase concept extraction/page generation, hash-based change detection, review-before-writing mode, provenance markers, static linting, export targets, and MCP server wrapper.
- **Stack area improved:** repo-intelligence, second-brain ingestion experiments, temporary knowledge compilation, and possible LLM-wiki/GBrain comparison workflows.
- **Autonomy leverage:** gives Hermes a more deterministic pipeline for transforming bounded source folders into candidate wiki artifacts instead of relying only on freeform note-writing.
- **Freedom leverage:** if it works on real source batches, it can cut manual synthesis time and turn accumulated bookmarks/repos/docs into queryable artifacts faster.

## What it is

`llm-wiki-compiler` is a Node/TypeScript CLI package named `llm-wiki-compiler` with the binary `llmwiki`. It compiles raw sources into an interlinked Markdown wiki inspired by Karpathy's LLM Wiki pattern. Commands include `ingest`, `ingest-session`, `compile`, `compile --review`, `review`, `query`, `lint`, `view`, `schema`, `export`, `watch`, and `serve`.

## Evidence checked

- **GitHub metadata:** `atomicstrata/llm-wiki-compiler`; TypeScript; MIT; 1,265 stars; 129 forks; pushed `2026-05-22`; latest release `v0.7.0` published `2026-05-18`; topics include `cli`, `knowledge-base`, `llm`, `markdown`, `obsidian`, `wiki`, `compiler`, `context-engineering`, `knowledge-compilation`.
- **README:** checked from `https://raw.githubusercontent.com/atomicstrata/llm-wiki-compiler/main/README.md` and the repomix pack. It describes provider configuration, compile-vs-RAG rationale, CLI commands, review queue, local viewer, exports, and MCP server.
- **Evaluation context:** memory/knowledge and compile-once Markdown workflows motivated the source review; the upstream README remains the public attribution.
- **repomix pack:** generated a temporary Repomix evidence pack; 241 files, ~415,356 tokens, ~1.5M chars. Not stored in the vault.
- **Key files inspected:** `README.md`, `package.json`, `src/cli.ts`, `src/commands/compile.ts`, `src/commands/query.ts`, `src/compiler/index.ts`, `src/linter/rules.ts`, `test/mcp-server.test.ts`, `LICENSE`.
- **Local smoke test:** ran `npx --yes llm-wiki-compiler@latest --help`; then ingested a temporary local Markdown file and ran `llmwiki lint`. It created `sources/sample.md` and `.llmwiki/last-lint.json` with `0 error(s), 0 warning(s), 0 info`.

## Verified / plausible / source claims

- **Verified:** package exposes `llmwiki` binary, requires Node `>=24`, is MIT licensed, and ships scripts for build/test/publish.
- **Verified:** CLI registers ingest, ingest-session, view, compile, review, query, watch, lint, schema, export, and MCP `serve` commands in `src/cli.ts`.
- **Verified:** compile orchestrator uses lock acquisition, change detection, source-state tracking, page generation, link resolution, index generation, optional review candidates, and embeddings update hooks.
- **Verified:** lint rules are static/no-LLM checks over frontmatter, wikilinks, citations, file structure, confidence, and related wiki quality signals.
- **Verified:** tests cover MCP tool registration, ingest shape, compile result shape, providers, provenance, review flow, schema, viewer security, export, embeddings, and query behavior.
- **Plausible:** `compile --review` could be a useful safety boundary for applying LLM-wiki compilation to bounded source subsets; this was not tested with actual model calls in this run.
- **Source claim:** quality of concept extraction/page generation depends on the configured LLM provider and prompt behavior.

## Strengths

- **More productized than `llm-wiki-agent`:** ships an installable CLI, npm package shape, release `v0.7.0`, and many commands rather than only an agent scaffold.
- **Review mode is a useful safety valve:** candidate pages can land under `.llmwiki/candidates/` before mutating `wiki/`, supporting review before generated pages enter a canonical corpus.
- **Good fit with Obsidian/GBrain:** output is Markdown/wikilinks and exports include `llms.txt`, JSON, JSON-LD, GraphML, and Marp.
- **MCP server is strategically useful:** exposes wiki tools/resources so Hermes or another MCP-aware agent could interact with a compiled wiki workspace.
- **Incremental/hashing model:** changed sources are detected and only new/changed files go through compilation, controlling cost and repeated work.
- **Evidence of testing:** the repo includes broad Vitest coverage across providers, provenance, schema, viewer, export, embeddings, review, and MCP paths.

## Risks / caveats

- **Node 24 requirement:** this is a sharper runtime dependency than many CLIs; check deployment hosts before assuming global install works everywhere.
- **LLM calls required for real compile/query:** ingest/lint can be smoke-tested without model calls, but the value depends on configured provider quality and cost.
- **Potential duplication/sprawl:** generated concept pages can still pollute a vault if pointed at canonical notes without review boundaries.
- **Young project:** active and released, but still early; package metadata in the repomix pack references `atomicmemory` URLs while the inspected repo is `atomicstrata`, so watch for rename/ownership churn.
- **Not a GBrain replacement:** it compiles and serves a wiki; it does not replace the current source registration, sync, memory, and query layer around GBrain.

## Integration ideas

- **Repo-intelligence sandbox:** feed selected README/docs/repomix excerpts into an isolated `llmwiki` project, compile with `--review`, then turn only the best candidate pages into curated repo-intelligence notes.
- **Second-brain subset experiment:** copy 5–10 non-sensitive notes from one folder into `sources/`, run `compile --review`, and compare generated pages against the current hand-curated Obsidian/GBrain output.
- **MCP experiment:** run `llmwiki serve` in a sandbox and see whether Hermes can query/read pages through MCP more cleanly than ad hoc file search.
- **Export bridge:** test whether `llms.txt` or JSON-LD exports help downstream LLM/wiki/GBrain workflows.

## Alternatives / related repos

- [SamurAIGPT/llm-wiki-agent](SamurAIGPT--llm-wiki-agent.md) — agent-scaffold version of the LLM-wiki pattern; better as workflow inspiration than installable CLI.
- [GBrain](garrytan--gbrain.md) — the reference AI/index/query layer over canonical Markdown knowledge.
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md) — graph/visualization-heavy direction worth comparing after generated synthesis pages exist.
- [Michaelliv/markit](Michaelliv--markit.md) — source normalization/conversion tool that could precede `llmwiki ingest` for messy inputs.

## Completed evidence and guidance

- Completed: Run a real `compile --review` experiment on 5 copied non-sensitive second-brain/repo-intelligence notes; produced 21 review candidates in a disposable sandbox.
- Completed: Compare output quality against the `llm-wiki-agent` scaffold and current Hermes-authored repo notes; see [LLM Wiki tools comparison](../comparisons/llm-wiki-second-brain.md).
- Reusable experiment method: a repeatable disposable ingest/compile/review helper can keep candidate output away from canonical knowledge.
- Guidance: Do not write generated `wiki/` output into the canonical vault unless promoted through explicit review.
