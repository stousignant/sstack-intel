---
title: XiaomiMiMo/MiMo-Code
type: repo-intel
source: https://github.com/XiaomiMiMo/MiMo-Code
category: coding-agent-runtime
topics: [github-repo, coding-agent-runtime, opencode-fork, agent-memory, autonomous-coding]
status: deep-analyzed
usefulness_score: 89
recommendation: adopt-now
usage: sandboxed
score_confidence: high
last_reviewed: 2026-06-20
license: MIT
---

# XiaomiMiMo/MiMo-Code

> Reference-stack evaluation as reviewed 2026-06-20; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `89/100` — very high signal as an OpenCode-derived coding-agent runtime that adds persistent memory, checkpoint/context reconstruction, subagents, stop-goal judging, compose workflows, and dream/distill loops; sandbox it, do not replace Hermes.
- Recommendation: `adopt-now` for a bounded disposable-repo bakeoff and pattern extraction.
- **Usage observed 2026-06-20:** `sandboxed`. `npx -y @mimo-ai/cli@0.1.1 --version` and `--help` were run with temporary `HOME` / `MIMOCODE_HOME`; the review did not establish runtime adoption.
- Confidence: `high`.
- Review candidate: compare MiMoCode against Hermes/Codex/OpenCode on one small disposable coding task, then distill only the winning memory/checkpoint/goal/compose patterns into SStack/Hermes.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Directly adjacent to Hermes, Codex worker lanes, OpenCode, agent memory, checkpoints, subagents, and self-improvement loops. |
| Leverage | 23/25 | Its strongest value is making long-horizon coding sessions less brittle: persistent memory, checkpoint reconstruction, `/goal` stop-condition judging, and `/dream` / `/distill` self-improvement. |
| Reuse readiness | 18/20 | MIT, npm package `@mimo-ai/cli`, one-command install, provider-agnostic config, MCP, ACP, agents, sessions, import/export; CLI `--version` and `--help` worked locally. |
| Maturity/trust | 13/15 | Very new but active: created 2026-06-10, v0.1.1 on 2026-06-15, pushed 2026-06-19, 10k+ stars; has tests and security policy, but inherits OpenCode no-sandbox risk. |
| Differentiation | 12/15 | Differentiates from vanilla OpenCode through memory/checkpoint/subagent/goal/compose/dream/distill features; overlaps heavily with Hermes so the win must be pattern distillation or a narrow worker lane. |
| **Total** | **89/100** | Strong sandbox candidate and pattern source, not a default-runtime migration. |

## Verdict

MiMoCode is worth a serious **sandbox bakeoff**, not a blind install alongside an established runtime. It is a fast-moving Xiaomi fork of OpenCode aimed at long-horizon coding: project/session/task memory, context reconstruction, subagents, goal-driven stop conditions, compose skills, and self-improvement passes. These capabilities are relevant when a Hermes/GBrain/SStack workflow has a measurable continuity or completion gap. The catch: it is another broad shell-capable coding-agent runtime, OpenCode's own security policy says there is no real sandbox, and the free MiMo channel / OAuth / Claude credential import paths are trust-boundary sensitive. Keep Hermes as cockpit and test MiMoCode only in disposable workspace/profile mode.

## Reference-stack relevance

- It is an unusually direct external reference for long-running agent workloads that must remember, checkpoint, resume, delegate, judge completion, and turn repeated work into reusable assets.
- The built-in memory model is close enough to Hermes/GBrain/second-brain concerns to be useful as a comparison, but not close enough to become canonical memory without a bakeoff.
- `/goal` is a clean pattern for preventing optimistic stops: an independent judge evaluates whether the transcript actually satisfies the stop condition.
- `/dream` and `/distill` illustrate a self-improvement pattern: consolidate durable memory and package repeated workflows into skills/subagents/commands.
- Because it is OpenCode-derived, it is more relevant than many greenfield agent projects: it inherits a real TUI/provider/MCP/LSP/plugins substrate and adds long-horizon semantics on top.

## What it is

