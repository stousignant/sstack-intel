---
title: HKUDS/AutoAgent
type: repo-intel
source: https://github.com/HKUDS/AutoAgent
category: agent-framework-evaluation
status: deep-analyzed
usefulness_score: 72
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# HKUDS/AutoAgent

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `72/100` — Zero-code agent framework with evaluation folder; useful comparison baseline, but likely not a Hermes replacement.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Inspect evaluation/tool-doc generation patterns only if building an agent-framework comparison or eval benchmark.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 17/25 | Fit with Hermes/GBrain/SStack/long-running-agent workflow. |
| Leverage | 18/25 | Impact on evals, self-improvement, autonomy, or durable operations. |
| Reuse readiness | 14/20 | Installability/docs/examples/license/sandboxability. |
| Maturity/trust | 13/15 | Activity, tests/docs/security, and supply-chain risk. |
| Differentiation | 10/15 | Unique pattern versus current stack. |
| **Total** | **72/100** | Zero-code agent framework with evaluation folder; useful comparison baseline, but likely not a Hermes replacement. |

## Verdict

AutoAgent is a broad zero-code LLM agent framework. Where Hermes is the active local interface, AutoAgent is a comparison baseline and potential source of evaluation/tool-documentation patterns, not a runtime replacement.

## Reference-stack relevance

- A useful autonomy workflow should increase capability without weakening reliability or safety across Hermes, its skills, and the GBrain knowledge layer.
- This category is about evaluation contracts, self-improvement loops, long-running agent coordination, and operational evidence.
- The key boundary is **evals before training/self-modification**: define workload-specific tasks, traces, scoring, budgets, and keep/revert rules before adopting optimizer loops.

## What it is

"AutoAgent: Fully-Automated and Zero-Code LLM Agent Framework"

## Evidence checked

- GitHub metadata: stars `9374`, forks `1313`, pushed `2025-10-16T06:35:28Z`, archived `False`.
- Topics: agent, llms.
- Inspected upstream repository: [source](https://github.com/HKUDS/AutoAgent); capture location omitted.
- Files fetched: README.md, LICENSE, pyproject.toml, root-contents.json, recent-commits.json.

## Strengths

- MIT license, high star count, evaluation folder, docs, tool docs, and Python packaging.
- Useful contrast with Hermes/OpenClaw/other agent frameworks.
- May contain evaluation artifacts worth sampling.

## Risks / caveats

- Zero-code framework direction can duplicate Hermes and reduce local control.
- Last push is older than current batch’s most active repos.
- Broad framework adoption is high-switching-cost.

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
