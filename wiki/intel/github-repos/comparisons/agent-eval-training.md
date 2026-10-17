---
title: Agent Evaluation and Training Repo Comparison
created: 2026-05-30
updated: 2026-05-30
type: comparison
tags: [github-repos, agent-evaluation, agent-training, hermes, self-improvement]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/Gen-Verse--OpenClaw-RL.md
  - wiki/intel/github-repos/repos/InternLM--WildClawBench.md
  - wiki/intel/github-repos/repos/NVIDIA--NemoClaw.md
  - wiki/intel/github-repos/repos/aiming-lab--AutoResearchClaw.md
  - wiki/intel/github-repos/repos/microsoft--agent-lightning.md
---

# Agent Evaluation and Training Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Install/sandbox first:** [InternLM/WildClawBench](../repos/InternLM--WildClawBench.md) — not the full benchmark blindly, but a tiny task/harness inspection to steal the evaluation contract for Hermes.
- **Distill next:** [microsoft/agent-lightning](../repos/microsoft--agent-lightning.md) — trajectory → optimizer → eval loop is the right self-improvement shape after evals exist.
- **Security reference:** [NVIDIA/NemoClaw](../repos/NVIDIA--NemoClaw.md) — useful sandbox/hardening checklist, especially because it explicitly mentions Hermes.
- **Pattern only for now:** [aiming-lab/AutoResearchClaw](../repos/aiming-lab--AutoResearchClaw.md) and [Gen-Verse/OpenClaw-RL](../repos/Gen-Verse--OpenClaw-RL.md). They are ambitious, but the near-term Hermes win is artifact contracts and loop design, not autonomous paper generation or RL training.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [WildClawBench](../repos/InternLM--WildClawBench.md) | 90 | 80 | Medium-high | MIT | Mostly, via Docker/task harness | `adopt-now` for bounded eval-task inspection. |
| [Agent Lightning](../repos/microsoft--agent-lightning.md) | 88 | 88 | High | MIT | Yes, but training infra-heavy | `distill-pattern`; trainer comes after evals. |
| [NemoClaw](../repos/NVIDIA--NemoClaw.md) | 86 | 86 | High | Apache-2.0 | Sandbox/local stack | `distill-pattern`; security checklist before runtime adoption. |
| [AutoResearchClaw](../repos/aiming-lab--AutoResearchClaw.md) | 82 | 82 | High | MIT | Mostly, with external research APIs likely | `distill-pattern`; research artifact/HITL patterns. |
| [OpenClaw-RL](../repos/Gen-Verse--OpenClaw-RL.md) | 80 | 78 | Very high | Apache-2.0 | Self-hosted claim | `distill-pattern`; async RL architecture only. |

## Category map

This batch splits into four layers:

1. **Evaluation contract** — WildClawBench: isolated tasks, hidden graders, harness comparison, time/cost/score.
2. **Optimization/training loop** — Agent Lightning and OpenClaw-RL: traces/rollouts, judges/rewards, optimizer, keep/revert discipline.
3. **Research automation workflow** — AutoResearchClaw: staged artifacts, citation verification, peer review, HITL gates.
4. **Sandbox/security substrate** — NemoClaw: container/sandbox posture, security docs, agent runtime hardening.

For any workflow considering self-modification or training, task evaluation should precede optimization: without a meaningful baseline and grader, improvements cannot be distinguished from noise. Training without evals is expensive theater.

## Conditional reference-stack guidance

Run a **tiny WildClawBench-derived evaluation spike** before touching RL/training frameworks. The output should be 5-10 workload-specific tasks for Hermes/GBrain/tool-use quality, rather than a new platform. With that baseline in place, Agent Lightning's trajectory-capture and optimization patterns become easier to assess. NemoClaw's hardening material is relevant when the workload includes longer-lived autonomous workers.

## Open questions

- Can WildClawBench tasks be run or inspected without pulling large Docker images/API credentials?
- Which 5-10 tasks best predict real workload value: repo intelligence, GBrain retrieval, coding edits, browser QA, or daily briefing quality?
- What sensitive data could enter Hermes trajectories, and where should redaction happen before any optimizer/trainer sees them?
- Are NemoClaw/OpenShell controls meaningfully stronger than a simpler containerized Hermes worker lane?
