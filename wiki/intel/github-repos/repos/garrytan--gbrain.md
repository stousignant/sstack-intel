---
title: garrytan/gbrain
type: repo-intel
aliases:
  - GBrain
  - GitHub repo: garrytan/gbrain
source: https://github.com/garrytan/gbrain
category: second-brain-infrastructure
topics: [github-repo, gbrain, second-brain, personal-knowledge-management, mcp, hybrid-search, knowledge-graph, agents]
status: deep-analyzed
usefulness_score: 96
recommendation: adopt-now
usage: active-index-layer
score_confidence: high
last_reviewed: 2026-05-24
license: MIT
---

# garrytan/gbrain

> Reference-stack fit as reviewed 2026-05-24; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `96/100` — GBrain is the highest-leverage index/query pillar under the dated reference-stack lens: MCP server, skillpack, sync workflow, and a strong reusable architecture for personal AI memory.
- **Recommendation:** `adopt-now` — keep as a reference-stack pillar and build repo-intelligence / dream-cycle workflows around a well-maintained index rather than a competing knowledge store.
- **Usage observed 2026-05-24:** `active-index-layer`.
- **Review candidate:** validate metadata, graph/timeline coverage and sync reliability before adding automation; keep GBrain derived from canonical Markdown rather than making it a competing human knowledge store.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 25/25 | Directly matches the Hermes + Obsidian/Git + local AI reference architecture; index/query/MCP pillar in the dated usage observation. |
| Leverage | 25/25 | Compounds every other workflow: repo intelligence, signal capture, nightly dream cycle, retrieval, task prep, and durable memory. |
| Reuse readiness | 18/20 | Dated clone/CLI checks succeeded; agent-facing docs and skillpack are unusually strong. Main friction is operational complexity and provider/search-mode setup. |
| Maturity/trust | 13/15 | MIT, active repo, 18k+ stars, 2.6k forks, 200 test files, 72 docs, 47 skills, explicit security boundaries. Still fast-moving; operational health needs separate validation. |
| Differentiation | 15/15 | Hybrid vector/BM25/RRF/graph retrieval + write-through Markdown + MCP + skillpack + Minions is meaningfully different from generic RAG or Obsidian plugins. |
| **Total** | **96/100** |  |

## Verdict

**Core infrastructure; do not replace with a sidecar wiki unless the sidecar is clearly bounded.** In an architecture where GBrain already indexes the canonical Obsidian/Git vault, it serves as the AI/index/query layer. Its value is the operating model: Markdown as system of record, Postgres/PGLite retrieval, hybrid search plus typed graph, MCP exposure, skillpack routing, and agent-run maintenance. Keep those responsibilities healthy and avoid parallel repo-intelligence or memory stores.

## Reference-stack relevance

- As a core index/query component in the reference architecture, improvements compound across workflows rather than creating another sandbox.
- It aligns with the north star: a self-improving Hermes/second-brain system that reduces repeated context loading and turns accumulated notes, repositories, and meetings into usable leverage.
- It gives Hermes a principled memory layer: brain-first lookup, source routing, sync, graph traversal, and skill-based workflows.
- **Reuse before building:** leverage GBrain's production brain architecture instead of building a custom memory/index system from scratch.

## Reuse / inspiration potential

- **Direct reuse:** yes under the dated reference-stack observation. Keep using it as the index/query/MCP layer over the canonical second-brain vault.
- **Pattern to borrow:** two-axis `brain` vs `source` routing, Markdown repo as system of record, typed-edge extraction on write, MCP remote/trusted boundary, skillpack resolver, doctor/remediation loops, eval replay for retrieval changes.
- **Workflows improved:** Hermes memory, second-brain retrieval, repo intelligence, context bridging, dream-cycle, task preparation, and autonomous maintenance.
- **Autonomy leverage:** high. `gbrain doctor`, skillpack workflows, Minions, cron/autopilot, and retrieval evals give agents concrete mechanisms for self-maintenance instead of vibes.
- **Operational leverage:** a healthier knowledge index can reduce manual context reconstruction and repeated decisions, improve project continuity, and speed conversion of raw inputs into decisions/actions.

## What it is

GBrain is a TypeScript/Bun CLI, MCP server, and knowledge-brain engine for personal/agent memory. It stores human-readable Markdown in a git-backed brain repo as the system of record, syncs it into PGLite or Postgres/pgvector, and exposes retrieval, graph, timeline, capture, ingestion, eval, skillpack, and maintenance operations to agents and shells.

Key shape:

- CLI binary: `gbrain` from `src/cli.ts`.
- Package: `gbrain`, version `0.39.0.0` in the review environment; latest inspected git commit was `v0.39.1.0 feat: schema packs`.
- Engines: zero-config PGLite for personal installs; Postgres/pgvector for larger/team brains.
- Retrieval: vector + BM25 + RRF + source-aware rank + graph augmentation + optional reranking / expansion.
- Agent surface: MCP stdio/HTTP, operation definitions, skillpack, resolver, and docs for agent workflows.

## Evidence checked

