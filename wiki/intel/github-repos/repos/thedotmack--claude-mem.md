---
title: thedotmack/claude-mem
type: repo-intel
aliases:
  - claude-mem
  - GitHub repo: thedotmack/claude-mem
source: https://github.com/thedotmack/claude-mem
category: agent-memory
topics: [github-repo, repo-intelligence, agent-memory, context-management]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: Apache-2.0
---

# thedotmack/claude-mem

> Reference-stack evaluation as reviewed 2026-05-30; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — Strongest mature agent-memory pattern source in this batch: cross-agent hooks, compression, SQLite/Chroma-style memory, worker service, MCP search tools, and security notes; direct adoption would duplicate Hermes/GBrain memory ownership.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Do not install globally. Distill hook-based session capture, compression, worker/logging, and explicit security controls into Hermes/GBrain dream-cycle and memory hygiene design.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22/25 | Relevant to Hermes/GBrain/context/memory workflows, with varying risk of duplicate canonical stores. |
| Leverage | 23/25 | Could improve recall, context budget, code navigation, or session continuity if bounded correctly. |
| Reuse readiness | 15/20 | README/manifests provide install paths; safe adoption still requires sandboxing and boundary checks. |
| Maturity/trust | 14/15 | Live metadata: 79754 stars, 6868 forks, pushed 2026-05-29T19:19:59Z, license Apache-2.0. |
| Differentiation | 10/15 | Differentiates mainly by evals, hooks, UX, or low-token code/context tools versus current Hermes/GBrain stack. |

## Verdict

Strongest mature agent-memory pattern source in this batch: cross-agent hooks, compression, SQLite/Chroma-style memory, worker service, MCP search tools, and security notes; direct adoption would duplicate Hermes/GBrain memory ownership. The default stance is **one canonical memory/index layer**: Hermes memory + session search + GBrain + the second-brain vault. These repos are valuable only when they improve a specific boundary — recall quality, context-budget observability, code-navigation speed, or team/shared-memory UX — without creating a second truth store.

## Workload fit

- Where a deployment already has memory and search, the leverage is not “more memory” but **better evaluated recall with clean ownership boundaries**.
- Agent hooks and MCP context tools can save tokens/time, but they also increase ambient capture and secret-leak risk.
- Good patterns here can make Hermes more self-improving: session capture, compaction, retrieval evals, purge/logout controls, and low-token code context.

## What it is

Claude-Mem is a TypeScript memory compression and persistence system for Claude Code and other coding agents; it captures session/tool observations, summarizes them, and injects relevant context into future sessions.

## Live metadata checked

- Source: <https://github.com/thedotmack/claude-mem>
- Description: Persistent Context Across Sessions for Every Agent –  Captures everything your agent does during sessions, compresses it with AI, and injects relevant context back into future sessions. Works with Claude Code, OpenClaw, Codex, Gemini, Hermes, Copilot, OpenCode + More
- Stars / forks: 79754 / 6868
- Primary language: TypeScript
- License: Apache-2.0
- Latest release: v13.4.0 / 2026-05-29T18:35:01Z
- Last pushed: 2026-05-29T19:19:59Z
- Topics: ai, ai-agents, ai-memory, anthropic, artificial-intelligence, claude, claude-agent-sdk, claude-agents, claude-code, claude-code-plugin, claude-skills, long-term-memory, mem0, openmemory, supermemory, chromadb, sqlite, embeddings, memory-engine, rag

## Evidence checked

- GitHub metadata via `gh repo view thedotmack/claude-mem` on 2026-05-30.
- [Upstream README](https://github.com/thedotmack/claude-mem/blob/main/README.md) inspected.
- License, package manifest, security policy, and top-level contents where present from the upstream repository.

## Strengths

- Very active and mature signals: Apache-2.0, recent v13.4.0 release, security policy, plugin/worker/service scripts, tests/evals, Docker artifacts, and docs.
- Cross-agent ambition includes Claude Code, Gemini CLI, OpenCode, Codex/OpenClaw style plugin files, and MCP search tools.
- Security policy calls out command-injection prevention and safe spawn patterns, useful as a memory-hook safety reference.

## Risks / caveats

- It wants to be a persistent memory layer; architectures with compact memory, session search, an independent index, and a Markdown vault should avoid duplicating canonical memory.
- Hooks and worker services observing sessions can capture sensitive prompts, tool outputs, and project data; sandbox before any install.
- Heavy plugin/service surface increases operational complexity compared with scoped Hermes skills.

## Integration ideas

- Borrow the lifecycle, not the database: session observation → compress → index → retrieve → inject with caps.
- Use security-policy examples as a prompt for Hermes hook/tool command-safety docs.

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

- Distill into a future memory-capture design only after deciding what Hermes/GBrain lacks relative to session_search.
- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
