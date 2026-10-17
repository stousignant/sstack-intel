---
title: jackwener/OpenCLI
type: repo-intel
source: https://github.com/jackwener/OpenCLI
category: browser-automation-cli
status: deep-analyzed
usefulness_score: 84
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: Apache-2.0
---

# jackwener/OpenCLI

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- Usefulness score: `84/100` — Strong tactical candidate for deterministic web/app CLI adapters and browser-use through existing sessions, but logged-in browser control needs consent gates.
- Recommendation: `adopt-now`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Sandbox OpenCLI on a harmless public/logged-out site and compare against Hermes browser tools + Playwright MCP before any logged-in-browser use.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 22/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 22/25 | Potential to save operator time or improve agent leverage. |
| Reuse readiness | 17/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 13/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 10/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

Strong tactical candidate for deterministic web/app CLI adapters and browser-use through existing sessions, but logged-in browser control needs consent gates. The default is **do not replace Hermes**. Keep Hermes/GBrain/second-brain as the active stack, and only sandbox narrow pieces that improve coding-agent execution, browser automation, context delivery, or long-running task supervision.

## Reference-stack relevance

- This batch is directly adjacent to the reference stack's questions about long-running tasks, Claude/OpenClaw/OpenCode-style workers, browser/tool control, and shared agent harnesses.
- Apache-licensed Node CLI, adapters for many sites, browser skill, tests/docs/privacy file, and a deterministic interface for AI agents.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

OpenCLI is described by GitHub/README as: Make Any Website into CLI & Use your logged-in browser by AI agent. . It had `23405` stars, `2351` forks, was last pushed `2026-06-02T17:31:08Z`, and exposed topics: ai-agent, ai-agents, ai-tools, cli.

## Evidence checked

- GitHub metadata via `gh repo view jackwener/OpenCLI`.
- README inspected from [upstream README](https://github.com/jackwener/OpenCLI/blob/HEAD/README.md) when available.
- Root listing captured as an upstream tree snapshot.
- License/package/security files when present under the same evidence directory.
- Root files sampled: .github, .gitignore, CHANGELOG.md, CONTRIBUTING.md, LICENSE, PRIVACY.md, README.md, README.zh-CN.md, TESTING.md, autoresearch, bun.lock, cases, cli-manifest.json, clis, designs, docs.

## Strengths

- Apache-licensed Node CLI, adapters for many sites, browser skill, tests/docs/privacy file, and a deterministic interface for AI agents.
- Recent repository activity signal: last pushed `2026-06-02T17:31:08Z`.
- License evidence checked from repository files or package metadata: `Apache-2.0`.

## Risks / caveats

- Logged-in Chrome automation is high-privilege; built-in adapters for social/content sites need explicit target consent and no ambient use.
- Treat README claims as claims until a bounded smoke test proves install/runtime behavior.
- Any tool that touches logged-in browsers, shells, provider credentials, worktrees, contacts, or agent memory needs disposable-project boundaries first.

## Integration ideas

- Use as a comparison/reference against [NousResearch/hermes-agent](NousResearch--hermes-agent.md), [openclaw/openclaw](openclaw--openclaw.md), and the SStack shared-skill/harness layer.
- Extract only small patterns that strengthen Hermes long-running task control: explicit owner, claim/lease, heartbeat, branch/workspace binding, rollback, proof bundle, and keep/revert decision.
- If sandboxed, use a disposable scratch directory or a disposable repo/profile and require clear success criteria before changing the reference stack's default workflow.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenClaw / Coding Harnesses Comparison](../comparisons/openclaw-coding-harnesses.md)

## Review candidates and context

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
