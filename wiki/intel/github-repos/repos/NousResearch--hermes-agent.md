---
title: NousResearch/hermes-agent
type: repo-intel
aliases:
  - hermes-agent
  - Hermes Agent
  - GitHub repo: NousResearch/hermes-agent
source: https://github.com/NousResearch/hermes-agent
category: agent-runtime
status: deep-analyzed
usefulness_score: 96
recommendation: adopt-now
usage: active-runtime
score_confidence: high
last_reviewed: 2026-05-25
license: MIT
tags: [github-repo, ai-agent, hermes, local-ai, active-runtime]
---

# NousResearch/hermes-agent

> Reference-stack evaluation as reviewed 2026-05-25. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `96/100` — primary-runtime fit for deployments combining Discord-first operation, local tools, skills, memory, cron, delegation, GBrain/MCP, and Markdown knowledge work.
- **Recommendation:** `adopt-now` — keep using Hermes as the main operational layer; learn it deeply before considering a switch or OpenClaw restart.
- **Usage observed 2026-05-25:** `active-runtime`. Dated observation from one deployment only; no path or configuration is implied.
- **Review candidate:** Use [official Hermes documentation](https://hermes-agent.nousresearch.com/docs) as the learning map; use [Hermes vs OpenClaw](../comparisons/hermes-vs-openclaw.md) when deciding what to borrow from OpenClaw.

## Scorecard

| Factor | Points | Evidence |
|---|---:|---|
| Stack fit | 25/25 | Native fit for the reference stack: Discord, local filesystem/terminal, skills, memory, cron, GBrain MCP, second-brain writes, repo intelligence. |
| Leverage | 25/25 | Skills, delegation, cron, gateway, session search, memory, and plugin/model-provider extensibility directly compound toward time sovereignty and reusable automations. |
| Reuse readiness | 19/20 | Observed installed and running in the reference stack on 2026-05-25; docs, CLI, tests, skills, and plugin surfaces exist. Main cost is learning the large system. |
| Maturity/trust | 14/15 | MIT, active, large test footprint, explicit developer guidance, security/concurrency hardening. Risk is large monolith files and fast-moving surface area. |
| Differentiation | 13/15 | Distinctive among coding agents because it combines personal memory, skills, messaging gateway, scheduled jobs, subagents, and local tooling. |

## Verdict

Hermes is the preferred center of gravity under the dated reference-stack lens: it combines Discord-first interaction, local tools, GBrain/second-brain access, mature skills, cron, delegation, session search, and provider plugins. OpenClaw is worth studying as a gateway/protocol/product reference. The main tradeoff is cognitive load: learn Hermes by subsystem rather than reading the whole repository.

## What it is

Hermes Agent is a Python-first, provider-agnostic agent runtime. The core loop (`run_agent.py`) calls LLMs using OpenAI-compatible message/tool formats, dispatches tools through `model_tools.py`, persists sessions in SQLite, and exposes the same agent through CLI, Discord/Telegram/etc gateway, TUI, ACP/editor integration, cron jobs, and subagents.

## Evidence checked

- Inspected repository: [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent).
- GitHub metadata: https://github.com/NousResearch/hermes-agent
- Repository revision recorded by the historical inspection (not newly verified against upstream): `2a474bcf7 fix(termux): resolve packed-refs and worktree refs in skill-sync fingerprint`.
- Key files inspected: `README.md`, `AGENTS.md`, `pyproject.toml`, `run_agent.py`, `model_tools.py`, `toolsets.py`, `cli.py`, `hermes_cli/main.py`, `hermes_cli/commands.py`, `gateway/run.py`, `gateway/platforms/*`, `hermes_state.py`, `agent/memory_manager.py`, `agent/memory_provider.py`, `wiki/tools/terminal_tool.py`, `wiki/tools/delegate_tool.py`, `cron/jobs.py`, `cron/scheduler.py`, `hermes_cli/mcp_config.py`, `agent/transports/hermes_tools_mcp_server.py`, `tui_gateway/server.py`, `ui-tui/src/*`, `plugins/*`.
- Repo metrics from local inspection: 3,610 tracked files; 1,797 tracked Python files; 1,185 tracked files under `tests/`; ~23,775 pytest test functions by AST count; 69 slash commands; 72 tool registrations; 89 bundled skills; 81 optional skills.
- GitHub metadata checked live on 2026-05-25: MIT, primary language Python, active main branch, homepage `https://hermes-agent.nousresearch.com`.

## Architecture map

### 1. Agent runtime

- `run_agent.py` — `AIAgent`, core conversation/tool loop, provider routing, memory/context integration, callbacks, budget/interrupt behavior.
- `model_tools.py` — tool schema discovery and tool dispatch. Imports `wiki/tools/registry.py` and built-in tools.
- `toolsets.py` — maps capabilities into toolsets (`web`, `terminal`, `file`, `skills`, `delegation`, `cronjob`, etc.) and defines the core bundle.
- `agent/` — provider helpers, prompt building, context compression, memory integration, title generation, transports.

Mental model: Hermes is **not just a chatbot**. It is an LLM loop with a large tool registry, persistent state, and multiple front doors.

### 2. Surfaces / front doors

- `hermes_cli/main.py` — actual package entrypoint for the `hermes` CLI; applies profile override early and routes subcommands.
- `cli.py` — classic Rich/prompt_toolkit interactive CLI, slash-command dispatch, display/spinner behavior.
- `gateway/run.py` — long-lived messaging gateway for Discord, Telegram, Slack, WhatsApp, Signal, Matrix, Email, SMS, Home Assistant, Feishu, WeCom, etc.
- `ui-tui/` + `tui_gateway/` — Ink/React terminal UI frontend and Python JSON-RPC backend.
- `acp_adapter/` — Agent Client Protocol integration for editors.
- `cron/` — scheduled autonomous jobs.

### 3. Persistence and personalization

- `hermes_state.py` — SQLite session DB, FTS5 session search, parent/child session relationships, branches, compression continuations.
- `agent/memory_manager.py` and `agent/memory_provider.py` — memory manager and plugin provider abstraction.
- `plugins/memory/*` — Honcho, Mem0, Supermemory, Hindsight, Byterover, RetainDB, etc.
- `skills/`, `optional-skills/`, `wiki/tools/skills_hub.py`, `agent/skill_commands.py` — procedural memory and skill loading/editing.
- `$HERMES_HOME/config.yaml` and `$HERMES_HOME/.env` — config vs secrets split.

### 4. Extensibility

- `wiki/tools/*.py` self-register tools through `wiki/tools/registry.py`.
- `plugins/*` provide model providers, memory providers, gateway platforms, web/browser/image/video providers, hooks, dashboards, and more.
- `hermes_cli/plugins.py` loads plugin directories with `plugin.yaml` + `register(ctx)`.
- `hermes_cli/mcp_config.py`, `wiki/tools/mcp_tool.py`, `agent/transports/hermes_tools_mcp_server.py` integrate external MCP servers and expose selected Hermes tools over MCP.

## Strengths

- **Workload fit is strong:** The inspected integration combines Discord, local code/files, terminal, GBrain, Markdown knowledge, repo intelligence, and scheduled automations.
- **Skills are high leverage:** procedural memory loads on demand and can improve over time. This is the key compounding layer.
- **Cron + gateway = proactive agent:** Hermes can run unattended checks and deliver results back to Discord, not just answer prompts.
- **Delegation gives parallelism:** subagents can inspect repos, debug, or research in isolated contexts without flooding the parent context.
- **Provider/plugin flexibility:** model providers, memory providers, web/browser/image providers, and platform integrations are pluginized.
- **Serious operational surface:** terminal backends, process tracking, checkpoints, session search, TUI, ACP, MCP, kanban, logs.
- **Tests and docs are unusually broad:** the repo has a large pytest footprint and very explicit `AGENTS.md` development guidance.

## Risks / caveats

- **Large monolith files:** `gateway/run.py`, `cli.py`, `hermes_cli/main.py`, and `tui_gateway/server.py` are big. Small changes can have wide blast radius.
- **Many config pathways:** CLI, gateway, TUI, plugins, profiles, `.env`, and `config.yaml` can drift if changes are not centralized.
- **Profile path footguns:** stateful code must use `get_hermes_home()` rather than hardcoded default-profile paths.
- **Gateway complexity:** approvals, background process notifications, platform sessions, cron, kanban, slash commands, auth, and provider errors all cross the gateway.
- **Plugin and skill trust:** plugins and skills run with agent-level power; third-party install should be treated as code execution, not just content.
- **Prompt-cache sensitivity:** changing system prompt/toolsets/memory mid-session is expensive and can destabilize behavior.

## Integration ideas

1. **Use Hermes skills as the reusable workflow layer.** If a task takes 5+ tool calls or teaches a stable workflow, save/update a skill.
2. **Use GBrain/second-brain as the durable human knowledge layer.** Hermes memory should hold compact preferences/environment facts; the vault holds long-lived notes and reports.
3. **Use cron for proactive loops.** Dream-cycle, repo-intel refreshes, GBrain health, and morning briefings belong here.
4. **Use delegation for deep one-shot analysis.** Parallel inspectors can keep deep one-shot evidence out of the controller's context.
5. **Prefer plugins before core edits.** For a custom feature, first check whether a skill, plugin, MCP server, or cron job provides the required capability.

## Learning path

See [official Hermes documentation](https://hermes-agent.nousresearch.com/docs). Short version:

1. Learn daily commands and slash commands.
2. Learn toolsets and skills.
3. Learn config/profiles/logs.
4. Learn the agent loop and tool dispatch.
5. Learn gateway/cron/delegation.
6. Learn plugins/MCP only when extending.

## Alternatives / related repos

- [openclaw/openclaw](openclaw--openclaw.md) — gateway-first multi-device personal AI assistant; best reference for protocol discipline, schema-driven config, device nodes, and channel breadth.
- [garrytan/gbrain](garrytan--gbrain.md) — active index/query layer for the canonical second-brain vault.
- [paperclipai/paperclip](paperclipai--paperclip.md) — agent-company/control-plane semantics reference.

## Review candidates and context

- Use [Hermes Agent vs OpenClaw](../comparisons/hermes-vs-openclaw.md) for the current comparison verdict.
- Keep Hermes as primary runtime; study OpenClaw for gateway/protocol/UI patterns rather than restarting the whole stack around it.
- Treat future learning gaps as candidates; any executable follow-up belongs in the established issue tracker.
