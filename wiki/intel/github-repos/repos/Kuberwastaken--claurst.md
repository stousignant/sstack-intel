---
title: Kuberwastaken/claurst
type: repo-intel
source: https://github.com/Kuberwastaken/claurst
category: coding-agent-runtime
status: deep-analyzed
usefulness_score: 76
recommendation: watch
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: GPL-3.0
---

# Kuberwastaken/claurst

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `76/100` — Clean-room Rust Claude-Code-style agent is technically interesting, but GPL and early version make it a watch/reference candidate.
- Recommendation: `watch`.
- **Usage observed 2026-06-03:** `reference-only`.
- Review candidate: Watch Rust multi-provider architecture; only sandbox if OpenCode/Codex/Hermes comparison exposes a terminal-agent gap.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 18/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 18/25 | Potential to reduce operator effort or improve agent throughput on long-running tasks. |
| Reuse readiness | 14/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 10/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 16/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

Clean-room Rust Claude-Code-style agent is technically interesting, but GPL and early version make it a watch/reference candidate. The default is **do not replace Hermes**. Keep Hermes/GBrain/second-brain as the active stack, and only sandbox narrow pieces that improve coding-agent execution, browser automation, context delivery, or long-running task supervision.

## Reference-stack relevance

- This batch is relevant to workloads involving long-running tasks, Claude/OpenClaw/OpenCode-style workers, browser/tool control, and shared agent harnesses.
- Rust TUI/runtime, multi-provider positioning, Claude/Codex/Gemini topics, install scripts, docs/spec/session folders.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

claurst is described by GitHub/README as: Agentic Coding for Builders who Ship. It had `9753` stars, `7790` forks, was last pushed `2026-05-29T15:00:18Z`, and exposed topics: claude, claude-code, cli, codex, gemini, rust, tui, claurst.

## Evidence checked

- GitHub metadata via `gh repo view Kuberwastaken/claurst`.
- README captured at [upstream README](https://github.com/Kuberwastaken/claurst) when available.
- Captured upstream root listing inspected.
- License/package/security files when present under the same evidence directory.
- Root files sampled: .devcontainer, .github, .gitignore, .vscode, AGENTS.md, CNAME, LICENSE.md, README.md, docs, index.html, install.ps1, install.sh, npm, public, scripts, session.

## Strengths

- Rust TUI/runtime, multi-provider positioning, Claude/Codex/Gemini topics, install scripts, docs/spec/session folders.
- Recent repository activity signal: last pushed `2026-05-29T15:00:18Z`.
- License evidence checked from repository files or package metadata: `GPL-3.0`.

## Risks / caveats

- GPL-3.0, early version, massive fork/star signals that need skepticism, and duplicates existing coding-agent lanes.
- Treat README claims as claims until a bounded smoke test proves install/runtime behavior.
- Any tool that touches logged-in browsers, shells, provider credentials, worktrees, contacts, or agent memory needs disposable-project boundaries first.

## Integration ideas

- Use as a comparison/reference against [NousResearch/hermes-agent](NousResearch--hermes-agent.md), [openclaw/openclaw](openclaw--openclaw.md), and the SStack shared-skill/harness layer.
- Extract only small patterns that strengthen Hermes long-running task control: explicit owner, claim/lease, heartbeat, branch/workspace binding, rollback, proof bundle, and keep/revert decision.
- If sandboxed, use a disposable scratch directory or repo/profile and require clear success criteria before changing an established workflow.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenClaw / Coding Harnesses Comparison](../comparisons/openclaw-coding-harnesses.md)

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
