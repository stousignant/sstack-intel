---
title: paperclipai/paperclip
type: repo-intel
aliases:
  - GitHub repo: paperclipai/paperclip
source: https://github.com/paperclipai/paperclip
url: https://paperclip.ing
category: agent-orchestration
status: deep-analyzed
topics: [github-repo, agent-orchestration, ai-companies, control-plane, local-ai]
usefulness_score: 88
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-05-24
license: MIT
---

# paperclipai/paperclip

> Reference-stack evaluation as reviewed 2026-05-24; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `88/100` — very high fit as an AI-agent company/control-plane reference, but heavier than Hermes/GBrain needs for most single-agent and second-brain workflows.
- **Recommendation:** `distill-pattern` — do not blindly make Paperclip the canonical task system yet; extract its strongest primitives into Hermes/GBrain/second-brain workflows, and only run Paperclip as a dedicated control plane when there is a real multi-agent company workload.
- **Usage observed 2026-05-24:** `pattern-in-use` — issue/liveness/control-plane patterns informed the reference evaluation; this is not runtime-adoption evidence.
- **Review candidate:** Use Paperclip's issue/liveness/checkout/budget semantics to harden the existing execution system and Hermes multi-agent operating loops.

## Scorecard

| Factor | Points | Rationale |
|---|---:|---|
| Stack fit | 24/25 | Directly maps to Hermes/PAI/local-agent orchestration needs: companies, agents, issues, goals, heartbeats, budgets, skills, and adapters. |
| Leverage | 23/25 | Strong model for supervising multiple agents through a board/operator surface; potential leverage depends on workload and operating cost. |
| Reuse readiness | 17/20 | MIT, active, one-command local/dev setup, Docker path, MCP server, CLI, docs, adapters; still complex enough that adoption cost is non-trivial. |
| Maturity/trust | 12/15 | Large active repo, current release, many tests, security docs, but fast-moving and likely product/API churn. |
| Differentiation | 12/15 | More complete control-plane model than ad hoc cron + todos; less clearly necessary for simple knowledge tasks where Hermes-native primitives are enough. |
| **Total** | **88/100** | High-value infrastructure/reference; direct adoption should be workload-driven, not ideology-driven. |

## Verdict

Paperclip is one of the strongest external references in this corpus for **agent work as a governed operating system** rather than “run some bots.” The useful thing is not the hype phrase “zero-human companies”; it is the concrete product vocabulary: company-scoped data, single-assignee issues, atomic checkout, heartbeat execution, budgets, approvals, run liveness, recovery actions, workspaces, skills, adapters, and audit trails.

**Use Paperclip as a design oracle and occasional runtime, not as a mandatory substrate for every task.** Hermes already has native cron jobs, subagents, session todos, skills, Discord delivery, GBrain, and file-level control. Where these own execution and knowledge state, first distill Paperclip's liveness and issue semantics into the existing execution owner and Hermes procedures. Run Paperclip itself only when a multi-agent workload requires a visible board with delegation, budgets, approvals, and persistent execution state.

## What it is

Paperclip is an open-source Node.js/TypeScript + React control plane for “AI-agent companies.” It sits above agent runtimes and coordinates them through:

- companies and goals,
- agents with roles/org-chart positions/adapters,
- issues/tasks with comments and documents,
- heartbeat-based execution,
- budget/cost tracking,
- approvals and governance,
- workspaces and runtime services,
- plugins, skills, MCP, secrets, and audit/event logs.

The README's framing is explicit: “If OpenClaw is an employee, Paperclip is the company.”

## Fresh metadata checked

Checked on 2026-05-24:

- GitHub: https://github.com/paperclipai/paperclip
- Homepage/docs: https://paperclip.ing
- License: MIT
- Default branch: `master`
- Latest release: `v2026.517.0`, published 2026-05-17
- Last pushed: 2026-05-24
- Stars: 67,464
- Forks: 12,383
- Shallow clone inspected at a disposable source checkout, commit `96f0279`
- Runtime evidence limit: no running Paperclip instance was verified in this review.

## Evidence checked

Primary files/docs inspected:

- `README.md` — product pitch, quickstart, feature map, architecture surface.
- `AGENTS.md` — contributor/agent rules, repo map, control-plane invariants.
- `doc/GOAL.md` — strategic framing: Paperclip as backbone/control plane for autonomous AI companies.
- `doc/SPEC-implementation.md` — V1 product contract and canonical data model.
- `doc/DEVELOPING.md` — local dev, one-command run, Docker, auth/private deployment, test guidance.
- `doc/execution-semantics.md` — issue ownership/status/liveness model.
- `ROADMAP.md` — plugin system, OpenClaw/claw agents, import/export, skills, routines, budgeting, approvals, memory/knowledge, enforced outcomes.
- `packages/mcp-server/README.md` — MCP wrapper over Paperclip REST API.
- Package manifests and repo layout.

Static evidence:

- Monorepo packages include `server`, `ui`, `cli`, `packages/db`, `packages/shared`, `packages/mcp-server`, adapter packages for Claude/Codex/OpenClaw/Cursor/Gemini/OpenCode/Pi/Grok, plugin packages, and sandbox providers.
- Test surface found: `443` `*.test.ts`, `16` `*.spec.ts`, `91` `*.test.tsx` files.
- Approximate major source surface found: `server/src` 471 TypeScript files, `ui/src` 250 TS + 336 TSX files, `packages` 523 TS files.

## Reference-stack relevance

Paperclip is directly relevant to self-improving agent stacks where governed autonomy should reduce supervision and operating burden.

High-fit patterns:

