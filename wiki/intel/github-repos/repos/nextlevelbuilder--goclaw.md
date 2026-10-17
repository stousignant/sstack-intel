---
title: nextlevelbuilder/goclaw
type: repo-intel
source: https://github.com/nextlevelbuilder/goclaw
category: openclaw-gateway-runtime
status: deep-analyzed
usefulness_score: 70
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: CC-BY-NC-4.0
---

# nextlevelbuilder/goclaw

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `70/100` — Ambitious Go OpenClaw rebuild with multi-tenancy, providers, channels, Docker, sandbox and Tailscale compose files; strong architecture source but bad direct dependency.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-06-03:** `reference-only`.
- Review candidate: Mine multi-tenant isolation/channel/security patterns only; avoid direct adoption because of non-commercial license and runtime overlap.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 17/25 | Fit with Hermes/SStack/GBrain workflows and current runtime boundaries. |
| Leverage | 16/25 | Potential to reduce operator effort or improve agent throughput. |
| Reuse readiness | 13/20 | Install/docs/examples and integration cost. |
| Maturity/trust | 9/15 | Maintenance, tests, license, security, and bus-factor signals. |
| Differentiation | 15/15 | Unique pattern value versus Hermes/Codex/OpenClaw alternatives. |

## Verdict

Ambitious Go OpenClaw rebuild with multi-tenancy, providers, channels, Docker, sandbox and Tailscale compose files; strong architecture source but bad direct dependency. The default is **do not replace Hermes**. Keep Hermes/GBrain/second-brain as the reference architecture, and only sandbox narrow pieces that improve coding-agent execution, browser automation, context delivery, or long-running task supervision.

## Reference-stack relevance

- This batch is directly adjacent to reference-stack questions about long-running tasks, Claude/OpenClaw/OpenCode-style workers, browser/tool control, and shared agent harnesses.
- Go module, Docker compose variants, Postgres/Redis/sandbox/Tailscale support, docs, Makefile, multiple channel/provider claims.
- The reusable payload is mostly operational semantics: setup/rollback, watchdogs, provider/runtime boundaries, context packaging, browser consent gates, and proof-of-work.

## What it is

goclaw is described by GitHub/README as: GoClaw - GoClaw is OpenClaw rebuilt in Go — with multi-tenant isolation, 5-layer security, and native concurrency. Deploy AI agent teams at scale without compromising on safety.. It had `3219` stars, `891` forks, was last pushed `2026-06-03T14:37:01Z`, and exposed topics: agent-orchestration, ai-agent, ai-gateway, anthropic, chatbot, discord-bot, golang, llm.

## Evidence checked

- GitHub metadata via `gh repo view nextlevelbuilder/goclaw`.
- [Upstream README](https://github.com/nextlevelbuilder/goclaw/blob/main/README.md) captured when available.
- [Upstream root listing](https://github.com/nextlevelbuilder/goclaw) inspected at review time.
- License/package/security files when present from the same upstream repository.
- Root files sampled: .dockerignore, .env.example, .gitattributes, .github, .gitignore, .railwayignore, .repomixignore, AGENTS.md, CHANGELOG.md, CLAUDE.md, CONTRIBUTING.md, Dockerfile, Dockerfile.sandbox, LICENSE, Makefile, README.md.

## Strengths

- Go module, Docker compose variants, Postgres/Redis/sandbox/Tailscale support, docs, Makefile, multiple channel/provider claims.
- Recent repository activity signal: last pushed `2026-06-03T14:37:01Z`.
- License evidence checked from repository files or package metadata: `CC-BY-NC-4.0`.

## Risks / caveats

- CC-BY-NC license, broad gateway/runtime surface, auth/channel secrets, and likely duplication of Hermes provider/tool orchestration.
- Treat README claims as claims until a bounded smoke test proves install/runtime behavior.
- Any tool that touches logged-in browsers, shells, provider credentials, worktrees, contacts, or agent memory needs disposable-project boundaries first.

## Integration ideas

- Use as a comparison/reference against [NousResearch/hermes-agent](NousResearch--hermes-agent.md), [openclaw/openclaw](openclaw--openclaw.md), and the SStack shared-skill/harness layer.
- Extract only small patterns that strengthen Hermes long-running task control: explicit owner, claim/lease, heartbeat, branch/workspace binding, rollback, proof bundle, and keep/revert decision.
- If sandboxed, use a disposable scratch workspace or repo/profile and require clear success criteria before changing an established workflow.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [OpenClaw / Coding Harnesses Comparison](../comparisons/openclaw-coding-harnesses.md)

## Review guidance

- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
