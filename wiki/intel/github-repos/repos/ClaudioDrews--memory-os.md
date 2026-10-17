---
title: ClaudioDrews/memory-os
type: repo-intel
aliases:
  - Memory OS
  - GitHub repo: ClaudioDrews/memory-os
source: https://github.com/ClaudioDrews/memory-os
category: memory-management
topics: [github-repo, hermes-agent, memory, qdrant, persistent-memory, context-injection, llm-wiki, local-first]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-07
license: MIT
---

# ClaudioDrews/memory-os

> Reference-stack evaluation as reviewed 2026-06-07. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — very high relevance because it targets Hermes memory directly, but it overlaps heavily with the reviewed Hermes + GBrain + canonical Markdown stack and should not be installed wholesale.
- **Recommendation:** `distill-pattern` — mine the concrete patterns around pre-LLM context injection, source collapse, ground-truth hierarchy, smoke tests, and memory-layer diagnostics; do not make it the canonical memory substrate.
- **Usage observed 2026-06-07:** `reference-only`. Inspected in a disposable clone; not adopted as a runtime.
- **Review candidate:** Extract a bounded checklist for improving the reviewed stack: injection observability, recall bakeoff questions, and safer context-precedence rules. If runtime behavior is tested, use a separate Hermes profile or disposable VM first.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | Hermes-native, local-first, and directly about persistent memory; poor fit as a wholesale install because it creates parallel Qdrant/wiki/fact/fabric layers beside GBrain and the canonical vault. |
| Leverage | 22/25 | The best ideas attack real pain: memory-zero behavior, context injection, structured facts, session recall, and self-curating wiki loops. |
| Reuse readiness | 15/20 | One-command installer, docs, Docker compose, smoke tests, and CI exist; but the installer mutates live Hermes config/state/cron/services and needs a sandbox-first path. |
| Maturity/trust | 11/15 | MIT, popular for its age, recently pushed, with tests passing locally; still extremely young and fast-moving. |
| Differentiation | 13/15 | Strong differentiated packaging for Hermes memory/injection; less differentiated against an existing combination of Hermes memory, `session_search`, GBrain, and Wikic/second-brain. |
| **Total** | **82/100** |  |

## Verdict

**Do not install Memory OS into the default Hermes profile.** It is a valuable design reference, not a replacement for the reviewed stack. Reuse its strongest ideas—explicit memory-authority hierarchy, injection telemetry, source collapse, social-closer gating, prompt-injection sanitization, and one-command smoke tests—while keeping curated Markdown canonical and GBrain the index/query/graph layer.

## Reference-stack relevance

- It is built specifically for Hermes Agent, so its patterns map more directly to this cockpit than generic memory tools such as Zep/mem0/Letta-style systems.
- It highlights an important failure mode: captured memory is not enough; agents need clear rules, observability, and evals proving the injected context is actually used.
- It gives a concrete reference architecture for layering session recall, fact memory, vector retrieval, wiki curation, and prompt precedence.
- It also shows what **not** to do here: create another canonical wiki and vector store when GBrain and the Markdown/Git vault already own that job.

## What it is

Memory OS is a Hermes Agent memory stack with seven advertised layers:

1. Workspace memory files (`MEMORY.md`, `USER.md`, `CREATIVE.md`).
2. Session history in SQLite/FTS5.
3. Structured facts in `memory_store.db` with entities, trust scores, and FTS5.
4. A modified Icarus plugin exposing Fabric tools and lifecycle hooks.
5. Qdrant vector search with dense + BM25 sparse retrieval and fallback paths.
6. A local LLM wiki pipeline under `$VAULT_PATH/wiki/`.
7. A “Ground Truth hierarchy” identity/instruction layer that tells the agent to treat injected memory as authoritative.

It installs Docker services for Redis, Qdrant, and an ARQ worker, plus Hermes plugin/hooks, SQLite schemas, cron ingestion, and rulebook amendments.

## Evidence checked

