---
title: mutable-state-inc/autoresearch-at-home
type: repo-intel
source: https://github.com/mutable-state-inc/autoresearch-at-home
category: collaborative-autoresearch
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: NOASSERTION
---

# mutable-state-inc/autoresearch-at-home

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `82/100` — Strong collaborative autoresearch pattern: experiment claiming, result sharing, duplicate avoidance, expiry, and swarm coordination.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Distill coordination semantics into Hermes long-running task runners: claim/lease, similarity dedupe, expiry, result ledger, and shared workspace boundaries.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | Fit with Hermes/GBrain/SStack/long-running-agent workflow. |
| Leverage | 23/25 | Impact on evals, self-improvement, autonomy, or durable operations. |
| Reuse readiness | 13/20 | Installability/docs/examples/license/sandboxability. |
| Maturity/trust | 10/15 | Activity, tests/docs/security, and supply-chain risk. |
| Differentiation | 15/15 | Unique pattern versus current stack. |
| **Total** | **82/100** | Strong collaborative autoresearch pattern: experiment claiming, result sharing, duplicate avoidance, expiry, and swarm coordination. |

## Verdict

Direct adoption is not a fit unless the operator is training nanochat on GPUs. But the coordination layer is gold for long-running Hermes work: agents claim work, avoid duplicates, share results, expire stale claims, and route progress through a shared workspace. That maps cleanly to durable batch runners and cron/dream-cycle loops.

## Reference-stack relevance

- The reference-stack goal is for Hermes/SStack/GBrain to become more autonomous without becoming sloppy or unsafe.
- This category is about evaluation contracts, self-improvement loops, long-running agent coordination, and operational evidence.
- The key boundary is **evals before training/self-modification**: define reference-workflow-specific tasks, traces, scoring, budgets, and keep/revert rules before adopting optimizer loops.

## What it is

AI agents running research on single-GPU nanochat training automatically

## Evidence checked

- GitHub metadata: stars `488`, forks `29`, pushed `2026-03-13T01:13:40Z`, archived `False`.
- Topics: none.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, pyproject.toml, root-contents.json, recent-commits.json.

## Strengths

- README clearly describes SETI@home-style multi-agent research swarm coordination.
- Concrete files include coordinator.py, collab.md, program.md, train.py, and pyproject.
- Excellent pattern source for long-running multi-agent batch work.

## Risks / caveats

- Unknown license from fetched metadata; do not copy code/text wholesale.
- Hardware/training-oriented; runtime is not relevant to the reference stack’s immediate stack.
- Shared external workspace/network coordination has trust and data-boundary concerns.

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

## Review candidates and context

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
