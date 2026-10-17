---
title: decolua/9router
type: repo-intel
aliases: [9router, GitHub repo: decolua/9router]
source: https://github.com/decolua/9router
category: security-containment-agent-safety
topics: [github-repo, llm-router, ai-gateway, oauth-risk, proxy, token-saver]
status: deep-analyzed
usefulness_score: 46
recommendation: reference-only
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# decolua/9router

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `46/100` — useful router/token-saver ideas, but risky as infrastructure due to OAuth aggregation, free-provider routing, MITM/proxy behavior, and dashboard defaults.
- **Recommendation:** `reference-only`; if tested, use disposable accounts/API keys only.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Audit credential storage, request logging, dashboard binding/auth, and provider ToS risks before any sandbox.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 13/25 | Router/gateway patterns are relevant, but compliance risk is high. |
| Leverage | 14/25 | Free/fallback routing could save cost, but at unacceptable risk. |
| Reuse readiness | 8/20 | Large Next.js/Node app with many credentials/providers. |
| Maturity/trust | 7/15 | Active and popular; risky defaults and ToS concerns. |
| Differentiation | 4/15 | Router ideas exist elsewhere without this risk profile. |

## Verdict

9router is not a safe default for a Hermes-centered agent stack. The useful ideas are model fallback, quota tracking, token-result compression, and OpenAI-compatible gateway design. The risky parts are the core pitch: “unlimited free” provider routing, OAuth token concentration, MITM/proxy tooling, request logging, and dashboard defaults.

## Reference-stack relevance

- Good negative example for router/proxy trust boundaries.
- Some token-saver/fallback concepts may inform Hermes routing.
- Highlights why model routing must be boring, auditable, and credential-safe.

## What it is

A local AI gateway/router for Claude Code, Codex, Cursor, Cline, Copilot, OpenClaw, and other tools, with OpenAI-compatible endpoint, provider fallback, free/subscription provider routing, quota tracking, and dashboard.

## Evidence checked

- GitHub metadata on 2026-06-03: ~16k stars, pushed 2026-05-31.
- README, `package.json`, license/root files under a disposable source-inspection workspace.
- Repomix pack: a temporary Repomix evidence pack — 837 files / ~588k tokens; 1 suspicious file excluded; read selectively.
- Targeted evidence: OAuth services for Claude/Codex/Cursor/GitHub/Kiro, local DB repos, dashboard auth/session, request logs, MITM/proxy tooling, RTK filters/tests, default password warning.

## Strengths

- Broad provider/client compatibility.
- Practical router features: fallback, quota tracking, API key generation, token-result compression.
- Local dashboard and OpenAI-compatible endpoint are useful design references.

## Risks / caveats

- Free-provider/subscription maximization may violate provider ToS and risk account bans.
- Stores/manages OAuth tokens, refresh tokens, API keys, provider accounts, proxy pools, and request logs.
- MITM/proxy behavior is dangerous if misconfigured or exposed.
- Default password/binding hardening must be verified.

## Integration ideas

- Extract only fallback/quota/token-compression ideas.
- Do not route real Hermes traffic or real OAuth accounts through it.
- Treat as a cautionary case for router governance.

## Alternatives / related repos

- [BlockRunAI/ClawRouter](BlockRunAI--ClawRouter.md)
- OpenRouter
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)

## Review candidates and context

- Non-binding candidate: document router/proxy credential safety rules using 9router as a negative example.
