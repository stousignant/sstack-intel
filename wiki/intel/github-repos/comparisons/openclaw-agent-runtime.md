---
title: OpenClaw-adjacent Agent Runtime Repo Comparison
created: 2026-05-30
updated: 2026-05-30
type: comparison
tags: [github-repos, openclaw, agent-runtime, agent-safety, hermes]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/HKUDS--ClawWork.md
  - wiki/intel/github-repos/repos/abhi1693--openclaw-mission-control.md
  - wiki/intel/github-repos/repos/aiming-lab--MetaClaw.md
  - wiki/intel/github-repos/repos/code-yeongyu--oh-my-openagent.md
  - wiki/intel/github-repos/repos/nanocoai--nanoclaw.md
---

# OpenClaw-adjacent Agent Runtime Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Best pattern source:** [nanocoai/nanoclaw](../repos/nanocoai--nanoclaw.md) — container isolation, per-agent workspaces, messaging/channel boundaries, scheduled jobs, and credential-vault patterns are highly relevant to a safer Hermes worker lane.
- **Self-improvement reference:** [aiming-lab/MetaClaw](../repos/aiming-lab--MetaClaw.md) — preserve proxy/skill-injection/scheduled-RL architecture, but gate all training behind evals and safe trajectory capture.
- **Eval/economics reference:** [HKUDS/ClawWork](../repos/HKUDS--ClawWork.md) — useful work-vs-learn and cost/survival metrics; ignore hypey earnings framing unless independently verified.
- **Operations UI reference:** [abhi1693/openclaw-mission-control](../repos/abhi1693--openclaw-mission-control.md) — useful board/gateway/approval/control-plane vocabulary; do not migrate to an OpenClaw platform.
- **Harness reference only:** [code-yeongyu/oh-my-openagent](../repos/code-yeongyu--oh-my-openagent.md) — rich lifecycle/team-mode semantics, but SUL-1.0 and sprawl make it sandbox-only.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [NanoClaw](../repos/nanocoai--nanoclaw.md) | 88 | 86 | High | MIT | Yes, containerized | `distill-pattern`; strongest isolation/runtime reference. |
| [MetaClaw](../repos/aiming-lab--MetaClaw.md) | 84 | 80 | High | MIT | Partly; cloud/Tinker optional | `distill-pattern`; self-improvement scheduler reference. |
| [ClawWork](../repos/HKUDS--ClawWork.md) | 80 | 74 | Medium-high | MIT | Mostly local benchmark stack | `distill-pattern`; economic eval pattern. |
| [OpenClaw Mission Control](../repos/abhi1693--openclaw-mission-control.md) | 78 | 78 | High | MIT | Self-hosted | `distill-pattern`; operations/governance vocabulary. |
| [Oh My OpenAgent](../repos/code-yeongyu--oh-my-openagent.md) | 76 | 84 | High | SUL-1.0 | Local plugin, broad auth | `distill-pattern`; team/lifecycle reference only. |

## Category map

1. **Personal runtime isolation:** NanoClaw designs a smaller containerized agent runtime with channel and credential boundaries.
2. **Control plane / governance:** Mission Control provides board/gateway/approval semantics around OpenClaw teams.
3. **Self-improvement/training loop:** MetaClaw adds proxy, skills, memory, reward, and scheduled RL/LoRA updates.
4. **Economic-accountability benchmark:** ClawWork prices work, token costs, and quality to measure survival/usefulness.
5. **Multi-harness agent OS:** Oh My OpenAgent packages hooks, teams, LSP/AST tools, and Codex/OpenCode integration.

## Reference-stack recommendation

Keep Hermes as the active runtime. The highest-leverage extraction is NanoClaw's isolation model plus MetaClaw's safe-window self-improvement scheduler plus ClawWork's cost/value metrics. Any sandbox must start **read-only/design-spike**, not as a global install with real messaging channels or credentials.

## Open questions

- Which Hermes worker tasks would justify containerized isolation rather than current terminal/process controls?
- What should an autonomous-agent “budget” mean for the reference stack: token cost, time, risk, interruptions, or money-equivalent value?
- Can Mission Control / OMO team-mode semantics improve Hermes Kanban/delegate_task enough to justify a schema patch?
- What exact trajectory/eval gates are required before MetaClaw-style self-improvement becomes safe?