1. **Agent work becomes first-class operational state.** Work is not “a prompt happened.” It is issue → owner → run → comments/documents → artifacts → status → cost/audit.
2. **Liveness is explicit.** The system asks: what moves this issue forward next? This addresses a common weakness in Markdown task files: stale todos with no executor or wake path.
3. **Budget and governance are structural.** Agent autonomy without spend/approval boundaries is just chaos with invoices.
4. **Adapters are the right abstraction.** Claude Code, Codex, OpenClaw, HTTP bots, process agents, and external plugins become interchangeable employees behind a common control plane.
5. **Goal ancestry matters.** Tasks should carry the “why” from project/company goals, preserving rationale across PAI/GBrain/Hermes context capsules and execution handoffs.
6. **MCP server exists.** Paperclip can expose control-plane actions as tools to agents rather than forcing all integrations through brittle raw REST curls.

## Strengths

- **Strong conceptual model:** company → goals → agents → issues → runs → artifacts/audit is the right mental model for multi-agent work.
- **Concrete V1 contract:** `doc/SPEC-implementation.md` is unusually explicit about scope, data model, status semantics, and invariants.
- **Execution semantics are thoughtful:** single-assignee, checkout locks, blockers vs parent/sub-issue, recovery actions, monitors, and liveness paths are exactly the kind of hard edge most agent demos ignore.
- **Local-first path exists:** embedded PostgreSQL, local instance root under `~/.paperclip/instances/default`, Docker path, local trusted mode, private/authenticated deployment options.
- **Adapter ecosystem:** built-in adapter packages for major local coding-agent runtimes plus OpenClaw gateway and plugin/adapters story.
- **MCP surface:** `@paperclipai/mcp-server` exposes Paperclip operations as agent tools.
- **Good evidence of active engineering:** fresh release, current pushes, broad tests, docs, scripts, migration/test/build workflow.

## Risks / caveats

- **Heavyweight for current Hermes-only work.** If the job is “answer in Discord, update second-brain, run a cron,” Paperclip may add UI/state/process overhead without improving outcome.
- **Fast-moving surface.** Release cadence and large codebase imply churn; notes and adapters can stale quickly.
- **Control plane ≠ intelligence.** Paperclip organizes agents; it does not replace Hermes' reasoning, GBrain retrieval, PAI context, or second-brain synthesis.
- **Budget/cost safety depends on accurate reporting.** The architecture supports budgets, but each adapter must report costs correctly or budget enforcement becomes theater.
- **Security blast radius.** A system that can wake local coding agents, inject secrets, and manage workspaces needs strict trust boundaries. Treat plugins/adapters as privileged code.
- **No local runtime verified in this refresh.** The repo is inspectable and mature-looking, but no running instance was verified in this analysis.

## Integration ideas

### 1. Borrow Paperclip's issue-liveness model for an existing work system

An existing issue/workflow system can borrow these principles:

- one owner per issue,
- explicit status semantics,
- every executable issue needs a next wake/action path,
- blockers are dependencies; parent/sub-issue is structure,
- “done” requires evidence/outcome, not vibes,
- recovery actions exist when execution gets stranded.

This is often more valuable than running a Paperclip server for a lightweight single-agent task.

### 2. Use Paperclip for “agent company” experiments only

Good Paperclip candidates:

- repo-intelligence batch analysis with multiple specialist agents,
- nightly self-improvement/dream-cycle workers with a visible board,
- multi-stage research digest pipeline with ingestion, extraction, review, and publishing steps,
- software projects where Codex/Claude/OpenClaw agents need persistent issues and workspaces,
- high-autonomy workflows requiring budgets/approvals/audit.

Bad Paperclip candidates:

- one-shot chat answers,
- simple local file edits,
- small GBrain/second-brain maintenance tasks,
- anything where Hermes native cron/subagent/todo is simpler and sufficient.

### 3. Treat Paperclip MCP as the clean integration path

If Paperclip is selected for a future workload, prefer its MCP server over raw curl in future agent workflows:

- `paperclipListIssues`, `paperclipGetIssue`, `paperclipCheckoutIssue`, `paperclipAddComment`, etc.
- Keep raw REST curl only as fallback or when MCP is unavailable.

### 4. Compare against Hermes-native orchestration

The reference stack assumes these Hermes capabilities:

- `delegate_task` for subagents,
- `cronjob` for schedules,
- session `todo` for execution checklists,
- skills for procedural memory,
- Discord delivery,
- GBrain/second-brain for durable knowledge.

Paperclip should win only when persistent multi-agent state, UI visibility, budgets, approvals, workspaces, or task/run audit materially improve a workload enough to justify the extra control plane.

## Alternatives / related repos

- [garrytan/gbrain](garrytan--gbrain.md) — canonical brain/index/query layer, not an agent work control plane.
- [hesamsheikh/awesome-openclaw-usecases](hesamsheikh--awesome-openclaw-usecases.md) — idea/pattern catalog for agent workflows.
- [code-yeongyu/oh-my-openagent](code-yeongyu--oh-my-openagent.md) — likely related multi-agent orchestration candidate; still lightweight-triaged.
- [eyaltoledano/claude-task-master](eyaltoledano--claude-task-master.md) — task decomposition/orchestration candidate; still lightweight-triaged.
- [openclaw/openclaw](openclaw--openclaw.md) — runtime/agent layer; Paperclip frames itself as the company layer above claw-style workers.

## Promoted disposition and guidance

- Review candidate: distill issue-liveness semantics into the existing execution owner rather than creating a competing task store.
- Guidance: A local multi-agent company experiment requires explicit operator authorization for a workload needing that control plane; test the MCP server path before designing new custom orchestration.
- Guidance: Revisit adapter/plugin security before letting Paperclip run high-privilege local agents unattended.