- **GitHub metadata:** `garrytan/gbrain`; TypeScript; MIT; 18,680 stars; 2,625 forks; pushed `2026-05-24`; default branch `master`; public and not archived.
- **Inspected upstream revision:** `5a2bdd20 2026-05-22 v0.39.1.0 feat: schema packs (#1248)` from `https://github.com/garrytan/gbrain.git`.
- **README/docs:** checked `README.md`, `AGENTS.md`, `docs/architecture/brains-and-sources.md`, `docs/architecture/RETRIEVAL.md`.
- **Package/code:** checked `package.json`, `src/core/engine.ts`, `src/core/operations.ts`, `src/mcp/server.ts`.
- **Repo scale:** 1,706 tracked files; 499 TypeScript source files; 200 test files; 72 docs Markdown files; 47 skill `SKILL.md` files.
- **Dated smoke test (2026-05-24):** `gbrain --version` returned `gbrain 0.39.0.0`; `gbrain doctor --json` connected successfully. Private instance-health findings are not upstream product evidence.
- **repomix pack:** not generated; local checkout was available and targeted source/doc inspection was enough for this analysis.

## Verified / plausible / source claims

- **Verified at review:** the inspected CLI supported `gbrain --version` and `gbrain doctor`; this is dated execution evidence, not a live reader-environment claim.
- **Verified:** The repo exposes `gbrain` as a Bun CLI, has explicit package exports, and has scripts for unit tests, full verification, E2E, local CI, schema/docs builds, and privacy/security checks.
- **Verified:** MCP stdio dispatch treats callers as remote/untrusted by default, while local `gbrain call` uses a trusted context; file upload validation has strict vs loose modes.
- **Verified:** Architecture docs define the important `brain` vs `source` routing model and the retrieval stack: vector, BM25, RRF, graph augmentation, source-aware ranking, reranking, and query expansion.
- **Operational caveat:** resolver, graph/timeline coverage, frontmatter and sync health require instance-specific checks; such findings do not alone establish upstream product defects.
- **Plausible:** The README benchmark claims are directionally credible because the repo has eval docs/harnesses, but the exact headline numbers were not independently reproduced in this run.
- **Source claim:** Production-scale claims about Garry's personal deployment and BrainBench headline metrics come from the README and should be treated as upstream claims unless separately replicated.

## Strengths

- **Best possible stack fit:** It is the preferred bridge between canonical Markdown and agent retrieval/MCP workflows under the dated reference-stack lens.
- **Strong architecture:** Separating brain DBs from sources prevents a common personal-KB failure mode: mixing data ownership, topic boundaries, and physical repos into one overloaded namespace.
- **Retrieval is not generic RAG:** Hybrid lexical/vector retrieval plus typed graph traversal targets relationship queries common to personal and organizational knowledge systems.
- **Markdown remains canonical:** This preserves human control, git history, Obsidian compatibility, and low lock-in.
- **Agent-native:** `AGENTS.md`, skillpack resolver, MCP server, operations definitions, and doctor/remediation workflows are designed for agents to operate the system rather than just read docs.
- **Security-aware:** The local vs remote operation boundary and stricter MCP upload behavior are the right shape for letting agents touch personal data.
- **Testing/docs depth:** 200 test files, 72 docs, and many dedicated check scripts signal a serious operational project, not a thin demo.

## Risks / caveats

- **Operational complexity:** This is powerful infrastructure, not a tiny Obsidian plugin. Search modes, embeddings, rerankers, PGLite locks, sync failures, migrations, and source routing need care.
- **Fast-moving upstream:** Local package version and latest commit/release language can drift quickly; upgrades should stay behind `safe-gbrain-upgrade` discipline.
- **Operational health:** Building more automation on an unhealthy index risks compounding bad retrieval; validate health before extending automation.
- **Provider dependencies:** Best retrieval quality may depend on external embedding/reranker providers such as ZeroEntropy/OpenAI/Voyage.
- **Benchmark claims need local validation:** The README's retrieval numbers should not substitute for representative workflow-specific eval replay on the intended corpus.
- **Not the canonical vault:** GBrain should index and operate over the canonical Markdown vault; it should not become a competing human knowledge store.

## Integration ideas

- Make the repo-intelligence rollup and repo notes first-class GBrain sources for repo-intelligence queries.
- Candidate: a recurring health check reporting actionable `gbrain doctor --json` deltas after a bounded baseline review.
- Use `gbrain eval export/replay` before changing retrieval config or source boosts for the second-brain corpus.
- Treat `gbrain capture` as the default low-friction capture path for Discord/voice/link ingestion once filing rules are clear.
- Use `source` boundaries deliberately: curated Markdown remains canonical; context bridge and generated sandboxes should not silently contaminate canonical retrieval unless explicitly synced.

## Alternatives / related repos

- [atomicstrata/llm-wiki-compiler](atomicstrata--llm-wiki-compiler.md) — useful bounded compiler/review sandbox, but should complement GBrain rather than replace the canonical index/query layer.
- [SamurAIGPT/llm-wiki-agent](SamurAIGPT--llm-wiki-agent.md) — strong pattern source for agent-maintained wiki workflows, but less mature as operational infrastructure than GBrain.

## Review candidates and guidance

- Review candidate: validate frontmatter on a copied corpus, review any proposed fixes, then re-run doctor; do not infer write authority from this note.
- Review candidate: Run graph/timeline extraction cleanup (`gbrain extract all` if appropriate) after confirming cost/scope.
- Review candidate: add a lightweight recurring GBrain health report only after checking the instance baseline and authorizing its scope.
- Review candidate: Build a reference-workflow-specific retrieval eval set from recent second-brain/repo-intelligence queries before changing search modes or source boosts.
