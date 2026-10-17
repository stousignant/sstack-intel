---
title: Agent Context and Memory Repo Comparison
created: 2026-05-30
updated: 2026-05-30
type: comparison
tags: [github-repos, agent-memory, context-management, hermes, gbrain]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/forloopcodes--contextplus.md
  - wiki/intel/github-repos/repos/mksglu--context-mode.md
  - wiki/intel/github-repos/repos/rohitg00--agentmemory.md
  - wiki/intel/github-repos/repos/supermemoryai--claude-supermemory.md
  - wiki/intel/github-repos/repos/thedotmack--claude-mem.md
---

# Agent Context and Memory Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Sandbox first:** [forloopcodes/contextplus](../repos/forloopcodes--contextplus.md) — small MIT MCP sidecar with local Ollama default and concrete low-token code/context tools. Compare against GBrain/Serena/Graphify on copied repos.
- **Benchmark/reference:** [rohitg00/agentmemory](../repos/rohitg00--agentmemory.md) — strongest memory bakeoff candidate because it includes eval/benchmark framing and names Hermes, but do not adopt as a canonical store yet.
- **Distill:** [thedotmack/claude-mem](../repos/thedotmack--claude-mem.md) and [mksglu/context-mode](../repos/mksglu--context-mode.md) — steal hooks, compaction, stats/doctor/purge, and security patterns without importing a parallel context/memory runtime.
- **Watch only:** [supermemoryai/claude-supermemory](../repos/supermemoryai--claude-supermemory.md) — useful UX reference, but SaaS/Pro/API-key/unknown-license constraints are wrong-fit for the reference stack's local-first core stack.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [agentmemory](../repos/rohitg00--agentmemory.md) | 86 | 88 | High | Apache-2.0 | Mostly local/server, needs review | `distill-pattern`; benchmark before adopting. |
| [claude-mem](../repos/thedotmack--claude-mem.md) | 84 | 90 | High | Apache-2.0 | Local hooks/workers, but ambient capture | `distill-pattern`; mature memory-hook reference. |
| [Context+](../repos/forloopcodes--contextplus.md) | 82 | 72 | Medium | MIT | Yes with Ollama default | `adopt-now` for bounded code-context sandbox. |
| [Context Mode](../repos/mksglu--context-mode.md) | 80 | 82 | Medium-high | Elastic-2.0 | Local SQLite/FTS5, broad hooks | `distill-pattern`; context-budget UX reference. |
| [Claude-Supermemory](../repos/supermemoryai--claude-supermemory.md) | 62 | 62 | Medium | unknown | No, SaaS/Pro/API key | `watch`; UX reference only. |

## Category map

1. **Persistent agent memory:** claude-mem and agentmemory capture sessions and inject future context.
2. **Hosted/team memory:** claude-supermemory offers polished team/project memory commands, but depends on Supermemory SaaS.
3. **Code/context MCP sidecar:** Context+ focuses on AST/file skeletons, feature hubs, and memory graph search for codebases.
4. **Context-window optimizer:** Context Mode sandboxes tool output and indexes session events to reduce prompt bloat.

## Reference-stack recommendation

Do **not** add another canonical memory store. Context+ is the only direct sandbox candidate because it may improve code navigation without owning canonical memory. For other memory systems, run a bakeoff only after defining workload-specific recall questions. The most reusable patterns are explicit memory ownership, purge/logout controls, eval scripts, context-budget stats, and low-token summaries.

## Open questions

- What recall failures does the reference Hermes/GBrain stack exhibit: project decisions, coding sessions, user preferences, or source citations?
- Can Context+ answer code-navigation questions better than GBrain/Serena/Graphify without maintaining a parallel index?
- What data should never be captured by hooks: credentials, private Discord content, browser sessions, raw tool output, or private assistant notes?
- Which context-budget metric matters: token reduction, answer quality, latency, or lower compaction loss?
