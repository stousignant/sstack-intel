---
title: Memory OS vs GBrain / Current Setup
created: 2026-06-07
updated: 2026-06-07
type: comparison
tags: [github-repos, repo-intelligence, memory, hermes, gbrain, second-brain]
sources:
  - wiki/intel/github-repos/repos/ClaudioDrews--memory-os.md
  - wiki/intel/github-repos/repos/garrytan--gbrain.md
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
---

# Memory OS vs GBrain / Current Setup

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

**Keep GBrain + the canonical Markdown vault as the active memory/index layer. Do not install Memory OS wholesale into the reviewed Hermes profile.**

Memory OS is a strong Hermes-native **pattern source** for context injection and memory obedience. Adopting it directly would create a second memory substrate — Qdrant, Redis, Fabric, facts DB, wiki folder, cron, and rulebook patches — beside the dated Hermes + `session_search` + GBrain + canonical Markdown-vault setup.

Default move under the reviewed architecture:

1. **Distill Memory OS patterns** into Hermes/GBrain operations.
2. **Add observability/evals** that prove whether injected memory is actually used.
3. **Only sandbox the Memory OS runtime** in a separate Hermes profile/VM if runtime behavior needs evidence.

## Decision matrix

| Capability | Memory OS | Dated reference setup | Verdict |
|---|---|---|---|
| Canonical human-editable knowledge | `$VAULT_PATH/wiki/` generated/curated wiki layer | Canonical Markdown/Obsidian/Git vault | Current setup wins; do not create a competing canonical wiki. |
| Agent index/query layer | Qdrant `knowledge_base` + BM25 fallback | GBrain PGLite/Postgres-style hybrid search, graph, timeline, MCP, facts, schema packs | GBrain wins for canonical stack fit and graph/source model. |
| Session recall | SQLite FTS5 over Hermes `state.db`, injected into prompts | Hermes `session_search` tool + persistent memory injection | Memory OS has useful auto-injection patterns; current setup has mature explicit lookup. |
| Structured facts | `memory_store.db` facts/entities/trust scoring | Hermes persistent memory + GBrain facts/takes/recall/extraction | Pattern worth stealing; direct DB duplication is bad. |
| Pre-LLM injection | Icarus hooks search Fabric/Qdrant/sessions/facts and collapse sources | Hermes system/developer memory injection + MCP/tools; GBrain queried explicitly/on demand | Memory OS has the sharper pattern for injection observability and collapse. |
| Ground-truth hierarchy | Explicit instruction that injected memory is authoritative | Hermes persona/memory/tool-use discipline; GBrain pages cited from canonical vault | Borrow carefully; live tool output still outranks stale memory. |
| Local-first posture | Docker Qdrant/Redis + local SQLite/wiki | Local Hermes + GBrain over Git vault, mostly local; embeddings/providers configurable | Both aligned, but Memory OS adds more daemons. |
| Install/migration cost | Invasive installer mutates the Hermes configuration home, `.env`, crontab, Docker, rulebook, gateway | Assumes an existing retrieval layer; verify operational health separately in private | Current setup wins; Memory OS must be sandboxed first. |
| Maturity | Very young, fast-moving, good tests for sanitizer/collapse | GBrain active local tool, already integrated, repo-intelligence notes exist | Current setup wins for workload-specific operational maturity. |

## What Memory OS adds that is worth reusing

1. **Memory obedience as a first-class problem.** The repo correctly names the gap between “context was retrieved” and “the agent actually used it.”
2. **Injected-context precedence rules.** Define documented prior decisions as authoritative unless live wiki, tools, or documentation contradict them.
3. **Source collapse.** Multiple memory hits should become a small fused packet, not a pile of unrelated snippets.
4. **Social-closer gating.** Skip retrieval for “ok / thanks / 👍” style messages.
5. **Injection telemetry.** Log what was injected, token count, score/source, and whether the model then wasted tools rediscovering the same fact.
6. **Smoke-test mindset.** A single command should verify memory plumbing end-to-end instead of assuming the agent remembers because services are running.
7. **Prompt-injection sanitizer tests.** Keep tests around retrieved-context sanitization, especially if arbitrary wiki/source text is injected into system context.

