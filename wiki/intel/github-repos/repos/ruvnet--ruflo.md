---
title: ruvnet/ruflo
type: repo-intel
aliases: [ruflo, claude-flow, GitHub repo: ruvnet/ruflo]
source: https://github.com/ruvnet/ruflo
category: agent-work-orchestration
topics: [github-repo, multi-agent, swarm, claude-code, codex, mcp, orchestration]
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# ruvnet/ruflo

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `78/100` — interesting multi-agent orchestration reference, but hype/sprawl and overlapping runtime scope make it pattern-first.
- **Recommendation:** `distill-pattern`, not adopt.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Mine only concrete swarm/consensus/memory/security patterns if they beat Hermes Kanban/delegation concepts.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 18/25 | Relevant to orchestration, but Claude-flow/Ruflo is a parallel runtime. |
| Leverage | 20/25 | Could inspire worker coordination and status semantics. |
| Reuse readiness | 13/20 | Installable npm-style package, but huge dependency/runtime surface. |
| Maturity/trust | 12/15 | Active and popular; package overrides/security scripts suggest awareness, but surface is broad. |
| Differentiation | 15/15 | Swarm/memory/consensus framing is distinct enough to study. |

## Verdict

Ruflo is worth studying, not installing as a default. Its claims around 60+ agents, self-learning swarms, memory, consensus, RAG, Codex/Claude integration, and MCP are too broad to adopt without a very specific need. The safe use is pattern extraction for Hermes/Kanban worker coordination.

## Reference-stack relevance

- It is a mature public artifact in the “multi-agent swarm for coding work” space.
- Could reveal useful semantics for worker roles, consensus, memory, and failure handling.
- Helps calibrate when multi-agent orchestration becomes real leverage versus theater.

## What it is

An npm/TypeScript/Rust-ish agent meta-harness for Claude Code/Codex-style workflows, with swarm orchestration, memory, RAG, MCP, and security/audit scripts in its package surface.

## Evidence checked

- GitHub metadata on 2026-06-03: MIT license, ~57.6k stars, pushed 2026-06-03.
- Root package metadata: package name `claude-flow`, bin `claude-flow`, dependencies on `@claude-flow/*`, optional Codex/plugin packages, security scripts and dependency overrides.
- Repomix pack: a temporary source pack of the public repository — huge pack (~7.4M tokens); read selectively only.
- Legacy migrated note for earlier project framing.

## Strengths

- Strong vocabulary for multi-agent orchestration, swarm coordination, and memory.
- Explicit MCP/Codex/Claude integration points.
- Security/audit scripts and overrides indicate some supply-chain awareness.

## Risks / caveats

- Very large runtime surface; high risk of adopting a second agent platform before measuring need.
- “Swarm/self-learning” claims are easy to over-value without evals.
- Large repomix pack had suspicious exclusions; no full code audit performed.

## Integration ideas

- Extract only worker lifecycle concepts that map to Hermes Kanban: role, heartbeat, owner, consensus, handoff, blocker, completion proof.
- Compare Ruflo swarm semantics against CCPM issue/worktree semantics before changing SStack workflows.

## Alternatives / related repos

- [automazeio/ccpm](automazeio--ccpm.md)
- [openai/symphony](openai--symphony.md)
- [paperclipai/paperclip](paperclipai--paperclip.md)
- [nanocoai/nanoclaw](nanocoai--nanoclaw.md)

## Review guidance

- Review candidate: distill only concrete orchestration semantics if/when a Hermes worker-board redesign starts.
