---
title: openclaw/lobster
type: repo-intel
source: https://github.com/openclaw/lobster
category: agent-workflows
status: deep-analyzed
usefulness_score: 86
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-27
license: MIT
---

# openclaw/lobster

> Reference-stack evaluation as reviewed 2026-05-27; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `86/100` — Most immediately testable tool in the batch: a small typed workflow shell with dry-run, graph, approval/resume, JSON envelopes, and npm CLI. Worth sandboxing as a deterministic workflow layer for agent-callable automations.
- Recommendation: `adopt-now`.
- **Usage observed 2026-05-27:** `not-used`.
- Review candidate: Run a disposable scratch-workspace sandbox with `lobster run --dry-run` and one toy workflow; compare against a plain Hermes skill/script.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23 | Hermes already benefits from deterministic CLI workflows and tool wrappers; Lobster is directly adjacent. |
| Leverage | 22 | Could turn repeated multi-step actions into resumable typed workflows instead of re-planning each time. |
| Reuse readiness | 19 | MIT, npm CLI, help works via npx, Node >=20, dry-run and graph modes. |
| Maturity/trust | 12 | Small/new project but has package scripts, tests, release, typed package exports. |
| Differentiation | 10 | Overlaps with Hermes skills/scripts/cron; value is typed workflow composition and approval/resume semantics. |

## Verdict

Most immediately testable tool in the batch: a small typed workflow shell with dry-run, graph, approval/resume, JSON envelopes, and npm CLI. Worth sandboxing as a deterministic workflow layer for agent-callable automations.

## Reference-stack relevance

- Could become a small reusable workflow substrate for repo-intelligence jobs, PR monitors, or guarded agent automations.
- More immediately useful than another full agent dashboard because it is CLI-shaped and deterministic.

## What it is

OpenClaw-native typed workflow shell for JSON-first pipelines, jobs, approvals, state, graph visualization, and calling LLM/OpenClaw tools.

## Live metadata checked

- Source: https://github.com/openclaw/lobster
- Homepage: https://docs.openclaw.ai/wiki/tools/lobster
- Primary language: TypeScript
- Stars / forks at review: 1214 / 276
- Last pushed: 2026-05-22T21:59:23Z
- Latest release: v2026.5.22
- License signal: MIT License
- Topics: none

## Evidence checked

- README frames Lobster as typed JSON-first pipelines/jobs/approval gates that save tokens and improve determinism/resumability.
- `package.json` exposes `lobster`, `clawd.invoke`, and `openclaw.invoke`; scripts include build/typecheck/lint/test and Node >=20.
- Local smoke test: `npx --yes @clawdbot/lobster --help` succeeded and showed dry-run, graph, resume, approve/cancel, tool JSON mode, and workflow commands.
- License is MIT; latest release v2026.5.22.

## Strengths

- Small enough to sandbox quickly.
- Dry-run and graph modes are exactly the right safety affordances for agent-called workflows.
- Approval/resume semantics map to human gates in Hermes.

## Risks / caveats

- OpenClaw-native naming and invoke paths may not map directly to Hermes tools.
- Could duplicate Hermes skills/scripts if adopted too broadly.
- New project; needs real workflow test before “active” status.

## Integration ideas

- Sandbox with a harmless workflow: repo status → gbrain search → formatted report, or PR monitor against public repo.
- Distill typed pipeline/approval/resume model into Hermes workflow-skill authoring even if Lobster is not adopted.

## Alternatives / related repos

- [paperclipai/paperclip](paperclipai--paperclip.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [agent work orchestration](../comparisons/agent-work-orchestration.md)

## Review guidance

- Run a disposable scratch-workspace sandbox with `lobster run --dry-run` and one toy workflow; compare against a plain Hermes skill/script.
