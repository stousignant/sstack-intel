---
title: ZJU-REAL/SkillZero
type: repo-intel
source: https://github.com/ZJU-REAL/SkillZero
category: agent-rl-skill-learning
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: Apache-2.0
---

# ZJU-REAL/SkillZero

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `78/100` — Research-grade skill-internalization RL project; useful conceptually after evals exist, not a near-term Hermes install.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Preserve as a research reference for skill internalization; revisit only after stable evaluation tasks and trajectory data exist.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 19/25 | Fit with Hermes/GBrain/SStack/long-running-agent workflow. |
| Leverage | 21/25 | Impact on evals, self-improvement, autonomy, or durable operations. |
| Reuse readiness | 12/20 | Installability/docs/examples/license/sandboxability. |
| Maturity/trust | 14/15 | Activity, tests/docs/security, and supply-chain risk. |
| Differentiation | 12/15 | Unique pattern versus current stack. |
| **Total** | **78/100** | Research-grade skill-internalization RL project; useful conceptually after evals exist, not a near-term Hermes install. |

## Verdict

SKILL0 studies agents internalizing skills through in-context reinforcement learning. Its practical relevance depends on first having representative evaluation tasks and trajectory capture; without those, it remains research context rather than a near-term implementation guide.

## Workload fit

- For agent workloads involving long-running coordination or self-improvement, the priority is to improve autonomy without weakening safety or verification.
- This category is about evaluation contracts, self-improvement loops, long-running agent coordination, and operational evidence.
- The key boundary is **evaluation before training/self-modification**: define representative tasks, traces, scoring, budgets, and keep/revert rules before adopting optimizer loops.

## What it is

Official code for "SKILL0: In-Context Agentic Reinforcement Learning for Skill Internalization"

## Evidence checked

- GitHub metadata: stars `316`, forks `14`, pushed `2026-05-20T12:43:56Z`, archived `False`.
- Topics: agent, curriculum-learning, in-context-reinforcement-learning, rl, skill, openclaw, openclaw-skills.
- Local evidence cache: a disposable source-inspection workspace.
- Files fetched: README.md, LICENSE, pyproject.toml, requirements.txt, root-contents.json, recent-commits.json.

## Strengths

- Apache-2.0 license, official paper/code, tests/docs/examples/skills, active 2026 updates.
- Directly about agentic skill internalization, curriculum learning, and RL.
- Could inform future SStack skill-learning/evaluation design.

## Risks / caveats

- Heavy research/runtime dependencies; likely not cheap to run locally.
- OpenClaw-oriented and RL-heavy; it may not fit workflows that first need deterministic evaluation scaffolding.
- Score confidence is medium without deeper paper/code inspection.

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

- Candidates above remain non-binding; implementation needs a separately scoped evaluation.
