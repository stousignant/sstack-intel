---
title: standardagents/arrow-js
type: repo-intel
source: https://github.com/standardagents/arrow-js
category: agent-friendly-ui-framework
status: deep-analyzed
usefulness_score: 70
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: NOASSERTION
---

# standardagents/arrow-js

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `70/100` — Agent-friendly UI framework/WASM sandbox reference; useful if building agent-facing web UIs, not urgent for Hermes ops.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Confidence:** `medium`.
- **Review candidate:** Keep as UI framework reference; revisit only if Wikic/Hermes needs an agent-editable web UI or sandboxed code playground.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 16/25 | Fit with Hermes/SStack/GBrain long-running agent workflows. |
| Leverage | 17/25 | Impact on durable coordination, visibility, or execution control. |
| Reuse readiness | 14/20 | Installability/docs/license/sandboxability. |
| Maturity/trust | 13/15 | Activity, tests/docs/security, and control-plane risk. |
| Differentiation | 10/15 | Unique pattern versus current stack. |
| **Total** | **70/100** | Agent-friendly UI framework/WASM sandbox reference; useful if building agent-facing web UIs, not urgent for Hermes ops. |

## Verdict

ArrowJS is not an agent orchestrator; it is a UI runtime designed around primitives coding agents understand, plus sandboxed playground/testing hints. It is relevant as a future UI substrate reference, but not a near-term SStack adoption target.

## Reference-stack relevance

- The target requirement is long-running Hermes work that survives context limits, restarts, and multi-agent handoffs.
- This batch covers visual cockpits, task boards, workspace managers, desktop-control surfaces, terminal canvases, and agent persona libraries.
- The useful payload is mostly operational semantics: identity, work ledgers, mailboxes, handoffs, worktrees, heartbeats, dashboards, and audit trails.

## What it is

The first UI framework for the agentic era — tiny, performant, with WASM sandboxes for safe code execution.

## Evidence checked

- GitHub metadata: stars `3531`, forks `75`, pushed `2026-04-01T14:28:41Z`, archived `False`.
- Topics: declarative, reactive, rendering, ui, ux, web, webcomponents.
- Upstream evidence: https://github.com/standardagents/arrow-js; the following fetched files were inspected at review time.
- Files fetched: README.md, package.json, AGENTS.md, root-contents.json, recent-commits.json.

## Strengths

- Tests/bench/docs/packages/playwright sandbox config and agent guide.
- Agent-friendly low-abstraction UI suits workflows where simple, task-focused UI primitives are preferable to additional framework layers.
- Could inform future web UI work for Wikic/Hermes dashboards.

## Risks / caveats

- License not resolved from fetched evidence (`LICENSE.txt` was not in optional fetch list).
- UI framework switching cost is not justified by current needs.
- Less directly related to long-running Hermes tasks than orchestration repos.

## Integration ideas

- Prefer distilling control-plane semantics into Hermes/SStack rather than adopting another runtime by default.
- Any tool that runs shells, agents, worktrees, desktop automation, SSH, provider accounts, or browser/OS control needs disposable-repo sandboxing and auth/filesystem review.
- Reuse the identity, handoff, heartbeat and audit concepts in an existing long-running-work ledger and evaluation suite, not a parallel tracker.

## Alternatives / related repos

- [Agent control planes / dashboards comparison](../comparisons/agent-control-planes-dashboards.md)
- [gastownhall/gastown](gastownhall--gastown.md)
- [generalaction/emdash](generalaction--emdash.md)
- [saltbo/agent-kanban](saltbo--agent-kanban.md)
- [TinyAGI/tinyagi](TinyAGI--tinyagi.md)

## Review guidance

- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
