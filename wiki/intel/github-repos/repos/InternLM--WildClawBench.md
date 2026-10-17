---
title: InternLM/WildClawBench
type: repo-intel
aliases:
  - WildClawBench
  - GitHub repo: InternLM/WildClawBench
source: https://github.com/InternLM/WildClawBench
category: agent-evaluation
topics: [github-repo, repo-intelligence, agent-evaluation, agent-training]
status: deep-analyzed
usefulness_score: 90
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# InternLM/WildClawBench

> Reference-stack evaluation as reviewed 2026-05-30. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `90/100` — Highest immediate leverage in this batch because it benchmarks real end-to-end agent work and explicitly compares OpenClaw, Claude Code, Codex CLI, and Hermes Agent harnesses.
- **Recommendation:** `adopt-now`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Sandbox a tiny subset, not the full benchmark: inspect or run 1–3 safe tasks and the harness/grading contract, then decide whether they can seed representative, independently graded agent-evaluation tasks.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Fits Hermes/GBrain/local-agent questions, but direct runtime fit varies by repo. |
| Leverage | 25/25 | Useful for evals, self-improvement, research automation, or sandbox safety. |
| Reuse readiness | 17/20 | Docs/install/licensing are present, but most require sandboxing before use. |
| Maturity/trust | 13/15 | Live metadata: 415 stars, 39 forks, pushed 2026-05-19T11:35:36Z, license MIT. |
| Differentiation | 11/15 | Distinctive compared with current Hermes stack as an eval/training/safety pattern source. |

## Verdict

Highest immediate leverage in this batch because it benchmarks real end-to-end agent work and explicitly compares OpenClaw, Claude Code, Codex CLI, and Hermes Agent harnesses. The useful move is not to install this globally. Keep Hermes/GBrain as the active operating layer, extract the eval/training/sandbox pattern, and only run bounded sandboxes with copied/non-sensitive data.

## Workload fit

- This batch sits directly on the question of making Hermes more measurable and self-improving: benchmark tasks, trajectory capture, training loops, HITL research workflows, and safer agent sandboxes.
- It can turn “agent improvement” from vibes into artifacts: task suites, hidden graders, traces, verification reports, and explicit keep/revert criteria.
- Its practical value is strongest when evaluation artifacts establish a concrete gap before adding another runtime or memory store.

## What it is

WildClawBench is an in-the-wild benchmark for agents inside an OpenClaw-style environment: 60 hand-authored tasks across productivity, coding, multimodal, long-horizon, safety, and real-tool orchestration.

## Live metadata checked

- Source: <https://github.com/InternLM/WildClawBench>
- Description: An in-the-wild benchmark for AI agents in the OpenClaw Environment.
- Stars / forks: 415 / 39
- Primary language: Python
- License: MIT
- Latest release: none observed
- Last pushed: 2026-05-19T11:35:36Z
- Topics: agentic-ai, agentic-evaluation, agents, benchmarks, openclaw

## Evidence checked

- GitHub metadata via `gh repo view InternLM/WildClawBench` on 2026-05-30.
- README from [upstream README](https://github.com/InternLM/WildClawBench).
- License and manifest files where present under [upstream repository inspection](https://github.com/InternLM/WildClawBench).
- Top-level contents from GitHub API snapshot in `contents.json`.

## Strengths

- Directly names Hermes Agent, Claude Code, Codex CLI, and OpenClaw as comparable harnesses, enabling controlled comparisons when task, model, and configuration parity are established.
- README emphasizes real environment, Docker isolation, hidden ground truth injected after execution, and harness/model separation.
- MIT license, HuggingFace dataset link, paper/report, and active 2026 updates make it a strong eval reference.

## Risks / caveats

- Full benchmark may require Docker images, API keys, tool credentials, and long wall-clock runs; not a quick “run everything” action.
- Leaderboard numbers are only useful if harness/config parity is understood; do not overfit to one public score table.
- OpenClaw environment assumptions may not match Hermes’ native tool model without adapter work.

## Integration ideas

- Steal the evaluation contract: isolated task container, hidden grader, same task across multiple agent harnesses, cost/time/score reporting.
- Use task shapes as seed material for Hermes/GBrain retrieval and tool-use evals.

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

- Run a bounded WildClawBench harness/task inspection; extract 5–10 safe, representative evaluation tasks.
- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
