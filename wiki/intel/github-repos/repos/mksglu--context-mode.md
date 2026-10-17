---
title: mksglu/context-mode
type: repo-intel
aliases:
  - context-mode
  - GitHub repo: mksglu/context-mode
source: https://github.com/mksglu/context-mode
category: context-window-optimization
topics: [github-repo, repo-intelligence, agent-memory, context-management]
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: Elastic-2.0
---

# mksglu/context-mode

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `80/100` — Very relevant context-window optimization and session-continuity design, but Elastic-2.0 license, broad hook enforcement, and plugin sprawl make it pattern material before adoption.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Distill sandboxed-tool-output, FTS5 session continuity, stats/doctor/insight commands, and routing-enforcement ideas into Hermes tooling guidance; only sandbox if token bloat becomes a concrete pain.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22/25 | Relevant to Hermes/GBrain/context/memory workflows, with varying risk of duplicate canonical stores. |
| Leverage | 23/25 | Could improve recall, context budget, code navigation, or session continuity if bounded correctly. |
| Reuse readiness | 14/20 | README/manifests provide install paths; safe adoption still requires sandboxing and boundary checks. |
| Maturity/trust | 10/15 | Live metadata: 16037 stars, 1153 forks, pushed 2026-05-30T12:22:01Z, license Elastic-2.0. |
| Differentiation | 11/15 | Differentiates mainly by evals, hooks, UX, or low-token code/context tools versus current Hermes/GBrain stack. |

## Verdict

Very relevant context-window optimization and session-continuity design, but Elastic-2.0 license, broad hook enforcement, and plugin sprawl make it pattern material before adoption. The default stance is **one canonical memory/index layer**: Hermes memory + session search + GBrain + the second-brain vault. These repos are valuable only when they improve a specific boundary — recall quality, context-budget observability, code-navigation speed, or team/shared-memory UX — without creating a second truth store.

## Reference-stack relevance

- The reference stack already has memory and search; the leverage is not “more memory,” it is **better evaluated recall with clean ownership boundaries**.
- Agent hooks and MCP context tools can save tokens/time, but they also increase ambient capture and secret-leak risk.
- Good patterns here can make Hermes more self-improving: session capture, compaction, retrieval evals, purge/logout controls, and low-token code context.

## What it is

Context Mode is an MCP/plugin system that reduces context-window bloat by sandboxing tool output, indexing session events in SQLite/FTS5, and routing agents toward compact analysis workflows across many coding platforms.

## Live metadata checked

- Source: <https://github.com/mksglu/context-mode>
- Description: Context window optimization for AI coding agents. Sandboxes tool output, 98% reduction. 15 platforms
- Stars / forks: 16037 / 1153
- Primary language: TypeScript
- License: Elastic-2.0
- Latest release: v1.0.151 / 2026-05-24T17:15:34Z
- Last pushed: 2026-05-30T12:22:01Z
- Topics: claude, claude-code, claude-code-plugins, mcp, skills, codex, copilot, opencode, antigravity, kiro, openclaw, claude-code-hooks, claude-code-skill, codex-cli, cursor-plugin, mcp-server, mcp-tools, pi-agent, zed-extension, context-mode

## Evidence checked

- GitHub metadata via `gh repo view mksglu/context-mode` on 2026-05-30.
- README from [upstream README](https://github.com/mksglu/context-mode/blob/HEAD/README.md).
- License, package manifest, security policy, and top-level contents where present under temporary upstream inspection material.

## Strengths

- Names the exact pain: raw MCP/tool outputs consuming context; README claims 315KB → 5.4KB style reductions and gives stats/doctor/upgrade/purge/insight commands.
- Session continuity model tracks edits, git operations, tasks, errors, and user decisions in SQLite/FTS5 instead of dumping everything into prompts.
- Multi-platform packaging across Claude Code, Codex, OpenClaw, OpenCode, Copilot/Gemini-style surfaces.

## Risks / caveats

- Elastic-2.0 is not as clean as MIT/Apache for remixing or hosted/service-like reuse.
- Hooks that enforce routing and sandbox tools could fight Hermes’ native tool discipline if installed blindly.
- Claims need a local token/quality benchmark; “98% reduction” alone does not prove better answers.

## Integration ideas

- Steal the principle Hermes already partially follows: programmatic tool/data reduction before context injection.
- Doctor/stats/purge/insight commands are good UX for any Hermes context-budget observability feature.

## Alternatives / related repos

- [thedotmack/claude-mem](thedotmack--claude-mem.md)
- [rohitg00/agentmemory](rohitg00--agentmemory.md)
- [supermemoryai/claude-supermemory](supermemoryai--claude-supermemory.md)
- [forloopcodes/contextplus](forloopcodes--contextplus.md)
- [mksglu/context-mode](mksglu--context-mode.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [oraios/serena](oraios--serena.md)
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md)

## Review candidates and context

- Patch Hermes/tool-use guidance later if there is a concrete gap around context-budget observability.
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
