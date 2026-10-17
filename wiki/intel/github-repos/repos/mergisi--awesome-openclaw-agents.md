---
title: mergisi/awesome-openclaw-agents
type: repo-intel
source: https://github.com/mergisi/awesome-openclaw-agents
category: openclaw-agent-template-catalog
status: deep-analyzed
usefulness_score: 72
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# mergisi/awesome-openclaw-agents

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- Usefulness score: `72/100` — Large OpenClaw agent template catalog; useful for ideation, dangerous as bulk prompt/persona import.
- Recommendation: `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Use as a quarantined discovery list for agent-template ideas; selectively port only concrete task roles with eval criteria.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 18/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 18/25 | Potential to save operator time or improve agent leverage. |
| Reuse readiness | 14/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 10/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 12/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

Large OpenClaw agent template catalog; useful for ideation, dangerous as bulk prompt/persona import. The default is **do not replace Hermes**. Keep Hermes/GBrain/second-brain as the active stack, and only sandbox narrow pieces that improve coding-agent execution, browser automation, context delivery, or long-running task supervision.

## Reference-stack relevance

- This batch is directly adjacent to the reference stack's questions about long-running tasks, Claude/OpenClaw/OpenCode-style workers, browser/tool control, and shared agent harnesses.
- MIT list with agents.json, SOUL.md-style templates, categories, skills, memory-wiki, quickstart, and contribution docs.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

awesome-openclaw-agents is described by GitHub/README as: 162 production-ready AI agent templates for OpenClaw. SOUL.md configs across 19 categories. Submit yours!. It had `3507` stars, `577` forks, was last pushed `2026-05-25T10:21:05Z`, and exposed topics: ai-agents, anthropic, automation, awesome, claude, openclaw, productivity, docker.

## Evidence checked

- GitHub metadata via `gh repo view mergisi/awesome-openclaw-agents`.
- README inspected from [upstream README](https://github.com/mergisi/awesome-openclaw-agents/blob/HEAD/README.md) when available.
- Root listing captured as an upstream tree snapshot.
- License/package/security files when present under the same evidence directory.
- Root files sampled: .github, .gitignore, .nojekyll, CONTRIBUTING.md, LICENSE, README.md, TROUBLESHOOTING.md, USE-CASES.md, agents.json, agents, configs, memory-wiki, quickstart, skills.

## Strengths

- MIT list with agents.json, SOUL.md-style templates, categories, skills, memory-wiki, quickstart, and contribution docs.
- Recent repository activity signal: last pushed `2026-05-25T10:21:05Z`.
- License evidence checked from repository files or package metadata: `MIT`.

## Risks / caveats

- Prompt-supply-chain/persona sprawl; production-ready claims need per-template audit before any reuse.
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
