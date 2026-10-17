---
title: chrysb/alphaclaw
type: repo-intel
source: https://github.com/chrysb/alphaclaw
category: openclaw-harness
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# chrysb/alphaclaw

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `78/100` — Useful OpenClaw setup/watchdog harness; the value in a Hermes-centered environment is reliability/observability patterns, not a new OpenClaw layer.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-06-03:** `reference-only`.
- Review candidate: Distill watchdog/setup/rollback/observability ideas into Hermes long-running-task operations rather than installing AlphaClaw.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 20/25 | Potential to reduce operator effort or improve agent leverage. |
| Reuse readiness | 16/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 11/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 11/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

Useful OpenClaw setup/watchdog harness; in an environment using Hermes as its primary runtime, the value is reliability/observability patterns rather than another OpenClaw layer. The default is **do not replace Hermes**. Where Hermes/GBrain/Markdown already supply the runtime and knowledge layers, sandbox narrow pieces only when they improve coding-agent execution, browser automation, context delivery, or long-running task supervision.

## Reference-stack relevance

- This batch is relevant to workloads involving long-running tasks, Claude/OpenClaw/OpenCode-style workers, browser/tool control, and shared agent harnesses.
- MIT Node package with setup UI, gateway manager, watchdog, Git-backed rollback, tests, and OpenClaw-specific operational hardening.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

alphaclaw is described by GitHub/README as: The ultimate setup harness for OpenClaw. Deploy in minutes. Stay running for months. No CLI required.. It had `1372` stars, `200` forks, was last pushed `2026-06-01T21:07:14Z`, and exposed topics: ai-agent, gateway, nodejs, openclaw, setup-ui, watchdog.

## Evidence checked

- GitHub metadata via `gh repo view chrysb/alphaclaw`.
- README captured at [upstream README](https://github.com/chrysb/alphaclaw) when available.
- Root listing captured at the captured upstream root listing.
- License/package/security files when present under the same evidence directory.
- Root files sampled: .cursor, .github, .gitignore, .npmrc, AGENTS.md, CONTRIBUTING.md, LICENSE, README.md, bin, lib, package-lock.json, package.json, pnpm-lock.yaml, scripts, tailwind.config.cjs, tests.

## Strengths

- MIT Node package with setup UI, gateway manager, watchdog, Git-backed rollback, tests, and OpenClaw-specific operational hardening.
- Recent repository activity signal: last pushed `2026-06-01T21:07:14Z`.
- License evidence checked from repository files or package metadata: `MIT`.

## Risks / caveats

- OpenClaw-specific and lower leverage while Hermes is the reference primary runtime; browser setup surface may pull credentials/config into another tool.
- Treat README claims as claims until a bounded smoke test proves install/runtime behavior.
- Any tool that touches logged-in browsers, shells, provider credentials, worktrees, contacts, or agent memory needs disposable-project boundaries first.

## Integration ideas

- Use as a comparison/reference against [NousResearch/hermes-agent](NousResearch--hermes-agent.md), [openclaw/openclaw](openclaw--openclaw.md), and the SStack shared-skill/harness layer.
- Extract only small patterns that strengthen Hermes long-running task control: explicit owner, claim/lease, heartbeat, branch/workspace binding, rollback, proof bundle, and keep/revert decision.
- If sandboxed, use a disposable scratch workspace or repo/profile and define success criteria before changing an existing default workflow.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenClaw / Coding Harnesses Comparison](../comparisons/openclaw-coding-harnesses.md)

## Review candidates and context

- Candidates above remain non-binding; execution state belongs to the established issue tracker.
