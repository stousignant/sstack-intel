---
title: rohitg00/agentmemory
type: repo-intel
aliases:
  - agentmemory
  - GitHub repo: rohitg00/agentmemory
source: https://github.com/rohitg00/agentmemory
category: agent-memory
topics: [github-repo, repo-intelligence, agent-memory, context-management]
status: deep-analyzed
usefulness_score: 86
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: Apache-2.0
---

# rohitg00/agentmemory

> Reference-stack evaluation as reviewed 2026-05-30; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `86/100` — Best benchmark/eval-oriented persistent-memory candidate in this batch, with Hermes named as a target and explicit eval scripts, but still risks creating a parallel memory truth store.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Use as a benchmark/reference for memory evals; do not adopt until it beats Hermes session_search + GBrain on representative recall questions.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Relevant to Hermes/GBrain/context/memory workflows, with varying risk of duplicate canonical stores. |
| Leverage | 23/25 | Could improve recall, context budget, code navigation, or session continuity if bounded correctly. |
| Reuse readiness | 15/20 | README/manifests provide install paths; safe adoption still requires sandboxing and boundary checks. |
| Maturity/trust | 14/15 | Live metadata: 19933 stars, 1637 forks, pushed 2026-05-29T09:23:53Z, license Apache-2.0. |
| Differentiation | 11/15 | Differentiates mainly by evals, hooks, UX, or low-token code/context tools versus current Hermes/GBrain stack. |

## Verdict

Best benchmark/eval-oriented persistent-memory candidate in this batch, with Hermes named as a target and explicit eval scripts, but still risks creating a parallel memory truth store. The default stance is **one canonical memory/index layer**: Hermes memory + session search + GBrain + the second-brain vault. These repos are valuable only when they improve a specific boundary — recall quality, context-budget observability, code-navigation speed, or team/shared-memory UX — without creating a second truth store.

## Reference-stack relevance

- the reference stack already has memory and search; the leverage is not “more memory,” it is **better evaluated recall with clean ownership boundaries**.
- Agent hooks and MCP context tools can save tokens/time, but they also increase ambient capture and secret-leak risk.
- Good patterns here can make Hermes more self-improving: session capture, compaction, retrieval evals, purge/logout controls, and low-token code context.

## What it is

Agentmemory is an npm/TypeScript persistent-memory server for AI coding agents with MCP, hooks, REST/API, skills, session replay, and benchmark/eval tooling.

## Live metadata checked

- Source: <https://github.com/rohitg00/agentmemory>
- Description: #1 Persistent memory for AI coding agents based on real-world benchmarks
- Stars / forks: 19933 / 1637
- Primary language: TypeScript
- License: Apache-2.0
- Latest release: v0.9.24 / 2026-05-29T09:23:54Z
- Last pushed: 2026-05-29T09:23:53Z
- Topics: agentmemory, agents, ai, claude, claudecode, codex, copilot, cursor, genai, harness, hermes, memory, openclaw

## Evidence checked

- GitHub metadata via `gh repo view rohitg00/agentmemory` on 2026-05-30.
- [Upstream README](https://github.com/rohitg00/agentmemory/blob/main/README.md) inspected.
- License, package manifest, security policy, and top-level contents where present from the upstream repository.

## Strengths

- Explicitly supports Hermes, OpenClaw, Codex, Claude Code, Copilot, Cursor, Gemini, OpenCode, and MCP clients.
- Apache-2.0, recent v0.9.24 release, CI/test badges, security policy, Docker/config files, eval runners, benchmarks, and session replay docs.
- Best candidate here for a fair bakeoff because it advertises retrieval accuracy/token savings and includes `eval:longmemeval` / `eval:coding-life` scripts.

## Risks / caveats

- Memory systems can look great in demos while harming local truth boundaries. It must win against existing Hermes/GBrain tools before adoption.
- Global install + hooks + REST/MCP server is a large ambient surface. Needs copied-data sandbox and security review.
- Depends on iii-engine/sdk; evaluate lock-in and data format export before trusting.

## Integration ideas

- Use its benchmark framing to shape representative memory-sidecar bakeoff questions.
- Steal session replay + eval-runner shape for testing Hermes memory improvements.

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

- Fold into the existing memory-sidecar bakeoff action rather than adding a new memory platform now.
- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
