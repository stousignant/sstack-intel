---
title: code-yeongyu/oh-my-openagent
type: repo-intel
aliases:
  - oh-my-openagent
  - GitHub repo: code-yeongyu/oh-my-openagent
source: https://github.com/code-yeongyu/oh-my-openagent
category: agent-harness
topics: [github-repo, repo-intelligence, openclaw, agent-runtime]
status: deep-analyzed
usefulness_score: 76
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: SUL-1.0
---

# code-yeongyu/oh-my-openagent

> Opinionated reference-stack evaluation, reviewed 2026-05-30. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `76/100` — Feature-rich multi-harness agent OS with Team Mode, lifecycle hooks, MCPs, LSP/AST tools, Codex/OpenCode plugins, and strong tests; SUL-1.0 and command-framework sprawl make it sandbox/reference only.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Compare OMO team/lifecycle semantics against OMC/oh-my-claudecode if a disposable multi-agent bakeoff happens; do not import globally.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 19/25 | Relevant to Hermes/GBrain/second-brain agent runtime, eval, operations, or isolation design without replacing the reference primary runtime. |
| Leverage | 22/25 | Could improve autonomous-agent safety, eval quality, work orchestration, or self-improvement loops. |
| Reuse readiness | 12/20 | README/manifests provide install paths; most should remain sandbox/pattern-only because they touch runtimes, credentials, or training loops. |
| Maturity/trust | 11/15 | Live metadata: 60324 stars, 4896 forks, pushed 2026-05-31T00:52:07Z, license SUL-1.0. |
| Differentiation | 12/15 | Differentiates through runtime isolation, economic eval, self-improvement scheduler, or team/orchestration semantics. |

## Verdict

Feature-rich multi-harness agent OS with Team Mode, lifecycle hooks, MCPs, LSP/AST tools, Codex/OpenCode plugins, and strong tests; SUL-1.0 and command-framework sprawl make it sandbox/reference only. The default is still **Hermes as reference primary runtime**. The useful payload is not migrating into the OpenClaw ecosystem; it is extracting runtime-isolation, eval, governance, economic-accountability, and self-improvement patterns that can strengthen Hermes/GBrain/second-brain workflows.

## Reference-stack relevance

- These repos are adjacent to the same problem Hermes is solving: personal agents that can work across channels, tools, memory, and tasks without melting down.
- The leverage is in design patterns: container boundaries, task/eval economics, approval/gateway control, and safe self-improvement windows.
- Broad OpenClaw/NanoClaw/OMO runtimes overlap heavily with Hermes; adoption only makes sense for tiny disposable bakeoffs or if they reveal a clear missing primitive.

## What it is

Oh My OpenAgent is a TypeScript/Bun multi-harness agent plugin system for OpenCode/Codex-style environments with Team Mode, ultrawork, lifecycle hooks, MCP tools, LSP/AST tools, and agent orchestration.

## Live metadata checked

- Source: <https://github.com/code-yeongyu/oh-my-openagent>
- Description: omo; the best agent harness - previously oh-my-opencode
- Stars / forks: 60324 / 4896
- Primary language: TypeScript
- License: SUL-1.0
- Latest release: v4.5.12 / 2026-05-30T19:40:28Z
- Last pushed: 2026-05-31T00:52:07Z
- Topics: claude-code, opencode, ai, amp, anthropic, claude, claude-skills, cursor, gemini, ide, openai, orchestration, tui, typescript, ai-agents, chatgpt

## Evidence checked

- GitHub metadata via `gh repo view code-yeongyu/oh-my-openagent` on 2026-05-30.
- README from [upstream README](https://github.com/code-yeongyu/oh-my-openagent).
- License, package/Python manifest, requirements, Docker/compose files, and top-level contents where present under a disposable source-inspection workspace.

## Strengths

- Very active release, large test surface in package scripts, multi-platform packaging, Team Mode, hooks, AST/LSP tools, and model/provider configuration.
- Strong “discipline agent” and work-continuation semantics may be useful for autonomous coding handoffs.
- DeepWiki badge and active roadmap indicate a rich ecosystem, even if noisy.

## Risks / caveats

- SUL-1.0 restricts commercial/hosted-style reuse; not a clean remix source.
- Recommends letting an LLM agent install complex auth/model setup — exactly the kind of thing to sandbox, not run on canonical profiles.
- Overlap with Hermes, Codex, Claude Code ecosystem, OMC, and OpenCode is huge; high sprawl cost.

## Integration ideas

- Distill lifecycle hooks, work-continuation, model capability guardrails, and AST/LSP MCP packaging.
- Useful comparison item for “team mode” semantics, but OMC remains the cleaner Claude Code lane reference.

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

- Reference in future disposable multi-agent harness bakeoff only.
- Non-binding guidance; executable state belongs to the established issue tracker.
