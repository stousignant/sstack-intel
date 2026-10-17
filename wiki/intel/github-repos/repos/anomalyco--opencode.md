---
title: anomalyco/opencode
type: repo-intel
source: https://github.com/anomalyco/opencode
category: coding-agent-runtime
status: deep-analyzed
usefulness_score: 86
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# anomalyco/opencode

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `86/100` — Mature MIT coding-agent runtime with very high ecosystem momentum; worth sandboxing as a secondary coding lane, not replacing Hermes.
- Recommendation: `adopt-now`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Run a bounded OpenCode CLI bakeoff against Hermes/Codex on one disposable repo, with proof-bundle requirements and no production credentials.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 22/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 22/25 | Potential to improve coding throughput and reduce coordination overhead. |
| Reuse readiness | 17/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 13/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 12/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

Mature MIT coding-agent runtime with very high ecosystem momentum; worth sandboxing as a secondary coding lane, not adopting as a replacement by default. Where Hermes/GBrain/Markdown already cover agent execution, retrieval, and canonical knowledge, test only a defined gap such as coding execution, browser automation, context delivery, or long-running task supervision.

## Workload fit

- Relevant workloads include long-running tasks, Claude/OpenClaw/OpenCode-style workers, browser/tool control, and shared agent harnesses.
- Large active codebase, MIT license, npm package, desktop/web/console surfaces, security policy, multilingual docs, and provider-agnostic coding-agent positioning.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

opencode is described by GitHub/README as: The open source coding agent.. It had `169287` stars, `20239` forks, was last pushed `2026-06-03T14:36:17Z`, and exposed topics: none captured.

## Evidence checked

- GitHub metadata via `gh repo view anomalyco/opencode`.
- README captured at [upstream README](https://github.com/anomalyco/opencode) when available.
- Root listing captured at the captured upstream root listing.
- License/package/security files when present under the same evidence directory.
- Root files sampled: .dockerignore, .editorconfig, .gitattributes, .github, .gitignore, .gitleaksignore, .husky, .opencode, .oxlintrc.json, .prettierignore, .vscode, .zed, AGENTS.md, CONTRIBUTING.md, LICENSE, README.ar.md.

## Strengths

- Large active codebase, MIT license, npm package, desktop/web/console surfaces, security policy, multilingual docs, and provider-agnostic coding-agent positioning.
- Recent repository activity signal: last pushed `2026-06-03T14:36:17Z`.
- License evidence checked from repository files or package metadata: `MIT`.

## Risks / caveats

- Huge popularity can hide hype; adding another active runtime increases workflow sprawl unless it beats Hermes/Codex on a defined task.
- Treat README claims as claims until a bounded smoke test proves install/runtime behavior.
- Any tool that touches logged-in browsers, shells, provider credentials, worktrees, contacts, or agent memory needs disposable-project boundaries first.

## Integration ideas

- Use as a comparison/reference against [NousResearch/hermes-agent](NousResearch--hermes-agent.md), [openclaw/openclaw](openclaw--openclaw.md), and the SStack shared-skill/harness layer.
- Extract only small patterns that strengthen Hermes long-running task control: explicit owner, claim/lease, heartbeat, branch/workspace binding, rollback, proof bundle, and keep/revert decision.
- If sandboxed, use a disposable scratch workspace or repo/profile and define success criteria before changing any default workflow.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenClaw / Coding Harnesses Comparison](../comparisons/openclaw-coding-harnesses.md)

## Review candidates and context

- Candidates above remain non-binding; execution state belongs to the established issue tracker.
