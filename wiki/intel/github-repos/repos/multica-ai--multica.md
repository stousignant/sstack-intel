---
title: multica-ai/multica
type: repo-intel
source: https://github.com/multica-ai/multica
category: agent-orchestration
status: deep-analyzed
usefulness_score: 88
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-05-27
license: Apache-2.0-with-commercial-restrictions
---

# multica-ai/multica

> Reference-stack fit as reviewed 2026-05-27; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- Usefulness score: `88/100` — Strongest full “agents as teammates” product surface in this batch, but the custom license and app/platform scope make it a watch/sandbox candidate rather than a clean Hermes dependency.
- Recommendation: `watch`.
- **Usage observed 2026-05-27:** `not-used`.
- Review candidate: Watch and distill product semantics; only sandbox after an explicit work-state and evidence contract is defined.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22 | Directly maps to the reference stack’s agent-team/task-board ambitions and explicitly claims Hermes/OpenClaw/Codex runtime support. |
| Leverage | 24 | If real, turns recurring repo work into delegated teammate workflows with blockers, comments, statuses, squads, and autopilots. |
| Reuse readiness | 15 | Self-hosting/docs exist, but it is a large pnpm/Turbo/Postgres/Electron/mobile/web platform, not a small CLI. |
| Maturity/trust | 12 | Very active and released, but modified Apache license restricts hosted/embedded commercial use and frontend branding changes. |
| Differentiation | 15 | More productized than Paperclip/Symphony-style specs; strongest UI/team metaphor but heavier than Hermes-native action trackers. |

## Verdict

Strongest full “agents as teammates” product surface in this batch, but the custom license and app/platform scope make it a watch/sandbox candidate rather than a clean Hermes dependency.

## Reference-stack relevance

- Useful reference for turning Hermes/Kanban/GBrain actions into visible agent work with owners, blockers, recurring autopilots, and progress streams.
- Good “agent teammate” product pattern, but probably too heavy to become the reference stack’s canonical local orchestration layer right now.

## What it is

Open-source managed agents platform for assigning coding work to agents as teammates; includes boards, statuses, comments, squads, autopilots, desktop/mobile/web apps, and self-hosting.

## Live metadata checked

- Source: https://github.com/multica-ai/multica
- Homepage: https://multica.ai
- Primary language: TypeScript
- Stars / forks at review: 33644 / 4055
- Last pushed: 2026-05-27T15:50:57Z
- Latest release: v0.3.10
- License signal: Other
- Topics: none

## Evidence checked

- README claims agents can be assigned issues, report blockers, update statuses, create issues, and work across Claude Code, Codex, Copilot CLI, OpenClaw, OpenCode, Hermes, Gemini, Pi, Cursor Agent, Kimi, and Kiro CLI.
- `package.json` shows a pnpm/Turbo monorepo with web/docs/desktop/mobile scripts, tests, lint, typecheck, Electron/Expo/React Native dependencies.
- `docker-compose.yml` uses local Postgres/pgvector; `SELF_HOSTING.md` exists and is substantial.
- License file is a modified Apache-2.0 with hosted/embedded service and frontend branding restrictions.

## Strengths

- Best product metaphor: agents appear as teammates, not invisible background jobs.
- Autopilots and squads map cleanly to recurring Hermes repo-intelligence/self-improvement work.
- Strong recent activity and release signal.

## Risks / caveats

- Custom license means it is not a clean “reuse/fork commercially later” substrate.
- Large app stack may distract from the reference stack’s Hermes/GBrain/second-brain flywheel.
- Claims broad runtime support; integration depth should be verified before adoption.

## Integration ideas

- Distill board semantics for an existing executable work tracker: assignee, blocker, proof, retry, recurring autopilot. Keep repo intelligence as source evidence, not a task board.
- Sandbox only if an existing execution board needs a richer UI; otherwise keep as design reference.

## Alternatives / related repos

- [paperclipai/paperclip](paperclipai--paperclip.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [Agent Work Orchestration Repo Comparison](../comparisons/agent-work-orchestration.md)

## Review candidates and context

- Watch and distill product semantics; only sandbox after an explicit work-state and evidence contract is defined.
