---
title: Graphify-Labs/graphify
type: repo-intel
aliases:
  - graphify
  - Graphify
  - Graphify Labs
  - GitHub repo: Graphify-Labs/graphify
  - GitHub repo: safishamsi/graphify
source: https://github.com/Graphify-Labs/graphify
category: code-intelligence
topics: [github-repo, repo-intelligence, knowledge-graph, code-intelligence, mcp, graph-rag, multimodal]
status: deep-analyzed
usefulness_score: 88
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-09-02
license: Apache-2.0
---

# Graphify-Labs/graphify

> Reference-stack evaluation as reviewed 2026-09-02. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

> **Ownership moved.** The repo transferred from `safishamsi/graphify` to `Graphify-Labs/graphify` (YC S26, homepage `graphify.com`). This note was renamed from `safishamsi--graphify.md` on 2026-09-02 and all inbound wikilinks were repointed. The original upstream identity is preserved in aliases and the public ownership history.

## Decision

- **Usefulness score:** `88/100` — still the most immediately testable local code/docs/media graph tool, now with a broader multimodal story, but the license changed and the project is commercializing.
- **Recommendation:** `adopt-now` — bounded sandbox only. Run it on a copied repo and on `wiki/` before considering anything routine.
- **Usage observed 2026-09-02:** `not-used`.
- **Review candidate:** Run `/graphify` on a non-sensitive target, inspect `GRAPH_REPORT.md` and `graph.html`, and compare against GBrain and manual inspection.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 24/25 | Local CLI/skill/MCP shape, mixed-corpus input, portable artifacts. Explicitly targets Claude Code, Codex, Cursor, Gemini CLI. |
| Leverage | 23/25 | Maps unfamiliar repos and mixed doc corpora in one pass; `--wiki` produces agent-crawlable markdown. |
| Reuse readiness | 18/20 | PyPI `graphifyy`, permissive license, `uv tool install` path, extras for MCP/Ollama/Bedrock/PDF/watch. |
| Maturity/trust | 13/15 | Very active (release v0.9.53 on 2026-08-30), but 1,205 open issues and pre-v1 versioning. |
| Differentiation | 10/15 | Down from 12: no vector store and explained edges are genuinely distinct, but the overlap with GBrain's graph layer is now clearer, and hosted `app.graphify.com` is the maintainer's real product. |

## Verdict

Graphify remains the better first sandbox in this cluster, and the 2026-09 refresh strengthens the case for pointing it at the vault rather than only at code: it takes code, `.md`, PDFs, and images in one corpus, tags every edge `EXTRACTED` or `INFERRED`, and ships no vector store at all. It is still a sidecar, not a canonical index. The new caveat is direction of travel — the open-source CLI now sits under a funded company whose stated product is the always-on hosted version.

## Workload fit

- One command maps a mixed corpus, including PDFs and articles as well as linked Markdown prose.
- Edge provenance tags make its output reviewable rather than something to trust blindly, which fits the vault's evidence norms.
- MCP stdio server means it can be exposed per-task to an agent without becoming a second persistent truth store next to GBrain.
- Code parsing is fully local via tree-sitter with no LLM call; only the semantic pass over docs and media hits a model.

## What it is

A Python CLI plus AI-assistant skill that turns a folder into a queryable knowledge graph. `/graphify .` writes `graphify-out/` containing `graph.html` (interactive force-directed graph), `GRAPH_REPORT.md` (key concepts, surprising connections, suggested questions), and `graph.json` (the persistent graph). Query surfaces are `graphify query "<question>"`, `graphify path A B`, and `graphify explain "<node>"`. Communities are detected with Leiden over NetworkX.

## Evidence checked

- GitHub API on 2026-09-02: 113,725 stars, 11,072 forks, **Apache-2.0**, Python, default branch `v8`, pushed 2026-08-30, 1,205 open issues, 385 watchers, homepage `graphify.com`.
- Latest release: `v0.9.53`, published 2026-08-30.
- `v8` README: install is now `uv tool install graphifyy && graphify install` (pipx alternative; plain `pip` discouraged on Mac/Windows because the skill resolves Python from `graphify-out/.graphify_python`).
- `v8` README: `--wiki` builds markdown articles per community with an `index.md` entry point; `--watch` and `graphify hook install` (post-commit) keep the graph current; exports to SVG, GraphML, and Neo4j cypher.
- `v8` README: MCP server via `python -m graphify.serve`, stdio or HTTP transport, exposing `query_graph`, `get_node`, `get_neighbors`, `shortest_path`, `list_prs`, `get_pr_impact`, `triage_prs`.
- `v8` README: extras include `mcp`, `ollama` (local inference), `bedrock`; `graphify-out/` is intended to be committed, with `cost.json` local-only.

## What changed since 2026-05-28

- **Owner:** `safishamsi` → `Graphify-Labs`. YC S26 badge and a hosted platform at `app.graphify.com` in early access.
- **License:** MIT → **Apache-2.0**. Still permissive; patent grant added. Not a blocker, but the vault's old MIT claim is now wrong.
- **Scale:** 55,485 → 113,725 stars; 5,832 → 11,072 forks.
- **Default branch:** `v1` → `v8`. The `main` branch README is stale and still describes an `obsidian/` output directory that the `v8` README does not mention. Read `v8`.
- **Positioning:** now explicitly "not a vector index — no embeddings, no vector store," which sharpens the contrast with GBrain's hybrid retrieval.

## Strengths

- Mixed-corpus ingestion in one graph: code via tree-sitter AST, docs and PDFs and images via a semantic model pass.
- Edge confidence tags make guessed relationships visible instead of silent.
- Persistent `graph.json` is queryable weeks later without re-reading the corpus.
- Local inference path exists (`ollama` extra) for privacy-sensitive corpora.

## Risks / caveats

- **Open-core drift.** The README funnels toward the hosted always-on product. Assume the CLI's feature ceiling is set by what does not cannibalize that.
- 1,205 open issues and pre-v1 versioning at v0.9.53; the API and output shape can still move under you.
- The semantic pass over docs and media sends content to a model. For the vault this means scoping the run to `wiki/`, never the private journal directory or anything with credentials, unless routed through the local `ollama` extra.
- Still overlaps GBrain. Treat the graph as a disposable audit artifact, not a third knowledge store.
- Star and fork counts are enormous for a young project; calibrate on sandbox output, not attention.

## Integration ideas

- Point it at a copied, non-sensitive wiki corpus as a vault-hygiene pass: read `GRAPH_REPORT.md` for god nodes, orphans, and surprising connections, then feed the real findings into `sstack-vault-cleanup`.
- Use `--wiki` output only as a comparison benchmark against Hermes-authored pages; do not commit generated articles into the vault.
- Expose the MCP server per-task rather than globally.
- Gitignore `graphify-out/` in the vault even though the project recommends committing it — the vault's durable product is curated prose.

## Alternatives / related repos

- [Egonex-AI/Understand-Anything](Egonex-AI--Understand-Anything.md) — richer dashboard and guided-tour UX; narrower knowledge-base mode.
- [oraios/serena](oraios--serena.md) — semantic code editing/navigation MCP candidate.
- [CodeGraphContext/CodeGraphContext](CodeGraphContext--CodeGraphContext.md) — code graph/MCP/report reference.
- [garrytan/gbrain](garrytan--gbrain.md) — canonical index and synthesis layer; not replaced by this.

## Review candidates and context

- Candidate: a copied-corpus codebase-understanding sandbox bakeoff against GBrain and manual inspection.
- Ownership history recorded 2026-09-02: `safishamsi/graphify` transferred to `Graphify-Labs/graphify`.
