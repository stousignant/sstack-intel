---
title: eyaltoledano/claude-task-master
type: repo-intel
aliases:
  - claude-task-master
  - Taskmaster
  - Task Master AI
  - GitHub repo: eyaltoledano/claude-task-master
source: https://github.com/eyaltoledano/claude-task-master
category: task-management
topics: [github-repo, repo-intelligence, task-management, mcp, ai-development, prd]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT WITH Commons-Clause
---

# eyaltoledano/claude-task-master

> Opinionated reference-stack evaluation, reviewed 2026-05-28. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — strong task/dependency schema and MCP/CLI reference, but license constraints and overlap with Hermes/Kanban mean pattern distillation beats adoption.
- **Recommendation:** `distill-pattern` — copy task fields, dependency semantics, complexity reports, tags/workstreams, and MCP sampling ideas; do not make it the canonical task store.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Compare its `tasks.json` schema against the established executable work owner before adopting any task-store mechanics.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 22/25 | Directly overlaps AI development task decomposition, MCP, PRD parsing, and dependency-aware execution. |
| Leverage | 22/25 | Could improve multi-step coding runs and prevent hidden task drift. |
| Reuse readiness | 16/20 | npm package, CLI, MCP server, docs, tests; easy to try, but bigger than a small helper. |
| Maturity/trust | 11/15 | Active, popular, CI/tests; Commons Clause limits commercial/hosted reuse. |
| Differentiation | 13/15 | More concrete task lifecycle than generic todos: dependencies, complexity, research, tags/workstreams. |

## Verdict

Taskmaster is a useful **task semantics reference**, not a default replacement for Hermes/GBrain/Kanban. Its most reusable asset is the task object: title, status, dependencies, priority, details, test strategy, subtasks, complexity analysis, and update history. The license is MIT with Commons Clause, so direct reuse in products/hosted services needs caution.

## Workload fit

- Multiple durable task surfaces can fragment work truth. Taskmaster is a concrete task-schema design to compare against, not permission to add another tracker.
- The MCP server and session-sampling provider pattern could inform Hermes task agents.
- The `research` and `loop` commands are relevant to autonomous coding, but risky without strong proof/eval gates.

## What it is

Taskmaster is an AI-powered task management system for AI-driven development. It parses PRDs into dependency-aware tasks, exposes CLI commands, and ships an MCP server for editors/agents. It supports multiple AI providers and workstreams/tags.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 27,277 stars, 2,542 forks, JavaScript primary language, pushed 2026-04-28, license metadata `Other`.
- README: docs, npm package, Cursor one-click MCP install, supported editors, CLI/MCP/task/dependency/research/loop docs.
- `package.json`: package `task-master-ai` 0.43.1, bins `task-master`, `task-master-mcp`, `task-master-ai`, tests/build scripts, publish provenance, license `MIT WITH Commons-Clause`.
- `LICENSE` and `docs/licensing.md`: Commons Clause forbids selling Task Master itself, hosting it as a service, or competing products based on it.
- `.taskmaster/config.json`: model roles for main/research/fallback and settings such as codebase analysis and telemetry.
- `docs/task-structure.md`: fields for task id/title/status/dependencies/priority/details/testStrategy/subtasks and complexity reporting.
- `docs/command-reference.md`: parse PRD, list, next, show, update, update-task, update-subtask, and related commands.
- `docs/mcp-provider.md`: MCP Provider implementation and structured object generation support.

## Strengths

- Concrete task format designed for both humans and AI agents.
- Dependency-aware `next` semantics are better than flat TODO lists.
- MCP server makes the workflow agent-friendly.
- Complexity analysis and research-backed updates are useful patterns.

## Risks / caveats

- Commons Clause makes wholesale adoption less suitable for reusable or commercial software.
- Could create another task truth store beside session-local todos, canonical issue tracking, and derived execution boards.
- Telemetry/config defaults should be reviewed before any local install.
- Autonomous `loop` behavior needs approval/proof gates before trust.

## Integration ideas

- Distill a common task schema for the established work-state owner: dependencies, test strategy, evidence, blocker, owner, wake path.
- Use dependency and status semantics to identify the next actionable task in the existing executable work tracker, not in repo-intelligence notes.
- Borrow MCP sampling/provider mechanics only if Hermes needs agent-native task generation.

## Alternatives / related repos

- [github/spec-kit](github--spec-kit.md) — upstream spec/plan/tasks generator.
- [bmad-code-org/BMAD-METHOD](bmad-code-org--BMAD-METHOD.md) — broader lifecycle methodology.
- [openclaw/lobster](openclaw--lobster.md) — typed workflow shell and dry-run/resume semantics.
- [paperclipai/paperclip](paperclipai--paperclip.md) — issue-liveness semantics.

## Review candidates and context

- Non-binding guidance; executable state belongs to the established issue tracker.
