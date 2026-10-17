---
title: nanocoai/nanoclaw
type: repo-intel
aliases:
  - nanoclaw
  - GitHub repo: nanocoai/nanoclaw
source: https://github.com/nanocoai/nanoclaw
category: personal-agent-runtime
topics: [github-repo, repo-intelligence, openclaw, agent-runtime]
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# nanocoai/nanoclaw

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `88/100` — Strongest runtime-design reference in this batch: lightweight container-isolated personal agent, messaging adapters, per-agent workspaces, scheduled jobs, credential vaulting, and explicit privacy boundaries; still not a replacement for Hermes.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Mine NanoClaw for container/session/credential-isolation and channel-boundary patterns; consider sandbox only if Hermes needs messaging-agent isolation beyond current Discord gateway.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Relevant to Hermes/GBrain/second-brain agent runtime, eval, operations, or isolation design without replacing the active runtime. |
| Leverage | 24/25 | Could improve autonomous-agent safety, eval quality, work orchestration, or self-improvement loops. |
| Reuse readiness | 17/20 | README/manifests provide install paths; most should remain sandbox/pattern-only because they touch runtimes, credentials, or training loops. |
| Maturity/trust | 13/15 | Live metadata: 29542 stars, 12887 forks, pushed 2026-05-30T07:42:43Z, license MIT. |
| Differentiation | 10/15 | Differentiates through runtime isolation, economic eval, self-improvement scheduler, or team/orchestration semantics. |

## Verdict

Strongest runtime-design reference in this batch: lightweight container-isolated personal agent, messaging adapters, per-agent workspaces, scheduled jobs, credential vaulting, and explicit privacy boundaries; still not a replacement for Hermes. The default is still **Hermes as active runtime**. The useful payload is not migrating into the OpenClaw ecosystem; it is extracting runtime-isolation, eval, governance, economic-accountability, and self-improvement patterns that can strengthen Hermes/GBrain/second-brain workflows.

## Reference-stack relevance

- These repos are adjacent to the same problem Hermes is solving: personal agents that can work across channels, tools, memory, and tasks without melting down.
- The leverage is in design patterns: container boundaries, task/eval economics, approval/gateway control, and safe self-improvement windows.
- Broad OpenClaw/NanoClaw/OMO runtimes overlap heavily with Hermes; adoption only makes sense for tiny disposable bakeoffs or if they reveal a clear missing primitive.

## What it is

NanoClaw is a lightweight personal Claude assistant runtime that routes messaging channels into per-agent containers with isolated workspaces, SQLite queues, scheduled tasks, memory, and OneCLI credential injection.

## Live metadata checked

- Source: <https://github.com/nanocoai/nanoclaw>
- Description: A lightweight alternative to OpenClaw that runs in containers for security. Connects to WhatsApp, Telegram, Slack, Discord, Gmail and other messaging apps,, has memory, scheduled jobs, and runs directly on Anthropic's Agents SDK
- Stars / forks: 29542 / 12887
- Primary language: TypeScript
- License: MIT
- Latest release: v2.0.64 / 2026-05-18T18:01:05Z
- Last pushed: 2026-05-30T07:42:43Z
- Topics: ai-agents, ai-assistant, claude-code, claude-skills, openclaw

## Evidence checked

- GitHub metadata via `gh repo view nanocoai/nanoclaw` on 2026-05-30.
- README from [upstream README](https://github.com/nanocoai/nanoclaw/blob/HEAD/README.md).
- License, package/Python manifest, requirements, Docker/compose files, and top-level contents where present under temporary upstream inspection material.

## Strengths

- Clear threat model: smaller understandable codebase, Docker/container isolation, per-agent workspace, channel-to-agent wiring, and one-writer SQLite queues.
- MIT, active releases, Node/TypeScript, tests, docs, scheduled tasks, and broad messaging-channel roadmap.
- Credential security pattern via OneCLI Agent Vault and per-agent policies is directly relevant to safe autonomous agents.

## Risks / caveats

- Still a full alternate runtime with messaging adapters, memory, scheduled tasks, and agent containers — high overlap with Hermes.
- Installer/onboarding uses real channels and credentials; sandbox only with throwaway identities/tokens.
- Claims around safety depend on actual container mounts and vault policy enforcement; inspect before adoption.

## Integration ideas

- Borrow: per-agent containers, explicit mounts, per-channel privacy wiring, inbound/outbound DB queues, one writer per DB, credential broker.
- Could inform a future Hermes isolated-worker lane more than a daily runtime migration.

## Alternatives / related repos

- [openclaw/openclaw](openclaw--openclaw.md)
- [nanocoai/nanoclaw](nanocoai--nanoclaw.md)
- [abhi1693/openclaw-mission-control](abhi1693--openclaw-mission-control.md)
- [aiming-lab/MetaClaw](aiming-lab--MetaClaw.md)
- [HKUDS/ClawWork](HKUDS--ClawWork.md)
- [code-yeongyu/oh-my-openagent](code-yeongyu--oh-my-openagent.md)
- [Agent Evaluation and Training Comparison](../comparisons/agent-eval-training.md)
- [Agent Work Orchestration Comparison](../comparisons/agent-work-orchestration.md)

## Review candidates and context

- Create/preserve isolation pattern notes for Hermes gateway/Kanban/autonomous-worker design.
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
