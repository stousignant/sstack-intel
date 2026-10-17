---
title: TinyAGI/tinyagi
type: repo-intel
source: https://github.com/TinyAGI/tinyagi
category: multi-agent-ops
status: deep-analyzed
usefulness_score: 72
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# TinyAGI/tinyagi

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `72/100` — Experimental multi-team 24/7 personal assistant orchestrator; mine heartbeat/team semantics, not runtime.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Compare its heartbeat/team/channel model against Hermes cron, delegation, and Discord delivery before any sandbox.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 19/25 | Fit with Hermes/GBrain/SStack/long-running-agent workflow. |
| Leverage | 18/25 | Impact on evals, self-improvement, autonomy, or durable operations. |
| Reuse readiness | 12/20 | Installability/docs/examples/license/sandboxability. |
| Maturity/trust | 11/15 | Activity, tests/docs/security, and supply-chain risk. |
| Differentiation | 12/15 | Unique pattern versus current stack. |
| **Total** | **72/100** | Experimental multi-team 24/7 personal assistant orchestrator; mine heartbeat/team semantics, not runtime. |

## Verdict

TinyAGI is adjacent to long-running Hermes workloads requiring multi-team assistants, isolated workspaces, messaging integrations, and heartbeat monitoring. But it is experimental and overlaps Hermes. Treat it as an operations-semantics reference.

## Reference-stack relevance

- The target requirement is greater autonomy across Hermes/SStack/GBrain without weakening safety or execution discipline.
- This category is about evaluation contracts, self-improvement loops, long-running agent coordination, and operational evidence.
- The key boundary is **evals before training/self-modification**: define tasks, traces, scoring, budgets, and keep/revert rules for the intended workload before adopting optimizer loops.

## What it is

TinyAGI is the agent teams orchestrator for One Person Company. (fka TinyClaw)

## Evidence checked

- GitHub metadata: stars `3571`, forks `505`, pushed `2026-03-30T12:34:57Z`, archived `False`.
- Topics: none.
- Inspected upstream repository: [source](https://github.com/TinyAGI/tinyagi); capture location omitted.
- Files fetched: README.md, LICENSE, package.json, Dockerfile, AGENTS.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, Docker/package setup, AGENTS.md, heartbeat.md, docs, teams/channels framing.
- Directly relevant to persistent agent teams and long-running work.
- Good comparison point for Hermes cron/delegate/process semantics.

## Risks / caveats

- Experimental stability label; do not adopt as main runtime.
- Messaging integrations imply credential/security review.
- May duplicate existing Hermes/GBrain/Discord setup.

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

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
