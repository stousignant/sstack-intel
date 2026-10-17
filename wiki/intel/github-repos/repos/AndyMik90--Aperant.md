---
title: AndyMik90/Aperant
type: repo-intel
source: https://github.com/AndyMik90/Aperant
category: coding-agent-control-plane
status: deep-analyzed
usefulness_score: 69
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: AGPL-3.0
---

# AndyMik90/Aperant

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `69/100` — High-signal autonomous Claude Code cockpit with kanban/multi-session patterns, but AGPL and broad desktop shell control make it pattern-only; any executable trial needs a disposable sandbox and license/security review.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-06-03:** `reference-only`.
- Review candidate: Keep as a control-plane/security reference; do not adopt into work or personal repos without a disposable sandbox and license/security review.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 17/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 16/25 | Potential to improve throughput in multi-session coding workflows. |
| Reuse readiness | 13/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 9/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 14/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

High-signal autonomous Claude Code cockpit with kanban/multi-session patterns, but AGPL and broad desktop shell control make it a pattern source rather than a default runtime. Keep any trial narrow and compare coding execution, browser control, context delivery, and long-running task supervision against the existing agent lane.

## Workload fit

- Relevant workloads include long-running coding tasks, multi-session coordination, browser/tool control, and shared agent harnesses.
- Multi-session coding board, release discipline, memory/proof artifacts, and active docs around autonomous coding.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

Aperant is described by GitHub/README as: Autonomous multi-session AI coding. It had `14318` stars, `1931` forks, was last pushed `2026-03-23T19:47:59Z`, and exposed topics: none captured.

## Evidence checked

- GitHub metadata via `gh repo view AndyMik90/Aperant`.
- README captured at [upstream README](https://github.com/AndyMik90/Aperant) when available.
- Captured upstream root listing inspected.
- License/package/security files when present under the same evidence directory.
- Root files sampled: .claude, .coderabbit.yaml, .design-system, .github, .gitignore, .husky, .pre-commit-config.yaml, .secretsignore.example, CHANGELOG.md, CLA.md, CLAUDE.md, CODEX_RATE_LIMITS_RESEARCH.md, CONTRIBUTING.md, LICENSE, Memory.md, README.md.

## Strengths

- Multi-session coding board, release discipline, memory/proof artifacts, and active docs around autonomous coding.
- Recent repository activity signal: last pushed `2026-03-23T19:47:59Z`.
- License evidence checked from repository files or package metadata: `AGPL-3.0`.

## Risks / caveats

- AGPL network-copyleft, desktop/shell authority, provider credentials, large app surface, and a prior review judged it unsuitable as a work baseline; this is a review conclusion, not a universal license verdict.
- Treat README claims as claims until a bounded smoke test proves install/runtime behavior.
- Any tool that touches logged-in browsers, shells, provider credentials, worktrees, contacts, or agent memory needs disposable-project boundaries first.

## Integration ideas

- Use as a comparison/reference against [NousResearch/hermes-agent](NousResearch--hermes-agent.md), [openclaw/openclaw](openclaw--openclaw.md), and the SStack shared-skill/harness layer.
- Extract only small patterns that strengthen Hermes long-running task control: explicit owner, claim/lease, heartbeat, branch/workspace binding, rollback, proof bundle, and keep/revert decision.
- If sandboxed, use a disposable scratch directory or repo/profile and define success criteria before changing any default workflow.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenClaw / Coding Harnesses Comparison](../comparisons/openclaw-coding-harnesses.md)

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
