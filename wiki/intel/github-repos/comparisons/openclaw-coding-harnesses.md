---
title: OpenClaw / Coding Harnesses Repo Comparison
created: 2026-06-03
updated: 2026-06-03
type: comparison
tags: [github-repos, repo-intelligence, openclaw, coding-agents, browser-automation]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/AndyMik90--Aperant.md
  - wiki/intel/github-repos/repos/DenchHQ--DenchClaw.md
  - wiki/intel/github-repos/repos/Kuberwastaken--claurst.md
  - wiki/intel/github-repos/repos/anomalyco--opencode.md
  - wiki/intel/github-repos/repos/chrysb--alphaclaw.md
  - wiki/intel/github-repos/repos/jackwener--OpenCLI.md
  - wiki/intel/github-repos/repos/mergisi--awesome-openclaw-agents.md
  - wiki/intel/github-repos/repos/nextlevelbuilder--goclaw.md
  - wiki/intel/github-repos/repos/ultraworkers--claw-code.md
  - wiki/intel/github-repos/repos/volcengine--OpenViking.md
---

# OpenClaw / Coding Harnesses Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Sandbox next:** `anomalyco/opencode` for a coding-agent lane bakeoff, and `jackwener/OpenCLI` only on harmless public/logged-out browser targets.
- **Distill patterns:** `chrysb/alphaclaw`, `nextlevelbuilder/goclaw`, `volcengine/OpenViking`, and `AndyMik90/Aperant` for watchdogs, rollback, isolation, context packaging, and work-state semantics.
- **Watch/reference:** `Kuberwastaken/claurst`, `ultraworkers/claw-code`, `DenchHQ/DenchClaw`, and `mergisi/awesome-openclaw-agents` until specific gaps justify deeper sandboxing.

The take: **do not adopt an OpenClaw stack just because the ecosystem is noisy.** Hermes remains the active runtime. The highest-leverage next experiment is a bounded coding-agent bakeoff and a consent-gated browser automation comparison.

## Decision matrix

| Repo | Score | Recommendation | License | Subtype | Evaluation candidate |
|---|---:|---|---|---|---|
| [AndyMik90/Aperant](../repos/AndyMik90--Aperant.md) | 69 | `distill-pattern` | `AGPL-3.0` | coding-agent-control-plane | Keep as a control-plane/security reference; do not adopt into work or personal repos without a disposable sandbox and license/security review. |
| [anomalyco/opencode](../repos/anomalyco--opencode.md) | 86 | `adopt-now` | `MIT` | coding-agent-runtime | Run a bounded OpenCode CLI bakeoff against Hermes/Codex on one disposable repo, with proof-bundle requirements and no production credentials. |
| [chrysb/alphaclaw](../repos/chrysb--alphaclaw.md) | 78 | `distill-pattern` | `MIT` | openclaw-harness | Distill watchdog/setup/rollback/observability ideas into Hermes long-running-task operations rather than installing AlphaClaw. |
| [DenchHQ/DenchClaw](../repos/DenchHQ--DenchClaw.md) | 64 | `watch` | `MIT` | openclaw-productivity-app | Watch as a local CRM/outreach product reference only; do not connect real contacts/accounts without a security and data-flow review. |
| [jackwener/OpenCLI](../repos/jackwener--OpenCLI.md) | 84 | `adopt-now` | `Apache-2.0` | browser-automation-cli | Sandbox OpenCLI on a harmless public/logged-out site and compare against Hermes browser tools + Playwright MCP before any logged-in-browser use. |
| [Kuberwastaken/claurst](../repos/Kuberwastaken--claurst.md) | 76 | `watch` | `GPL-3.0` | coding-agent-runtime | Watch Rust multi-provider architecture; only sandbox if OpenCode/Codex/Hermes comparison exposes a terminal-agent gap. |
| [mergisi/awesome-openclaw-agents](../repos/mergisi--awesome-openclaw-agents.md) | 72 | `reference-only` | `MIT` | openclaw-agent-template-catalog | Use as a quarantined discovery list for agent-template ideas; selectively port only concrete task roles with eval criteria. |
| [nextlevelbuilder/goclaw](../repos/nextlevelbuilder--goclaw.md) | 70 | `distill-pattern` | `CC-BY-NC-4.0` | openclaw-gateway-runtime | Mine multi-tenant isolation/channel/security patterns only; avoid direct adoption because of non-commercial license and runtime overlap. |
| [ultraworkers/claw-code](../repos/ultraworkers--claw-code.md) | 74 | `watch` | `MIT` | coding-agent-runtime | Watch for real maturity/parity evidence; compare only after OpenCode/Claurst/Hermes bakeoff criteria exist. |
| [volcengine/OpenViking](../repos/volcengine--OpenViking.md) | 82 | `distill-pattern` | `AGPL-3.0` | agent-context-database | Compare OpenViking’s filesystem/context-database model against GBrain/Hermes context boundaries before any sandbox; likely distill hierarchical context ideas only. |

## Category map

- **Coding-agent runtimes:** OpenCode, Claurst, Claw Code. These compete with Codex/Claude Code/Hermes coding lanes.
- **OpenClaw harnesses/control planes:** AlphaClaw, Aperant, GoClaw, DenchClaw. These are mostly pattern sources unless the operator chooses OpenClaw as a secondary runtime.
- **Browser/app automation:** OpenCLI. This is tactically useful but needs explicit logged-in-browser consent boundaries.
- **Context substrate:** OpenViking. Strong context engineering ideas, but direct adoption overlaps GBrain and carries AGPL.
- **Agent template catalogs:** Awesome OpenClaw Agents. Useful only as quarantined discovery; avoid bulk prompt import.

## Reference-stack guidance

Priority order:

1. If coding-lane quality is the gap, compare **OpenCode, Hermes, and Codex** on one disposable task with the same acceptance/proof bundle.
2. If browser automation is required, compare **OpenCLI, Hermes browser tools, and Playwright MCP** on a logged-out target before any real browser session.
3. For long-running work, compare AlphaClaw, GoClaw, OpenViking, and Aperant for watchdog, rollback, context-packaging, and work-state capabilities; account for runtime and data-store overlap before integrating patterns.
4. Treat OpenClaw template catalogs as discovery sources, not trusted skills; import only reviewed, task-matched examples.

## Open questions

- Does OpenCode produce better evidence bundles than current Hermes/Codex workflows on the reference stack's actual repos?
- Does OpenCLI meaningfully outperform Hermes browser tools for deterministic web actions without increasing account-risk?
- Which OpenViking context-database ideas can strengthen GBrain/Hermes without introducing a second canonical context store?