- **GitHub metadata:** `ClaudioDrews/memory-os`; Python; MIT; 1,000 stars; 93 forks; created `2026-05-31`; pushed `2026-06-07`; not archived.
- **README/Quickstart:** claims seven layers, one-command install, Docker/Qdrant/Redis worker, Icarus plugin, fact store, LLM wiki, and ground-truth hierarchy.
- **Files inspected:** `README.md`, `QUICKSTART.md`, `setup.sh`, `setup/install.md`, `docker/docker-compose.yml`, `icarus/plugin.yaml`, `icarus/hooks.py`, `icarus/tools.py`, `scripts/context_enhancer.py`, `setup/setup_db.py`, `layers/03-fact-store.md`, `layers/05-qdrant.md`, `layers/06-llm-wiki.md`, `layers/07-ground-truth.md`, `.github/workflows/ci.yml`.
- **Local smoke test:** inspected in a disposable clone of [the upstream repository](https://github.com/ClaudioDrews/memory-os); `python3 -m compileall -q icarus scripts setup _test_collapse.py _test_sanitize.py` passed; `_test_sanitize.py` reported `ALL 24 TESTS PASS`; `_test_collapse.py` reported `ALL COLLAPSE TESTS PASS`.
- **Reference comparison lens (2026-06-07):** Hermes for agent execution/session memory, GBrain for index/query/graph, and curated Markdown for canonical knowledge. Private runtime-health measurements are not upstream evidence.

## Verified / plausible / source claims

- **Verified:** the repo has a Hermes plugin manifest exposing 16 Fabric tools and four lifecycle hooks: `on_session_start`, `pre_llm_call`, `post_llm_call`, and `on_session_end`.
- **Verified:** `setup.sh` targets the default Hermes home, creates separate Memory OS and wiki/fabric directories, starts Docker services, installs a cron job, appends rulebook text, and restarts the Hermes gateway.
- **Verified:** Docker compose binds Redis and Qdrant to localhost and mounts wiki read-only, Hermes/fabric read-write into the worker.
- **Verified:** context injection code includes social-closer gating, Qdrant search fail-open behavior, FTS session lookup, fact lookup, prompt-injection sanitization, and context collapse logic.
- **Verified:** local syntax and included pure tests pass without installing the stack.
- **Source claim:** production effectiveness, “actually works,” and memory-behavior improvements are README claims; they were not validated in a live Hermes runtime.
- **Plausible:** the Ground Truth hierarchy is a real pattern worth borrowing, but it must be reconciled with Hermes' existing system/developer hierarchy and tool-use discipline.

## Strengths

- **Hermes-native shape:** lifecycle hooks and plugin tools are directly relevant to this environment.
- **Good diagnosis:** the repo correctly separates memory capture, retrieval, context injection, and agent obedience to injected memory.
- **Concrete tests:** sanitizer/collapse tests and CI are more serious than a pure README demo.
- **Local-first posture:** Docker Qdrant/Redis, SQLite, local wiki files, and provider-agnostic LLM extraction may suit workloads that prioritize locally inspectable components.
- **Operational packaging:** a smoke test and explicit layer docs make it easier to audit than many memory projects.
- **Useful safety ideas:** prompt-injection sanitization, social-closer filtering, fail-open retrieval, and per-session deduplication are worth stealing.

## Risks / caveats

- **Competing brain risk:** the default wiki directory and Qdrant `knowledge_base` layer would compete with the canonical Markdown vault + GBrain unless deliberately integrated.
- **Installer is too invasive for default profile:** it copies a plugin into the default Hermes home, creates/changes SQLite DBs, writes `.env`, installs cron, appends rulebook text, starts Docker services, and restarts the gateway.
- **Potential Python hygiene issue:** `setup.sh` falls back to `pip install --break-system-packages`, which is exactly the kind of global mutation to avoid on this host.
- **Resource/ops overhead:** Redis + Qdrant + worker + cron add another always-on substrate; database and background-worker lock behavior need explicit ownership and operational checks.
- **Young repo:** created one week before this review; popularity is impressive but not the same as production maturity.
- **Security boundary:** a read-write mount of Hermes home/fabric into the worker and prompt/context injection paths deserve a dedicated sandbox audit before live install.
- **Conceptual overlap:** fact store, session recall, vector search, wiki curation, and memory injection overlap with existing Hermes memory, `session_search`, GBrain facts/search/graph, Wikic, and the canonical vault.

## Reference-stack comparison

See [Memory OS vs GBrain / Current Setup](../comparisons/memory-os-vs-gbrain-current-setup.md) for the side-by-side recommendation.

Short version: Memory OS is a stronger **memory-injection reference** than a stack migration candidate. Where GBrain indexes a curated Markdown vault, it remains the canonical **index/query/graph layer** rather than Memory OS.

## Integration ideas

- Add a GBrain/Hermes **injection observability check**: when memory is injected, log source, score, tokens, and whether the agent reused it or re-searched anyway.
- Turn Memory OS' Ground Truth hierarchy into a local **context precedence note** that respects Hermes' system/developer/tool hierarchy without pretending injected memory outranks live terminal/tool output.
- If a memory-sidecar decision is active, define 10–20 workload-specific recall questions and compare Hermes/GBrain/`session_search` performance before adding another substrate.
- Steal the smoke-test pattern: one command should verify session DB, GBrain source sync, embeddings coverage, tool availability, and no competing background lock owner.
- If testing Memory OS runtime, create a separate Hermes profile and separate vault path; never point it at the canonical profile/vault on the first run.

## Alternatives / related repos

- [garrytan/gbrain](garrytan--gbrain.md) — active index/query/graph layer; keep as canonical.
- [Gentleman-Programming/engram](Gentleman-Programming--engram.md) — small local SQLite/FTS/MCP memory sidecar; pattern source only until a bakeoff exists.
- [MemPalace/mempalace](MemPalace--mempalace.md) — verbatim-memory and benchmark reference; useful for eval design.
- [NevaMind-AI/memU](NevaMind-AI--memU.md) — proactive/shadow-memory patterns; direct adoption risks parallel truth.
- [NateBJones-Projects/OB1](NateBJones-Projects--OB1.md) — open-brain architecture reference; overlaps with GBrain/second-brain.
- [plastic-labs/honcho](plastic-labs--honcho.md) — managed/self-hosted memory DB; useful patterns, not canonical memory here.

## Review candidates and guidance

- Review candidate: Extract a small “memory injection observability” issue for Hermes/GBrain: prove when injected context is used vs ignored.
- Review candidate: Create a recall bakeoff question set before adopting any new memory store.
- Guidance: If runtime-testing Memory OS, use a disposable Hermes profile/VM and inspect changes to the profile, crontab, Docker services, and vault files before and after.
