---
title: microsoft/agent-lightning
type: repo-intel
aliases:
  - agent-lightning
  - GitHub repo: microsoft/agent-lightning
source: https://github.com/microsoft/agent-lightning
category: agent-training
topics: [github-repo, repo-intelligence, agent-evaluation, agent-training]
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# microsoft/agent-lightning

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `88/100` — Best general “train any agent” reference in this batch: framework-agnostic telemetry/trajectory extraction plus RL/APO/SFT hooks, but too training-infra-heavy to install before the operator has an eval set.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Do not install globally. Distill its trace → optimizer → eval loop into Hermes dream-cycle/retrieval-eval design; sandbox only after a small fixed benchmark exists.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22/25 | Fits Hermes/GBrain/local-agent questions, but direct runtime fit varies by repo. |
| Leverage | 24/25 | Useful for evals, self-improvement, research automation, or sandbox safety. |
| Reuse readiness | 16/20 | Docs/install/licensing are present, but most require sandboxing before use. |
| Maturity/trust | 13/15 | Live metadata: 17255 stars, 1509 forks, pushed 2026-04-29T06:32:24Z, license MIT. |
| Differentiation | 13/15 | Distinctive compared with current Hermes stack as an eval/training/safety pattern source. |

## Verdict

Best general “train any agent” reference in this batch: framework-agnostic telemetry/trajectory extraction plus RL/APO/SFT hooks, but too training-infra-heavy to install before the operator has an eval set. The useful move is not to install this globally. Keep Hermes/GBrain as the active operating layer, extract the eval/training/sandbox pattern, and only run bounded sandboxes with copied/non-sensitive data.

## Reference-stack relevance

- This batch sits directly on the question of making Hermes more measurable and self-improving: benchmark tasks, trajectory capture, training loops, HITL research workflows, and safer agent sandboxes.
- It can turn “agent improvement” from vibes into artifacts: task suites, hidden graders, traces, verification reports, and explicit keep/revert criteria.
- The practical value compounds only if the operator avoids adding yet another canonical runtime or memory store before evals prove a gap.

## What it is

Agent Lightning is a Microsoft Python framework for optimizing existing agents with reinforcement learning, automatic prompt optimization, and supervised fine-tuning with “almost zero code change.”

## Live metadata checked

- Source: <https://github.com/microsoft/agent-lightning>
- Description: The absolute trainer to light up AI agents.
- Stars / forks: 17255 / 1509
- Primary language: Python
- License: MIT
- Latest release: v0.3.0 / 2025-12-24T01:54:25Z
- Last pushed: 2026-04-29T06:32:24Z
- Topics: agent, agentic-ai, llm, mlops, reinforcement-learning

## Evidence checked

- GitHub metadata via `gh repo view microsoft/agent-lightning` on 2026-05-30.
- README from [upstream README](https://github.com/microsoft/agent-lightning/blob/HEAD/README.md).
- License and manifest files where present under temporary upstream inspection material.
- Top-level contents from GitHub API snapshot in `contents.json`.

## Strengths

- Strong framework-agnostic positioning: README names LangChain, OpenAI Agent SDK, AutoGen, CrewAI, Microsoft Agent Framework, and no-framework Python OpenAI agents.
- Mature signals for a young repo: PyPI package, docs site, examples, tests/CI badge, MIT license, security policy, and v0.3.0 release.
- The architecture is highly relevant to Hermes self-improvement: collect trajectories from a working agent, selectively optimize one/more agents, and compare against objective tasks.

## Risks / caveats

- Training stack is not lightweight: dependencies include telemetry/server components and optional VERL/vLLM paths; not a casual local install.
- Optimization without a fixed reference-workflow-specific eval set would be cargo cult RL. The eval harness must come before any trainer.
- Agent telemetry can capture sensitive task/context data; any future sandbox needs copied/non-sensitive trajectories.

## Integration ideas

- Use as the conceptual template for Hermes “evidence before self-modification”: trace, score, optimize, verify, keep/revert.
- Pair with WildClawBench or a tiny local retrieval/tool-use eval before considering agent training.

## Alternatives / related repos

- [microsoft/agent-lightning](microsoft--agent-lightning.md)
- [InternLM/WildClawBench](InternLM--WildClawBench.md)
- [aiming-lab/AutoResearchClaw](aiming-lab--AutoResearchClaw.md)
- [Gen-Verse/OpenClaw-RL](Gen-Verse--OpenClaw-RL.md)
- [NVIDIA/NemoClaw](NVIDIA--NemoClaw.md)
- [karpathy/autoresearch](karpathy--autoresearch.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)

## Review candidates and context

- Create/extend a Hermes self-improvement design note only after real eval questions and scoring criteria are defined.
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