MiMoCode describes itself as a terminal-native AI coding assistant that can read/write code, run commands, manage Git, use persistent project memory, reconstruct context across sessions, spawn subagents, run goal-conditioned autonomous loops, and execute compose-mode spec/skill workflows. The repository is TypeScript/Bun-heavy, published as `@mimo-ai/cli`, and presents itself as an OpenCode fork with added persistent memory, intelligent context management, subagent orchestration, goal-driven autonomous loops, compose workflows, and self-improvement via dream/distill.

## Evidence checked

- GitHub metadata via `gh repo view XiaomiMiMo/MiMo-Code`: `10,013` stars, `921` forks, MIT license, primary language TypeScript, latest release `v0.1.1` published `2026-06-15`, last push `2026-06-19T16:07:03Z`, topics `ai`, `ai-agents`, `cli`, `mimo`, `mimo-code`.
- README via GitHub: claims terminal-native coding assistant, MiMo Auto free-for-limited-time channel, mainstream LLM provider support, `build`/`plan`/`compose` agents, persistent SQLite FTS5 memory, checkpoint/context reconstruction, task tracking, subagents, `/goal`, voice input, `/dream`, `/distill`, and OpenCode relationship.
- npm metadata via `npm view @mimo-ai/cli`: package `@mimo-ai/cli@0.1.1`, MIT, binary `mimo`, published/released June 2026.
- Local clone: a disposable source checkout, commit `17bf5e43a91d5ee8ed450a22127cc6228bb2e194` (`Merge pull request #1149 from XiaomiMiMo/fix/remove-claude-origin-mcp-skip`).
- Local smoke tests:
  - `npx -y @mimo-ai/cli@0.1.1 --version` with isolated temporary `HOME` and `MIMOCODE_HOME` returned `0.1.1`.
  - Same sandboxed env with `--help` ran a one-time SQLite migration and listed commands including `run`, `serve`, `mcp`, `providers`, `agent`, `session`, `plugin`, `db`, `acp`, `github`, `pr`, and options including `--model`, `--continue`, `--session`, `--fork`, `--agent`, `--never-ask`, and `--trust`.
- Security policy: `SECURITY.md` states OpenCode/MiMoCode does **not** sandbox the agent; permission prompts are UX awareness, not isolation. Server mode is opt-in; without `OPENCODE_SERVER_PASSWORD`, server runs unauthenticated with a warning.
- Use restrictions: `USE_RESTRICTIONS.md` forbids unlawful/malicious uses, military use, malicious cyber activity, unauthorized personal-data access, and autonomous high-risk actions without human oversight.
- Code inspected:
  - `packages/opencode/src/memory/service.ts` — SQLite FTS5 memory service with lazy reconcile and BM25 scoring floor.
  - `packages/opencode/src/session/checkpoint.ts` — checkpoint writer, context boundary computation, tail preservation, rebuild context, memory/checkpoint/notes/task progress paths.
  - `packages/opencode/src/session/goal.ts` — per-session stop-condition goal and independent JSON judge.
  - `packages/opencode/src/agent/agent.ts` — native `build`, `plan`, `compose`, `general`, `explore`, `checkpoint-writer`, `dream`, and `distill` agents with permissions/tool allowlists.
  - `packages/opencode/src/actor/spawn.ts` — subagent/fork actor lifecycle, actor IDs, parent/child session handling, return-format contract, and cancellation.
  - `packages/opencode/src/config/config.ts` — config fields for checkpoint thresholds, memory search, Claude Code memory indexing, dream/distill auto intervals, provider/model/MCP/agent/plugin options.
  - `packages/opencode/src/skill/compose/.bundle/` — built-in compose skills for planning, execution, review, TDD, debugging, verification, merge, parallel/subagent, self-extension, worktrees, and new-skill authoring.
- Test surface: local clone contains `323` `*.test.ts` files under `packages/opencode/test`, including workflow, actor, tool, memory/checkpoint-adjacent, TUI, and utility tests. Tests were not run because dependencies were not installed; root `package.json` explicitly says not to run tests from the repo root.

## Strengths

