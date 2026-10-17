---
title: Context / Memory / Code Intelligence Repo Comparison
created: 2026-05-27
updated: 2026-05-27
type: comparison
tags: [github-repos, context, memory, code-intelligence, mcp, repo-intelligence]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/andrewyng--context-hub.md
  - wiki/intel/github-repos/repos/CodeGraphContext--CodeGraphContext.md
  - wiki/intel/github-repos/repos/NevaMind-AI--memU.md
  - wiki/intel/github-repos/repos/oraios--serena.md
  - wiki/intel/github-repos/repos/upstash--context7.md
---

# Context / Memory / Code Intelligence Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Install/sandbox first:** [oraios/serena](../repos/oraios--serena.md) — best immediate Hermes coding-agent leverage.
- **Use tactically:** [upstash/context7](../repos/upstash--context7.md) — excellent external library docs lookup, but hosted/private-backend and not personal memory.
- **Distill patterns:** [andrewyng/context-hub](../repos/andrewyng--context-hub.md) for local docs annotations; [NevaMind-AI/memU](../repos/NevaMind-AI--memU.md) for shadow memory bot/proactive-memory lifecycle; [CodeGraphContext/CodeGraphContext](../repos/CodeGraphContext--CodeGraphContext.md) for code graph reports/bundles.
- **Do not build custom yet:** the existing ecosystem already covers semantic code editing, docs lookup, and proactive memory patterns. The next custom work should be thin integration/policy/eval, not a new context platform.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [oraios/serena](../repos/oraios--serena.md) | 24 | 13 | Medium | MIT | Mostly local | Sandbox now as coding-agent MCP sidecar. |
| [upstash/context7](../repos/upstash--context7.md) | 21 | 13 | Low | MIT | No — hosted docs service | Use tactically for external docs; avoid global always-on rule. |
| [CodeGraphContext/CodeGraphContext](../repos/CodeGraphContext--CodeGraphContext.md) | 21 | 13 | Medium | MIT | Yes | Compare against GBrain before adoption. |
| [andrewyng/context-hub](../repos/andrewyng--context-hub.md) | 20 | 12 | Low | MIT | Partly — open markdown + local annotations | Distill annotation loop; use ad hoc if coverage fits. |
| [NevaMind-AI/memU](../repos/NevaMind-AI--memU.md) | 18 | 12 | High | Apache-2.0 file; GitHub says Other | Self-host possible | Distill proactive memory pattern; avoid parallel memory store. |

## Category map

This sprint split the “context” problem into four different surfaces:

1. **Code structure context** — semantic/project-aware tools that help agents navigate and edit code. Serena and CodeGraphContext live here.
2. **External documentation context** — tools that fetch current library/API docs. Context7 and Context Hub live here.
3. **Personal/proactive memory** — tools that capture user/agent history and predict future needs. memU lives here.
4. **Policy/eval/integration layer** — the part the reference stack needs to build: when to call which context source, how to avoid prompt pollution, and how to measure whether it helped.

## Repo-by-repo notes

### [oraios/serena](../repos/oraios--serena.md)

Best immediate candidate. It gives coding agents LSP/IDE-style symbol retrieval and semantic edits via MCP. Smoke test succeeded locally with `uvx --from serena-agent serena --help`. Sandbox before broad enablement because its generic file/shell tools overlap with Hermes' existing tools.

### [upstash/context7](../repos/upstash--context7.md)

Best tactical docs lookup. The hosted/private backend is a conscious trade-off: high utility for current library docs, lower local-first purity. Use for library/API questions, not as personal memory or repo-local truth.

### [CodeGraphContext/CodeGraphContext](../repos/CodeGraphContext--CodeGraphContext.md)

Good graph-analysis reference. It has reports, graph DB backends, MCP, and CLI commands. But because GBrain already has code graph tools, the next step is side-by-side capability comparison, not immediate adoption.

### [andrewyng/context-hub](../repos/andrewyng--context-hub.md)

Best small pattern: local annotations attached to docs. That pattern should influence Hermes skills/reference files so repeated API gotchas become durable without bloating global memory.

### [NevaMind-AI/memU](../repos/NevaMind-AI--memU.md)

Best proactive-memory inspiration but wrong as a direct dependency right now. The two-agent lifecycle and memory-as-filesystem model are useful; adding another canonical memory system is not.

## Conditional reference-stack guidance

Recommended priority order: **Serena first**, then documentation lookup, then memory/docs patterns; only then compare CodeGraphContext with GBrain. Match each experiment to the capability gap it addresses:

1. If symbol navigation or semantic edits are the gap, compare **Serena** on a non-critical repo with and without its tools.
2. If current external library documentation is needed, test **Context7** ad hoc and measure value against request noise and hosting/privacy costs.
3. If local documentation or proactive recall is the gap, compare Context Hub and memU patterns for annotations and shadow-memory lifecycle before integrating any procedure.
4. Compare **CodeGraphContext and GBrain** only when graph/report capabilities are needed beyond the current query layer.

## Open questions

- Does Serena reduce actual edit mistakes in Hermes/GBrain repos, or only feel smarter?
- Should Hermes have a context policy skill: “repo-local → GBrain/Serena; external docs → Context7/chub; personal memory → GBrain/memory; never blindly merge sources”?
- Which docs tool has better coverage for the reference stack's real libraries: Context7 or Context Hub?
- Can memU's proactive-memory lifecycle be reproduced with existing Hermes cron/dream-cycle + GBrain facts without importing its runtime?

## Evidence log

- Live GitHub metadata fetched with `gh repo view` on 2026-05-27.
- README, manifest, and license/community files inspected from disposable source copies.
- Smoke tests run:
  - `npx --yes @aisuite/chub --help` succeeded.
  - `npx --yes ctx7 --help` succeeded with a Node engine warning.
  - `uvx --from codegraphcontext codegraphcontext --help` succeeded.
  - `uvx --from serena-agent serena --help` succeeded.
- memU runtime smoke test intentionally skipped because package requires Python 3.13 and examples need provider/DB setup.
