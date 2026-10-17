---
title: ghostwright/ghost-os
type: repo-intel
source: https://github.com/ghostwright/ghost-os
category: desktop-agent-control
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# ghostwright/ghost-os

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `78/100` — Accessibility-first macOS computer-use substrate with MCP/recipes; high pattern value but not directly runnable on the Linux reference environment.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Mine accessibility/recipe/MCP design for future desktop-control comparisons; do not adopt until there is a Mac-specific need and sandbox.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 20/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 13/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 12/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 13/15 | Unique pattern versus current stack. |
| **Total** | **78/100** | Accessibility-first macOS computer-use substrate with MCP/recipes; high pattern value but not directly runnable on the Linux reference environment. |

## Verdict

Ghost OS is interesting because it avoids screenshot-only computer use and leans on macOS accessibility, recipes, and MCP. It is not immediately useful on the Linux reference environment, but it is a strong reference for structured desktop automation.

## Reference-stack relevance

- The reference-stack goal is for long-running Hermes work to survive context limits, restarts, and multi-agent handoffs.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

Full computer-use for AI agents. Self-learning workflows. Native macOS. No screenshots required.

## Evidence checked

- GitHub metadata: stars `1483`, forks `140`, pushed `2026-03-23T22:41:44Z`, archived `False`.
- Topics: accessibility, ai-agents, automation, claude-code, computer-use, llm-tools, macos, mcp, recipes, swift.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, LICENSE, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, Swift Package, tests, docs, GHOST-MCP.md, recipes, vision sidecar, explicit macOS computer-use scope.
- Accessibility-first design is likely safer and more reliable than pure screenshot agents.
- Relevant to future Mac desktop automation or PAI/Claude workflows.

## Risks / caveats

- macOS 14+ only; the reference platform at review was Linux.
- Desktop control is sensitive; requires permissions and strong sandboxing.
- Needs deeper MCP/security audit before use.

## Integration ideas

- Prefer distilling control-plane semantics into Hermes/SStack rather than adopting another runtime by default.
- Any tool that runs shells, agents, worktrees, desktop automation, SSH, provider accounts, or browser/OS control needs disposable-repo sandboxing and auth/filesystem review.
- Useful design concepts include a long-running work ledger and eval suite with identity, handoff, heartbeat and audit evidence.

## Alternatives / related repos

- [Agent control planes / dashboards comparison](../comparisons/agent-control-planes-dashboards.md)
- [gastownhall/gastown](gastownhall--gastown.md)
- [generalaction/emdash](generalaction--emdash.md)
- [saltbo/agent-kanban](saltbo--agent-kanban.md)
- [TinyAGI/tinyagi](TinyAGI--tinyagi.md)

## Review candidates and context

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