## What to reject or sandbox only

- **Default one-command install into live Hermes.** Too much uncontrolled mutation: plugin copy, SQLite schemas, `.env`, cron, Docker services, rulebook append, gateway restart.
- **A second canonical wiki.** The reviewed canonical knowledge layer is a Markdown vault indexed by GBrain. Memory OS' `$VAULT_PATH/wiki` must not become a parallel truth store.
- **Another always-on vector DB.** GBrain already handles retrieval/indexing in the reviewed setup. Add Qdrant only for an isolated bakeoff.
- **Fact store duplication.** A second `memory_store.db` with trust scoring creates conflict unless it is folded into the existing Hermes/GBrain fact model.
- **Global prompt hierarchy edits.** Useful pattern, but any precedence rule must respect the real authority chain: user/system/developer instructions, live tool output for runtime state, official docs for APIs, and memory for documented context.

## Recommended integration plan

### 1. No install by default

Treat [ClaudioDrews/memory-os](../repos/ClaudioDrews--memory-os.md) as `recommendation: distill-pattern`, `usage: reference-only` until a sandbox proves direct value.

### 2. Create a recall bakeoff before adding memory stores

Build 10–20 workload-specific queries before evaluating another store:

- “Which source owns canonical knowledge for this project?”
- “Which storage/concurrency caveats require instance-level verification?”
- “Where should repository research notes live in this knowledge system?”
- “Which source owns operating state, and how should recall distinguish it from reusable knowledge?”
- “What trade-offs were recorded between wiki compilers and the current retrieval layer?”

Run the same query set through the existing memory, session-recall, and index/query layers before comparing Memory OS in a sandbox.

### 3. Add injection/rediscovery telemetry

The highest-leverage improvement is not more memory. It is proving whether memory changes behavior.

A useful local metric:

```text
For each turn:
  injected_context = {source, id/slug, score, tokens, summary}
  subsequent_tool_calls = search/read/session/gbrain calls
  rediscovery_flag = tool call repeats an injected fact/source
  outcome = answered_from_memory | verified_needed | avoidable_rediscovery | stale_memory_corrected
```

This telemetry can help distinguish retrieval misses from model-behavior failures without requiring another canonical memory store.

### 4. Sandbox Memory OS only if needed

If runtime evidence is needed:

- Use a separate Hermes profile or disposable VM.
- Do **not** point the first run at canonical or confidential data.
- Capture before/after diffs for the isolated runtime configuration, schedules, containers, and generated knowledge files.
- Run the provided smoke test plus a tiny recall scenario.
- Compare against GBrain on the same recall questions.

## Verdict for the reviewed architecture

Memory OS and GBrain address adjacent but different capabilities: Memory OS emphasizes **automatic context injection and memory obedience**; the reviewed GBrain integration emphasizes **querying, graphing, and operating on canonical Markdown knowledge**.

The right architecture under the dated review was:

```text
Hermes = active cockpit / tool loop / skills / messaging runtime
Existing project/tool owners = operating-state ownership
GBrain = active index/query/graph/MCP layer over that truth
Wikic = deterministic vault checks/review substrate
Memory OS = pattern source for injection, recall collapse, telemetry, and memory obedience
```

Bluntly: installing Memory OS wholesale into this reviewed setup would be infrastructure sprawl. Reuse its best ideas; keep GBrain and the canonical Markdown vault as the active memory/index layer.

## Open questions

- Does the reviewed GBrain/Hermes integration expose enough hook surface to log “injected memory used vs rediscovered,” or would this require a plugin?
- Should Memory OS' source-collapse idea become a Hermes skill/plugin feature or a GBrain `recall packet` feature?
- Are the reference stack's current memory failures primarily retrieval misses, stale/conflicting memory, or model-behavior failures after good context is already present?
