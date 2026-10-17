---
title: yologdev/yoyo-evolve
type: repo-intel
source: https://github.com/yologdev/yoyo-evolve
category: self-improving-agents
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# yologdev/yoyo-evolve

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `88/100` — Best self-evolving-agent reference in the batch; mine its journaling, memory and skill-evolution loop, not its full runtime.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `high`.
- **Review candidate:** Distill yoyo’s bounded evolution mechanics into Hermes dream-cycle/eval design: journal ledger, skill counter, memory, tests, and keep/revert gates.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Fit with Hermes/GBrain/SStack/long-running-agent workflow. |
| Leverage | 24/25 | Impact on evals, self-improvement, autonomy, or durable operations. |
| Reuse readiness | 15/20 | Installability/docs/examples/license/sandboxability. |
| Maturity/trust | 12/15 | Activity, tests/docs/security, and supply-chain risk. |
| Differentiation | 14/15 | Unique pattern versus current stack. |
| **Total** | **88/100** | Best self-evolving-agent reference in the batch; mine its journaling, memory and skill-evolution loop, not its full runtime. |

## Verdict

yoyo-evolve is high-leverage pattern material for Hermes self-improvement: public daily evolution, explicit identity/personality/memory, skills, tests, and a Rust codebase around a self-modifying coding agent. Its artifact trail is a strong evidence-discipline model for Hermes dream-cycle and similar maintenance workflows, not a reason to adopt its runtime.

## Workload fit

- For agent workloads involving long-running coordination or self-improvement, the priority is to improve autonomy without weakening safety or verification.
- This category is about evaluation contracts, self-improvement loops, long-running agent coordination, and operational evidence.
- The key boundary is **evaluation before training/self-modification**: define representative tasks, traces, scoring, budgets, and keep/revert rules before adopting optimizer loops.

## What it is

A Truman Show of a self-evolving AI coding agent. It writes its own code. Growing up in public.

## Evidence checked

- GitHub metadata: stars `1801`, forks `119`, pushed `2026-06-03T11:37:59Z`, archived `False`.
- Topics: none.
- Upstream evidence: https://github.com/yologdev/yoyo-evolve; the following fetched files were inspected at review time.
- Files fetched: README.md, LICENSE, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, active daily commits, docs/journals/memory/skills/tests all visible at repo root.
- Strong fit to self-improving Hermes patterns: evolution ledger, memory, skill mutation, and explicit identity boundaries.
- Provides concrete evidence artifacts rather than only README claims.

## Risks / caveats

- Self-modifying agent framing can encourage unsafe autonomy if copied without budget/scope/stop conditions.
- Runtime adoption would overlap Hermes and OpenClaw rather than improve the active stack.
- Needs targeted reading of core Rust control files before any implementation borrowing.

## Integration ideas

- Treat this as source material for Hermes eval harnesses, dream-cycle experiments, long-running task orchestration, or SStack skill validation — not as a live runtime by default.
- Convert reusable ideas into concrete eval tasks, trace schemas, action ledgers, or safety gates before considering automation.
- Keep all experiments bounded, non-sensitive, and reversible; preserve result evidence in the second brain or a project tracker.

## Alternatives / related repos

- [Evals / self-improvement / autoresearch comparison](../comparisons/evals-self-improvement-autoresearch.md)
- [karpathy/autoresearch](karpathy--autoresearch.md)
- [InternLM/WildClawBench](InternLM--WildClawBench.md)
- [microsoft/agent-lightning](microsoft--agent-lightning.md)
- [NVIDIA/NemoClaw](NVIDIA--NemoClaw.md)

## Review guidance

- Candidates remain non-binding evaluation guidance.
