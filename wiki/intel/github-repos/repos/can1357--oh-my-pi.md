---
title: can1357/oh-my-pi
type: repo-intel
aliases: [oh-my-pi, omp, GitHub repo: can1357/oh-my-pi]
source: https://github.com/can1357/oh-my-pi
category: coding-agent-harness
topics: [github-repo, coding-agent, lsp, debugger, terminal-agent, harness]
status: deep-analyzed
usefulness_score: 86
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# can1357/oh-my-pi

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `86/100` — strong coding-harness benchmark for LSP/DAP/tool design, but not a near-term replacement for Hermes.
- **Recommendation:** `distill-pattern`; sandbox only if we need a direct coding-harness bakeoff.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Mine LSP/DAP/hash-anchored edit and stream-rule patterns into Hermes/Codex coding workflow evaluation.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Relevant to coding-agent quality, less to second-brain/GBrain. |
| Leverage | 21/25 | LSP/debugger integration could materially improve coding tasks. |
| Reuse readiness | 16/20 | Installable CLI, MIT, active; large codebase and separate runtime. |
| Maturity/trust | 14/15 | Very active, CI/docs, large usage signal. |
| Differentiation | 15/15 | Strong differentiator around IDE-grade LSP/DAP and tool harness design. |

## Verdict

OMP is a serious coding-agent harness reference. Its useful quality bar is hash-anchored edits, summarized reads, LSP-aware refactors, DAP debugging, provider breadth, and stream-time rule injection. It should not displace Hermes as the main assistant/runtime, but it is a good benchmark when assessing coding-agent lanes or future Hermes tool improvements.

## Reference-stack relevance

- Shows what “agent with IDE wired in” looks like beyond grep/read/edit loops.
- Useful comparison point for Codex/Claude/Hermes code-editing workflows.
- Its debugger and stream-rule patterns could improve long autonomous coding tasks.

## What it is

A terminal AI coding agent forked from Pi, with TypeScript/Bun plus a Rust core, many providers, built-in tools, LSP operations, DAP debugger operations, browser/subagent support, and benchmarked edit-format claims.

## Evidence checked

- GitHub metadata on 2026-06-03: MIT license, ~10.1k stars, pushed 2026-06-03.
- README: install, provider/tool counts, LSP/DAP sections, stream-rule behavior, browser/subagent/tooling claims.
- Repomix pack: a temporary Repomix evidence pack — very large pack (~4.7M tokens); read selectively only.
- Package/root metadata showed TypeScript/Rust/Bun structure and security files.

## Strengths

- IDE-grade LSP and debugger integration are exactly where many coding agents are weak.
- Model/provider breadth makes it useful as a neutral harness benchmark.
- Stream-time rule injection is a sharp context-budget pattern.
- MIT license and active development reduce adoption friction for experiments.

## Risks / caveats

- Large alternate runtime; adopting it globally would create tool sprawl.
- README benchmark claims need independent reproduction before becoming design truth.
- Repomix flagged suspicious files and excluded them; treat the pack as evidence only, not a full audit.

## Integration ideas

- Create a tiny coding-task bakeoff: Hermes vs Codex vs OMP on refactor+test+debug tasks.
- Distill LSP/DAP patterns into Hermes coding-tool wishlist.
- Use OMP as a “what good looks like” benchmark, not a canonical runtime.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [anomalyco/opencode](anomalyco--opencode.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenHands/OpenHands](OpenHands--OpenHands.md)

## Review candidates and context

- Non-binding candidate: run a small coding-harness benchmark only when a concrete refactor/test/debug comparison justifies it.
