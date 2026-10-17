---
title: Claude Code Ecosystem Comparison
created: 2026-05-30
updated: 2026-05-30
type: comparison
tags: [github-repos, claude-code, coding-agents, repo-intelligence]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/SuperClaude-Org--SuperClaude_Framework.md
  - wiki/intel/github-repos/repos/Yeachan-Heo--oh-my-claudecode.md
  - wiki/intel/github-repos/repos/hesreallyhim--awesome-claude-code.md
  - wiki/intel/github-repos/repos/musistudio--claude-code-router.md
  - wiki/intel/github-repos/repos/siteboon--claudecodeui.md
---

# Claude Code Ecosystem Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation
- Install now: **none globally**. The reference stack’s active runtime is still Hermes; avoid a second command/control plane by default.
- Sandbox if needed: [oh-my-claudecode](../repos/Yeachan-Heo--oh-my-claudecode.md) for Claude Code team orchestration, and [CloudCLI / Claude Code UI](../repos/siteboon--claudecodeui.md) only for mobile/web-agent access experiments on throwaway repos.
- Distill patterns: [SuperClaude](../repos/SuperClaude-Org--SuperClaude_Framework.md) command lifecycle/installer UX; [Claude Code Router](../repos/musistudio--claude-code-router.md) provider-routing/auth/logging; [Awesome Claude Code](../repos/hesreallyhim--awesome-claude-code.md) as a discovery queue only.

## Decision matrix
| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [Yeachan-Heo/oh-my-claudecode](../repos/Yeachan-Heo--oh-my-claudecode.md) | 22/25 | 13/15 | Medium | MIT | Mostly local/plugin | Best sandbox candidate for Claude Code team semantics; distill strict-mode and team lifecycle. |
| [SuperClaude-Org/SuperClaude_Framework](../repos/SuperClaude-Org--SuperClaude_Framework.md) | 20/25 | 13/15 | Medium | MIT | Local config/framework | Strong workflow/command taxonomy; patch Hermes gaps, do not adopt a parallel persona framework. |
| [siteboon/claudecodeui](../repos/siteboon--claudecodeui.md) | 20/25 | 12/15 | Medium/high | AGPL-3.0 | Self-host or cloud | Best mobile/web UI reference; sandbox carefully because browser shell + agents is sensitive. |
| [musistudio/claude-code-router](../repos/musistudio--claude-code-router.md) | 19/25 | 12/15 | Low/medium | MIT | Local proxy | Useful provider-router pattern for Claude Code; Hermes already owns provider config. |
| [hesreallyhim/awesome-claude-code](../repos/hesreallyhim--awesome-claude-code.md) | 18/25 | 13/15 | Low | CC-BY-NC-ND-4.0 | N/A | Use only as discovery index; no remixing/adapting text. |

## Category map

This batch splits into five different artifact contracts:

1. **Mobile/web agent control surface** — CloudCLI / Claude Code UI. High UX leverage, high exposure risk.
2. **Team orchestration framework** — oh-my-claudecode. Most relevant for comparing against Hermes delegation/Kanban.
3. **Provider-router/proxy** — Claude Code Router. Useful config/auth/logging patterns; not a Hermes replacement.
4. **Command/methodology framework** — SuperClaude. Strong lifecycle taxonomy and installer/list UX; risky if imported wholesale.
5. **Discovery catalog** — Awesome Claude Code. Good source queue, weak as a durable knowledge product because of license and genericity.

## Reference-stack recommendation

Default move: **keep Hermes as the active runtime and treat this batch as pattern fuel**. The only near-term sandbox is OMC, and only to test whether Claude Code team mode beats Hermes `delegate_task`/Kanban on a bounded coding task. Do not expose shell-capable agent sessions through a web UI; that is a security footgun.

The high-leverage extraction is narrower:

- Add strict-mode bundles / path restrictions / external-worker toggles to skill/plugin security reviews.
- Improve skill discoverability and lifecycle docs with SuperClaude-style command references and install verification.
- Reuse Claude Code Router’s localhost/auth/logging defaults for future gateway/plugin surfaces.
- Use Awesome Claude Code as a discovery source, not as content to copy; its license does not support adapting the text.

## Open questions
- Does OMC team mode produce better proof bundles than Hermes `delegate_task` on one real but non-sensitive coding task?
- Would a mobile Hermes/Paperclip/CloudCLI-style web UI actually beat Discord for the reference stack’s mobile workflows, or just add attack surface?
- Should Hermes provider/profile UX adopt named presets similar to Claude Code Router?
