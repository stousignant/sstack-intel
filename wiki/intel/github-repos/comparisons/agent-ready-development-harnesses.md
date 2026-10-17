---
title: Agent-Ready Development Harnesses Repo Comparison
created: 2026-05-30
updated: 2026-05-30
type: comparison
tags: [github-repos, repo-intelligence, context-engineering, spec-driven-development, agent-readiness]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/Fission-AI--OpenSpec.md
  - wiki/intel/github-repos/repos/gsd-build--get-shit-done.md
  - wiki/intel/github-repos/repos/m0n0x41d--haft.md
  - wiki/intel/github-repos/repos/microsoft--agentrc.md
---

# Agent-Ready Development Harnesses Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Sandbox first:** [microsoft/agentrc](../repos/microsoft--agentrc.md) — strongest immediate candidate because it turns repo readiness and instruction quality into measurable artifacts.
- **Distill patterns:** [Fission-AI/OpenSpec](../repos/Fission-AI--OpenSpec.md), [m0n0x41d/haft](../repos/m0n0x41d--haft.md), [gsd-build/get-shit-done](../repos/gsd-build--get-shit-done.md) / successor `open-gsd/gsd-core`.
- **Do not globally install yet:** all four overlap with existing Hermes planning/TDD/skill/Kanban surfaces. The win is extracting artifact contracts, not importing another command framework.

## Decision matrix

| Repo | Fit | Reuse readiness | Trust | Verdict |
|---|---:|---:|---:|---|
| [microsoft/agentrc](../repos/microsoft--agentrc.md) | 23 | 17 | 13 | `adopt-now` for a copied-repo sandbox: readiness → generated AGENTS/instructions → eval/drift checks. |
| [Fission-AI/OpenSpec](../repos/Fission-AI--OpenSpec.md) | 22 | 18 | 13 | `distill-pattern`; strong proposal/spec/design/tasks/archive contract, but overlaps Spec Kit/Hermes plans. |
| [m0n0x41d/haft](../repos/m0n0x41d--haft.md) | 22 | 14 | 13 | `distill-pattern`; evidence decay/parity/WorkCommission are high-signal, direct install can wait. |
| [gsd-build/get-shit-done](../repos/gsd-build--get-shit-done.md) | 20 | 13 | 12 | `distill-pattern`; legacy repo moved to `open-gsd/gsd-core`; mine context-rot/verify semantics, do not install legacy package. |

## Category map

These repos are all trying to make AI-assisted development less vibes-based, but they operate at different layers:

1. **Repo readiness and context quality** — AgentRC measures whether a repo gives coding agents enough build/test/lint/architecture context, then generates/evaluates instruction artifacts.
2. **Spec-driven change artifacts** — OpenSpec turns feature work into persistent proposal/spec/design/tasks/archive folders.
3. **Decision governance** — Haft adds option comparison, evidence freshness, stale-assumption review, and bounded WorkCommissions.
4. **Context-rot / phase-state workflow** — GSD/GSD Core packages discuss/plan/execute/verify loops and phase continuity for long-running agent sessions.

## Reference-stack recommendation

Default next move is **not** “install all the frameworks.” The leverage path is:

1. Run AgentRC on one copied non-sensitive repo and inspect only generated artifacts plus readiness/evaluation output.
2. Distill OpenSpec’s `proposal/specs/design/tasks/archive` shape into planning/verification conventions only if it beats current plan files.
3. Reuse Haft’s evidence-decay/parity language for decision records and existing project issues.
4. Reuse GSD Core’s context-rot and verification-phase language for long-running coding sessions.

If a future bakeoff happens, compare the same tiny task across Hermes planning + TDD, GitHub Spec Kit, AgentRC-generated context, OpenSpec, Haft, and GSD Core. Anything that does not improve artifact quality or reduce review time gets rejected.

## Open questions

- Does AgentRC’s generated `AGENTS.md` beat operator-authored project instructions, or does it create generic noise?
- Does OpenSpec add useful archival and verification discipline beyond Spec Kit and existing Hermes plan skills?
- Can Haft’s evidence-decay model be represented as plain Markdown fields instead of adopting its MCP runtime?
- Which GSD Core phase-state concepts belong in session handoffs versus execution-ledger schemas?