- **Long-horizon agent semantics are real in code, not just README copy.** Memory service, checkpoint code, goal judge, actor spawning, dream/distill agents, and compose skill bundles are implemented in the repository.
- **OpenCode substrate plus new memory/autonomy layer.** It appears to keep OpenCode's provider/TUI/MCP/LSP/plugin ecosystem while adding long-horizon context and workflow mechanics.
- **Good fit for pattern mining.** The checkpoint writer, rebuild context budgets, task progress reconciliation, `/goal` judge, and compose-skill packaging are all directly comparable to Hermes cron/delegation/GBrain/session handoff skill workflows.
- **Easy first smoke test.** npm package can be invoked by `npx` without global install; `--version` and `--help` worked under temporary home directories.
- **Explicit security caveats.** The no-sandbox warning is a negative for adoption but a positive for honesty; it makes the threat model clearer than many agent runtimes.
- **MIT license and active early velocity.** Released and pushed within days of review, with substantial star/fork traction.

## Risks / caveats

- **No real sandbox.** This is the biggest adoption boundary. Treat permissions as prompts, not containment; run inside disposable repos/containers/VMs for autonomous or untrusted tasks.
- **Credential/trust boundaries need care.** README advertises MiMo Auto, Xiaomi MiMo OAuth, custom OpenAI-compatible providers, and one-step import from Claude Code. Do not import existing real provider credentials in a first pass.
- **Server mode can expose dangerous local control.** `--hostname`, `--port`, mDNS, CORS, and `serve` are useful but should stay loopback/private; set auth if enabled.
- **Very new project.** Created June 2026 and still `0.1.1`; strong activity signal, but API/behavior may churn fast.
- **Parallel runtime sprawl.** Hermes already owns memory, tools, skills, cron, Discord cockpit, GBrain, and second-brain integration. MiMoCode should have to win a bakeoff before becoming anything more than a sandbox worker/reference.
- **README relationship wording is odd.** It says it is built as a fork of OpenCode but links the OpenCode text to the MiMo-Code repo itself; code/package metadata still contains OpenCode ancestry (`package.json` name/repository and `SECURITY.md` references anomalyco/opencode).

## Integration ideas

- **Goal-gated autonomous loops:** port the `/goal` pattern into Hermes task/delegation flows: a user-set stop condition plus an independent judge that can force another iteration when evidence is missing.
- **Checkpoint/rebuild context:** compare MiMoCode's checkpoint sections, task progress diffs, tail boundary, and memory budgets against Hermes session handoff / context compaction. Steal the small bits that reduce “agent stopped too early” and “lost plot after compaction.”
- **Self-improvement lane:** compare `/dream` and `/distill` to Hermes dream-cycle / skill-drift workflows. The useful shape is reviewed proposal output, not autonomous mutation of a canonical operating stack.
- **Compose-skill bundle:** mine the built-in compose skills for SStack skill-authoring/testing patterns, especially plan/execute/review/TDD/verify/merge/self-extend.
- **Worker-lane bakeoff:** run one disposable coding task through Hermes, Codex/OMX, OpenCode, and MiMoCode with the same proof-bundle requirements. If MiMoCode wins on continuity or goal satisfaction, consider a narrow “MiMo sandbox worker” lane supervised by Hermes.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — active cockpit/runtime; keep as default.
- [anomalyco/opencode](anomalyco--opencode.md) — upstream-ish runtime reference and comparison baseline.
- [Yeachan-Heo/oh-my-codex](Yeachan-Heo--oh-my-codex.md) — Codex-native worker-lane harness candidate.
- [obra/superpowers](obra--superpowers.md) — focused multi-harness development workflow enhancer.
- [automazeio/ccpm](automazeio--ccpm.md) — spec/epic/task/worktree workflow baseline.

## Review guidance

- Promote only if an executable experiment is warranted: define a bounded MiMoCode bakeoff with no real provider-credential import, no global install, loopback-only server use, and a fixed proof-bundle rubric.
- Revisit after one more release cycle or after the first bakeoff; watch specifically for security hardening, config/schema stability, and whether memory/checkpoint behavior materially beats Hermes/Codex on real work.
