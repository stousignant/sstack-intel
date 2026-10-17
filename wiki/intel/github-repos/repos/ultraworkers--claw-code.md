---
title: ultraworkers/claw-code
type: repo-intel
source: https://github.com/ultraworkers/claw-code
category: coding-agent-runtime
status: deep-analyzed
usefulness_score: 74
recommendation: watch
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# ultraworkers/claw-code

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `74/100` — Rust/oh-my-codex-derived coding agent with explosive stars and MIT license; potentially useful benchmark, but hype indicators demand caution.
- Recommendation: `watch`.
- **Usage observed 2026-06-03:** `reference-only`.
- Review candidate: Watch for real maturity/parity evidence; compare only after OpenCode/Claurst/Hermes bakeoff criteria exist.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 18/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 18/25 | Potential to reduce operator effort or improve agent throughput. |
| Reuse readiness | 14/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 10/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 14/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

Rust/oh-my-codex-derived coding agent with explosive stars and MIT license; potentially useful benchmark, but hype indicators demand caution. The default is **do not replace Hermes**. Keep Hermes/GBrain/second-brain as the reference architecture, and only sandbox narrow pieces that improve coding-agent execution, browser automation, context delivery, or long-running task supervision.

## Reference-stack relevance

- This batch is directly adjacent to reference-stack questions about long-running tasks, Claude/OpenClaw/OpenCode-style workers, browser/tool control, and shared agent harnesses.
- MIT, SECURITY/PARITY/ROADMAP/USAGE docs, Rust workspace, tests, install script, and explicit parity tracking.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

claw-code is described by GitHub/README as: The repo is finally unlocked. enjoy the party! The fastest repo in history to surpass 100K stars ⭐. Join Discord: https://discord.gg/5TUQKqFWd Built in Rust using oh-my-codex.. It had `193205` stars, `109982` forks, was last pushed `2026-06-03T14:16:56Z`, and exposed topics: none captured.

## Evidence checked

- GitHub metadata via `gh repo view ultraworkers/claw-code`.
- [Upstream README](https://github.com/ultraworkers/claw-code/blob/main/README.md) captured when available.
- [Upstream root listing](https://github.com/ultraworkers/claw-code) inspected at review time.
- License/package/security files when present from the same upstream repository.
- Root files sampled: .claude.json, .claude, .claw.json, .dockerignore, .github, .gitignore, .omx, .port_sessions, CLAUDE.md, CODE_OF_CONDUCT.md, CONTRIBUTING.md, Containerfile, LICENSE, PARITY.md, PHILOSOPHY.md, README.md.

## Strengths

- MIT, SECURITY/PARITY/ROADMAP/USAGE docs, Rust workspace, tests, install script, and explicit parity tracking.
- Recent repository activity signal: last pushed `2026-06-03T14:16:56Z`.
- License evidence checked from repository files or package metadata: `MIT`.

## Risks / caveats

- Extreme star/fork counts and marketing language are anomaly signals; do not treat popularity as trust without runtime audit.
- Treat README claims as claims until a bounded smoke test proves install/runtime behavior.
- Any tool that touches logged-in browsers, shells, provider credentials, worktrees, contacts, or agent memory needs disposable-project boundaries first.

## Integration ideas

- Use as a comparison/reference against [NousResearch/hermes-agent](NousResearch--hermes-agent.md), [openclaw/openclaw](openclaw--openclaw.md), and the SStack shared-skill/harness layer.
- Extract only small patterns that strengthen Hermes long-running task control: explicit owner, claim/lease, heartbeat, branch/workspace binding, rollback, proof bundle, and keep/revert decision.
- If sandboxed, use a disposable scratch workspace or a disposable repo/profile and require clear success criteria before changing an established workflow's defaults.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenClaw / Coding Harnesses Comparison](../comparisons/openclaw-coding-harnesses.md)

## Review guidance

- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
