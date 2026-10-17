---
title: Agent Control Planes / Dashboards Repo Comparison
created: 2026-06-03
updated: 2026-06-03
type: comparison
tags: [github-repos, repo-intelligence, agent-control-planes, dashboards, orchestration, hermes]
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/AndrewKochulab--jarvis-dashboard.md
  - wiki/intel/github-repos/repos/farzaa--clicky.md
  - wiki/intel/github-repos/repos/gastownhall--gastown.md
  - wiki/intel/github-repos/repos/generalaction--emdash.md
  - wiki/intel/github-repos/repos/ghostwright--ghost-os.md
  - wiki/intel/github-repos/repos/msitarzewski--agency-agents.md
  - wiki/intel/github-repos/repos/peters--horizon.md
  - wiki/intel/github-repos/repos/saltbo--agent-kanban.md
  - wiki/intel/github-repos/repos/standardagents--arrow-js.md
---

# Agent Control Planes / Dashboards Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Mine first:** [gastownhall/gastown](../repos/gastownhall--gastown.md) and [saltbo/agent-kanban](../repos/saltbo--agent-kanban.md) for durable operational semantics: identities, ledgers, mailboxes, handoffs, task state, teams, and skills.
- **Watch/sandbox if needed:** [generalaction/emdash](../repos/generalaction--emdash.md) and [peters/horizon](../repos/peters--horizon.md) as visual cockpits for parallel coding agents/terminals.
- **Reference only:** [AndrewKochulab/jarvis-dashboard](../repos/AndrewKochulab--jarvis-dashboard.md), [ghostwright/ghost-os](../repos/ghostwright--ghost-os.md), [farzaa/clicky](../repos/farzaa--clicky.md), [msitarzewski/agency-agents](../repos/msitarzewski--agency-agents.md), and [standardagents/arrow-js](../repos/standardagents--arrow-js.md).

## Decision matrix

| Repo | Layer | Score | Verdict | Reference-stack use |
|---|---|---:|---|---|
| gastownhall/gastown | multi-agent workspace ledger | 88 | distill-pattern | Mailboxes, identities, handoffs, git-backed work state |
| generalaction/emdash | visual parallel coding-agent control plane | 86 | watch | Disposable cockpit bakeoff only |
| saltbo/agent-kanban | agent-first task board | 82 | distill-pattern | Identity/role/skill/team/task-board semantics |
| agno-agi/dash | self-learning data agent | 80 | distill-pattern | Context/eval/data-agent grounding patterns |
| ghostwright/ghost-os | macOS desktop-control substrate | 78 | distill-pattern | Accessibility/MCP/recipe patterns for Mac automation |
| peters/horizon | terminal session canvas | 76 | watch | Multi-agent terminal supervision UX |
| farzaa/clicky | screen-aware AI companion | 72 | reference-only | UX inspiration; public repo is legacy |
| AndrewKochulab/jarvis-dashboard | Obsidian/DataviewJS dashboard | 70 | reference-only | Dashboard/metric inspiration only |
| standardagents/arrow-js | agent-friendly UI framework | 70 | reference-only | Future agent-editable web UI reference |
| msitarzewski/agency-agents | specialist persona library | 68 | reference-only | Sample roles only when needed; no bulk import |

## Category map

1. **Durable work ledgers and task boards** — useful when work spans sessions and needs claims, handoffs, and recovery evidence.
2. **Visual cockpits** — useful if the workload needs many concurrent coding-agent sessions, but high shell/auth/filesystem surface.
3. **Dashboards** — useful visibility patterns; keep Markdown-first and GBrain-indexable where possible.
4. **Desktop-control/companion UX** — future Mac-specific automation references, not Linux Hermes defaults.
5. **Persona libraries/UI frameworks** — discovery/reference only unless a concrete project demands them.

## Reference-stack recommendation

The dated design preference is not another installation. It is a **bounded long-running execution ledger** with:

- task id,
- owner/agent lane,
- claim/lease/expiry,
- branch/worktree/artifact paths,
- heartbeat,
- handoff/mailbox,
- blocker state,
- completion evidence,
- eval/acceptance result,
- keep/revert decision.

Gas Town, Agent Kanban, and Emdash are the best references for that substrate.

## Open questions

- Which existing execution owner can hold the ledger without creating a second backlog?
- Which redacted execution evidence belongs in the operator interface versus private records?
- Is a visual cockpit worth the security surface, or are messaging and process tracking enough?
- Can Wikic verify task-ledger artifacts and links deterministically without expanding beyond its compiler/doctor boundary?
