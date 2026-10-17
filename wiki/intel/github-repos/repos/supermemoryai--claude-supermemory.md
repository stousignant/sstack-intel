---
title: supermemoryai/claude-supermemory
type: repo-intel
aliases:
  - claude-supermemory
  - GitHub repo: supermemoryai/claude-supermemory
source: https://github.com/supermemoryai/claude-supermemory
category: agent-memory
topics: [github-repo, repo-intelligence, agent-memory, context-management]
status: deep-analyzed
usefulness_score: 62
recommendation: watch
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: NOASSERTION
---

# supermemoryai/claude-supermemory

> Reference-stack evaluation as reviewed 2026-05-30; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `62/100` — Clean team-memory UX for Claude Code, but SaaS/Pro requirements, API keys, unknown repository license, and Claude-specific plugin shape make it a watch/reference item rather than default infrastructure.
- **Recommendation:** `watch`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Do not adopt. Use only as a UX reference for team/project memory commands and logout/session affordances.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 14/25 | Relevant to Hermes/GBrain/context/memory workflows, with varying risk of duplicate canonical stores. |
| Leverage | 17/25 | Could improve recall, context budget, code navigation, or session continuity if bounded correctly. |
| Reuse readiness | 14/20 | README/manifests provide install paths; safe adoption still requires sandboxing and boundary checks. |
| Maturity/trust | 7/15 | Live metadata: 2590 stars, 152 forks, pushed 2026-05-29T04:29:03Z, license unknown. |
| Differentiation | 10/15 | Differentiates mainly by evals, hooks, UX, or low-token code/context tools versus current Hermes/GBrain stack. |

## Verdict

Clean team-memory UX for Claude Code, but SaaS/Pro requirements, API keys, unknown repository license, and Claude-specific plugin shape limit its fit. The default should be one canonical memory/index layer: use the selected runtime memory and session search with GBrain and the second-brain vault where applicable. Consider another tool only if it improves a specific boundary—recall quality, context-budget observability, code-navigation speed, or team/shared-memory UX—without creating a second truth store.

## Workload fit

- Where a deployment already has memory and search, the leverage is not “more memory” but **better evaluated recall with clean ownership boundaries**.
- Agent hooks and MCP context tools can save tokens/time, but they also increase ambient capture and secret-leak risk.
- Good patterns here can make Hermes more self-improving: session capture, compaction, retrieval evals, purge/logout controls, and low-token code context.

## What it is

Claude-Supermemory is a Claude Code plugin that connects sessions to Supermemory, enabling project/team memories, commands for search/save/index/config, and Supermemory-hosted session documents.

## Live metadata checked

- Source: <https://github.com/supermemoryai/claude-supermemory>
- Description: Enable Claude Code to learn in real-time, update it's knowledge, and grow with you, using supermemory.
- Stars / forks: 2590 / 152
- Primary language: JavaScript
- License: unknown
- Latest release: v0.0.2 / 2026-02-09T01:05:12Z
- Last pushed: 2026-05-29T04:29:03Z
- Topics: none listed

## Evidence checked

- GitHub metadata via `gh repo view supermemoryai/claude-supermemory` on 2026-05-30.
- [Upstream README](https://github.com/supermemoryai/claude-supermemory/blob/main/README.md) inspected.
- License, package manifest, security policy, and top-level contents where present from the upstream repository.

## Strengths

- Simple command surface: super-search, super-save, project index/config, logout, and session URL.
- Clear separation between global settings and per-project config.
- Useful UX reference for team-memory affordances and explicit credential logout.

## Risks / caveats

- Requires Supermemory Pro or above and a Supermemory API key; not local-first.
- No licenseInfo from GitHub metadata and no license file detected in evidence fetch.
- Its SaaS requirement and API key conflict with local-first/canonical-memory constraints unless a concrete team/SaaS use case justifies them.

## Integration ideas

- Steal the UX pattern of explicit memory save/search/index commands and a visible session document link.
- Credential lifecycle/logout command is a good affordance for any future memory integration.

## Alternatives / related repos

- [thedotmack/claude-mem](thedotmack--claude-mem.md)
- [rohitg00/agentmemory](rohitg00--agentmemory.md)
- [supermemoryai/claude-supermemory](supermemoryai--claude-supermemory.md)
- [forloopcodes/contextplus](forloopcodes--contextplus.md)
- [mksglu/context-mode](mksglu--context-mode.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [oraios/serena](oraios--serena.md)
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md)

## Review guidance

- No durable action beyond watch/reference; reconsider only for a defined team-memory workflow with explicit data and licensing review.
- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
