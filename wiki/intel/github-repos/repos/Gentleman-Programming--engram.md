---
title: Gentleman-Programming/engram
type: repo-intel
aliases:
  - engram
  - GitHub repo: Gentleman-Programming/engram
source: https://github.com/Gentleman-Programming/engram
category: memory-management
topics: [github-repo, memory, mcp, sqlite, fts5, coding-agents]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT
---

# Gentleman-Programming/engram

> Reference-stack evaluation as reviewed 2026-05-28. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — strong local-first memory reference for coding agents, but likely a sidecar/pattern source rather than a replacement for Hermes memory + GBrain + session search.
- **Recommendation:** `distill-pattern` — study MCP/CLI/TUI/session-lifecycle design; sandbox only if it answers a concrete memory gap.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Compare Engram's save/search/wake-up semantics against Hermes memory, session_search, and GBrain facts before adding another store.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | MCP, local SQLite, coding-agent session memory all map well to Hermes, but overlap current memory layers. |
| Leverage | 20/25 | Could improve compaction/session continuity if specific gaps are found. |
| Reuse readiness | 18/20 | Single Go binary, Homebrew, setup commands for Codex/Claude/OpenCode/Gemini, docs, security file. |
| Maturity/trust | 13/15 | Active, popular, MIT, docs/tests implied by repo structure; optional cloud needs boundary review. |
| Differentiation | 12/15 | Differentiates through agent-agnostic MCP + SQLite/FTS + TUI, but not clearly beyond GBrain/session DB yet. |

## Verdict

Engram is a credible **memory sidecar candidate**, but the default should be pattern distillation. In an environment already using Hermes persistent memory, `session_search` transcripts, GBrain facts/takes/pages, and an Obsidian vault, it adds another substrate. Consider it only if a bakeoff shows a material gap in cross-agent coding-session continuity, compaction recovery, or per-project memory that current tools do not cover.

## Reference-stack relevance

- It targets the exact “AI coding agents forget after sessions” pain.
- MCP stdio makes it easy to integrate with multiple agents.
- SQLite + FTS5 is simple, local, inspectable, and operationally sane.
- Its memory hygiene/session lifecycle docs may be useful even if the binary is never adopted.

## What it is

A Go binary for persistent AI coding-agent memory. It stores memories in SQLite/FTS5 and exposes them through MCP, HTTP API, CLI, and TUI. README lists setup paths for Claude Code, Pi, OpenCode, Gemini CLI, Codex, VS Code, Cursor, Windsurf, and generic MCP tools.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 3,828 stars, 465 forks, Go, MIT, pushed 2026-05-27, not archived.
- README: single-binary local/cloud memory, MCP stdio architecture, 19 MCP tools, setup one-liners.
- Root contents: `cmd/`, `internal/`, `docs/`, `plugin/`, `skills/`, `go.mod`, `Makefile`, `SECURITY.md`, `LICENSE`, `.claude-plugin/`.

## Strengths

- Local-first, single binary, no runtime dependency mess.
- Agent-agnostic MCP surface.
- Multiple user interfaces: CLI, HTTP API, TUI.
- Good candidate for a contained benchmark against current memory stack.

## Risks / caveats

- Optional cloud/sync path needs privacy/security review.
- Another persistent memory store can fragment truth if not scoped tightly.
- FTS5-only/structured memory may be weaker than GBrain's hybrid search and typed facts for broader second-brain work.

## Integration ideas

- Sandbox on a copied coding-session corpus, not the canonical vault.
- Compare recall against `session_search` and GBrain for “what did we decide about X?” questions.
- Distill memory-save schema into Hermes post-task summaries if better than current memory guidance.

## Alternatives / related repos

- [MemPalace/mempalace](MemPalace--mempalace.md) — semantic/verbatim memory system with benchmark claims.
- [garrytan/gbrain](garrytan--gbrain.md) — active canonical index/query layer.
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — active runtime and memory tools.

## Review candidates and context

- Candidate: a copied-data memory-sidecar bakeoff against Hermes session search and GBrain.
