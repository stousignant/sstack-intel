---
title: "Yeachan-Heo/oh-my-claudecode"
type: repo-intel
source: https://github.com/Yeachan-Heo/oh-my-claudecode
category: agent-orchestration
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# Yeachan-Heo/oh-my-claudecode

> Reference-stack evaluation as reviewed 2026-05-30. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- Usefulness score: `[('Stack fit', 22, 25, 'Excellent fit as a Claude Code lane/reference; not Hermes-native.'), ('Leverage', 23, 25, 'Strong multi-agent workflow leverage.'), ('Reuse readiness', 17, 20, 'Installable npm/plugin paths; needs disposable profile.'), ('Maturity/trust', 13, 15, 'Active, tests, security docs.'), ('Differentiation', 13, 15, 'Team orchestration and strict mode stand out.')]/100` — OMC is the most interesting direct workflow framework in this round: MIT, active, security-aware, multi-agent/team oriented, and specific about Claude Code plugin vs CLI runtimes.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- Review candidate: If a Claude Code lane is under consideration, install in a disposable profile/repo, enable strict security mode, and compare `/team` orchestration against Hermes delegate_task/Kanban handoffs.

## Scorecard
| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22/25 | Excellent fit as a Claude Code lane/reference; not Hermes-native. |
| Leverage | 23/25 | Strong multi-agent workflow leverage. |
| Reuse readiness | 17/20 | Installable npm/plugin paths; needs disposable profile. |
| Maturity/trust | 13/15 | Active, tests, security docs. |
| Differentiation | 13/15 | Team orchestration and strict mode stand out. |

## Verdict

OMC is the most interesting direct workflow framework in this round: MIT, active, security-aware, multi-agent/team oriented, and specific about Claude Code plugin vs CLI runtimes. It should not displace Hermes delegation, but its team/status/shutdown semantics and strict-mode controls are worth distilling; a bounded sandbox is justified if Claude Code becomes an active secondary worker lane.

## Reference-stack relevance
- Maps to multi-agent coordination requirements: “teams-first” orchestration, Codex/Gemini/Claude routes, status/shutdown, and in-session skills.
- Security guide has concrete toggles Hermes should learn from: strict mode, path restrictions, no remote MCP, no external LLM workers, no auto-update, iteration caps.
- Good comparison target for whether Hermes delegate_task + Kanban needs richer team semantics.

## What it is

A TypeScript/npm Claude Code plugin and CLI (`oh-my-claude-sisyphus`, `omc`) for multi-agent orchestration, in-session skills, team mode, runtime CLI, MCP server, and prompt/skill benchmarks.

## Evidence checked
- GitHub metadata via `gh repo view` on 2026-05-30: stars `35369`, forks `3237`, primary language `TypeScript`, archived `False`, fork `False`.
- Maintenance signal: pushed `2026-05-30T20:45:26Z`, updated `2026-05-30T22:36:45Z`, latest release `v4.14.4` `2026-05-26T09:27:38Z`.
- License: `MIT` from GitHub/license file.
- README: `https://raw.githubusercontent.com/Yeachan-Heo/oh-my-claudecode/main/README.md`.
- Top-level manifests/docs inspected locally under [upstream repository inspection](https://github.com/Yeachan-Heo/oh-my-claudecode): README, package/pyproject when present, license, security file when present, top-level contents.
- Repository topics: agentic-coding, ai-agents, claude, claude-code, oh-my-opencode, opencode, vibe-coding, automation, multi-agent-systems, parallel-execution.

## Strengths
- Very active: pushed 2026-05-30; latest release v4.14.4 on 2026-05-26; ~35k stars / 3.2k forks.
- MIT license and npm binary path (`omc`, `oh-my-claudecode`).
- Explicitly distinguishes terminal CLI commands from in-session skills, reducing workflow confusion.
- Security guide documents `OMC_SECURITY=strict` with concrete restrictions.
- Tests/benchmarks/scripts are present in package scripts (`vitest`, prompt benchmarks, metadata verification).

## Risks / caveats
- Claude Code-centered; adopting wholesale would duplicate Hermes delegation/Kanban rather than improve it automatically.
- External LLM/Codex/Gemini worker modes and MCP servers need explicit consent and credential boundaries.
- Large plugin surface; supply-chain/security review required before use on private projects.

## Integration ideas
- Distill team status/shutdown/session semantics into Hermes subagent/Kanban run contracts.
- Adopt the “strict mode” bundle idea for high-risk Hermes skills/plugins.
- If tested, benchmark one review/fix task against Hermes delegate_task with the same proof bundle.

## Alternatives / related repos
- [Claude Code Ecosystem Comparison](../comparisons/claude-code-ecosystem.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [oraios/serena](oraios--serena.md)
- [microsoft/skills](microsoft--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)

## Review candidates and context
- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.

## Score breakdown

| Dimension | Score | Max | Note |
|---|---:|---:|---|
| Stack fit | 22 | 25 | Excellent fit as a Claude Code lane/reference; not Hermes-native. |
| Leverage | 23 | 25 | Strong multi-agent workflow leverage. |
| Reuse readiness | 17 | 20 | Installable npm/plugin paths; needs disposable profile. |
| Maturity/trust | 13 | 15 | Active, tests, security docs. |
| Differentiation | 13 | 15 | Team orchestration and strict mode stand out. |
