---
title: Agent Workflows / Coding Harnesses Repo Comparison
created: 2026-06-03
updated: 2026-09-23
type: comparison
tags: [github-repos, agent-workflows, coding-harnesses, long-running-tasks]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-09-23
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/automazeio--ccpm.md
  - wiki/intel/github-repos/repos/can1357--oh-my-pi.md
  - wiki/intel/github-repos/repos/different-ai--openwork.md
  - wiki/intel/github-repos/repos/primeintellect-ai--prime-agent.md
  - wiki/intel/github-repos/repos/revfactory--harness.md
  - wiki/intel/github-repos/repos/ruvnet--ruflo.md
  - wiki/intel/github-repos/repos/steipete--agent-scripts.md
  - wiki/intel/github-repos/repos/the-open-engine--zeroshot.md
---

# Agent Workflows / Coding Harnesses Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Best self-improving runtime pattern source:** [PrimeIntellect-ai/prime-agent](../repos/primeintellect-ai--prime-agent.md) — distill its persistent Python/RLM control plane, scoped continual-harness refinement, daemon continuity, and bounded goal/gate semantics; do not replace Hermes by default.
- **Best typed execution and delivery-gate pattern source:** [the-open-engine/zeroshot](../repos/the-open-engine--zeroshot.md) — distill authored graph bounds, structured verifier signals, last-writer settlement, and exact delivery receipts; do not add it as a second cockpit while crash restart remains unshipped.
- **Historical baseline:** [automazeio/ccpm](../repos/automazeio--ccpm.md) — historical runtime reference whose useful payload is GitHub/worktree patterns rather than another active route.
- **Distill now:** [steipete/agent-scripts](../repos/steipete--agent-scripts.md) — supports the shared-skill/source-of-truth design direction.
- **Distill skill-evaluation patterns:** [revfactory/harness](../repos/revfactory--harness.md) — preserve comparative skill tests, near-miss trigger checks, and rerun-aware handoffs; reject the Claude-specific control plane.
- **Benchmark later:** [can1357/oh-my-pi](../repos/can1357--oh-my-pi.md) — strong coding-agent quality bar, especially LSP/DAP and edit harness patterns.
- **Watch / pattern-only:** [different-ai/openwork](../repos/different-ai--openwork.md) and [ruvnet/ruflo](../repos/ruvnet--ruflo.md) — useful control-plane/orchestration references, but too broad as default runtimes.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [PrimeIntellect-ai/prime-agent](../repos/primeintellect-ai--prime-agent.md) | 24 | 11 | High | MIT | Yes | Distill and sandbox only: exceptional continual-harness/RLM reference, but a broad unsandboxed parallel runtime with current CI and dependency caveats. |
| [the-open-engine/zeroshot](../repos/the-open-engine--zeroshot.md) | 20 | 11 | Medium-high | MIT | Local, self-hosted, or hosted | Distill its typed graph, independent-verifier, event-ledger, and exact delivery-receipt semantics; do not adopt as another cockpit while restart recovery and stability remain weak. |
| [automazeio/ccpm](../repos/automazeio--ccpm.md) | 24 | 12 | Medium | MIT | Yes-ish: GitHub-backed | Historical baseline only; do not reinstall as an active reference-stack route. |
| [steipete/agent-scripts](../repos/steipete--agent-scripts.md) | 24 | 13 | Low | MIT | Yes | Distill pointer/validation/projection patterns into the shared-skill source. |
| [revfactory/harness](../repos/revfactory--harness.md) | 15 | 4 | Low for patterns; wrong runtime for adoption | Apache-2.0 | Files are local; execution is Claude Code-specific | Distill skill-QA and orchestration patterns only; documentation claims exceed the repo's actual CI/release machinery. |
| [can1357/oh-my-pi](../repos/can1357--oh-my-pi.md) | 20 | 14 | Medium | MIT | Yes | Use as coding-harness benchmark; do not replace Hermes. |
| [different-ai/openwork](../repos/different-ai--openwork.md) | 20 | 13 | High | Other | Local/desktop + web | Watch; control-plane UX reference with security/license caveats. |
| [ruvnet/ruflo](../repos/ruvnet--ruflo.md) | 18 | 12 | High | MIT | Mixed | Distill only concrete multi-agent lifecycle semantics. |

## Category map

For the platform-level industry map around Archon—GitHub Agentic Workflows, GitLab Duo custom flows, Microsoft Conductor, durable-execution engines, and CI/CD glue—see [archon industry alternatives](archon-industry-alternatives.md). This page remains the repo-batch comparison for harness/runtime candidates; the Archon page owns the broader market and positioning conclusion.

This category now splits into six subtypes:

1. **Self-improving persistent runtime** — Prime Agent combines a persistent Python control plane, scoped harness refinement, daemon sessions, direct messaging, goals, heartbeats, schedules, and bounded gates.
2. **Historical durable-work contract** — CCPM demonstrated PRD, epic, issue, worktree, status, standup, and blocked/next patterns later distilled into the shared-skill source.
3. **Shared agent substrate** — agent-scripts is a compact example of canonical instructions, skills, validation, and repo-owned skill projection.
4. **Team/skill meta-factory** — revfactory/harness generates Claude Code agents and skills from a domain description; its portable value is the team-pattern and skill-evaluation methodology, not its runtime contract.
5. **Runtime/control-plane alternatives** — OMP, Ruflo, and OpenWork are valuable references, but each risks adding a parallel runtime if adopted too quickly.
6. **Typed execution graph and settlement engine** — Zeroshot makes bounded transitions, verifier signals, repair loops, and delivery receipts first-class protocol objects rather than prompt conventions.

## Reference-stack guidance

Prime Agent changes the pattern bar, not the active-runtime recommendation. First extract its local/global continual-harness ledger, refinement conflict detection, persistent-goal versus continuation-policy split, and crash-safe schedule semantics into Hermes and portable-skill self-improvement design. A runtime bakeoff is justified only if Hermes cannot reproduce those benefits cleanly.

Zeroshot addresses a different need: authored graph control flow and delivery settlement. Its executor/acceptance-review/code-review/repair separation, structured verifier signals, exact delivery receipts, and refusal to settle while another writer can invalidate proof are useful comparison points. Its SQLite event history should not be treated as crash-resilient durable execution; interrupted-run restart remains proposed rather than shipped.

CCPM remains a historical baseline: its GitHub/worktree concepts are relevant where spec-driven or supervised-delivery workflows need them, while its retired runtime and duplicated PRD/epic state are not evidence for a new active route.

Second priority: compare `steipete/agent-scripts` with existing shared skills and tighten validation/projection rules.

Do **not** start by installing Ruflo/OpenWork globally. They are attractive because they look like full platforms, which is exactly why they are risky.

## Open questions

- Does GitHub Issues beat Markdown/Kanban for the reference stack's private long-running agent tasks?
- Does Prime Agent's persistent Python kernel materially outperform Hermes' explicit typed tools plus `execute_code` on the same long-running task without weakening auditability?
- Can the shared-skill source adopt Prime Agent's scoped refinement ledger without creating another memory/skill truth store?
- What is the minimum proof bundle every autonomous coding worker must return?
- Should the shared-skill source generate host-specific skill projections like gstack/agent-scripts, or keep direct shared directories?
- Which OMP LSP/DAP features are actually missing from Hermes/Codex workflows?
- Can Hermes and portable skills reproduce Zeroshot's exact-delivery-receipt and last-writer settlement guarantees without adopting another runtime or task store?
