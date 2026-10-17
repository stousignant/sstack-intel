---
title: BlockRunAI/ClawRouter
type: repo-intel
aliases: [ClawRouter, GitHub repo: BlockRunAI/ClawRouter]
source: https://github.com/BlockRunAI/ClawRouter
category: security-containment-agent-safety
topics: [github-repo, llm-router, openclaw, payment-risk, proxy, hermes]
status: deep-analyzed
usefulness_score: 67
recommendation: watch
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# BlockRunAI/ClawRouter

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `67/100` — Hermes-relevant router/proxy ideas, but payment and upstream proxy trust boundaries make it sandbox-only.
- **Recommendation:** `watch`; evaluate only with an unfunded wallet and captured network traffic.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Run a sandbox audit with no funded wallet to verify key handling and upstream prompt payloads.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 19/25 | Explicit Hermes/OpenClaw router integration. |
| Leverage | 17/25 | Could improve model routing/cost experiments. |
| Reuse readiness | 12/20 | Local proxy exists, but payments/proxy trust complicate use. |
| Maturity/trust | 10/15 | Substantial implementation; financial/security surface is high. |
| Differentiation | 9/15 | x402/payment routing is distinct but risky. |

## Verdict

ClawRouter is interesting because it explicitly mentions Hermes and offers a local OpenAI-compatible router/proxy with model fallback, cost-aware profiles, and x402 USDC payments. That same payment/proxy surface is why it should not touch production Hermes traffic or funded wallets without audit.

## Workload fit

- Could be a cheap routing experiment for Hermes-like traffic.
- Shows wallet-signature/payment-aware router architecture.
- Useful for thinking about model-routing policy and fallback chains.

## What it is

An agent-native LLM router/proxy for OpenClaw/Hermes-style tools, with many models, local routing, fallback, OpenAI-compatible endpoint, and Base/Solana USDC x402 payments.

## Evidence checked

- GitHub metadata on 2026-06-03: ~6.5k stars, pushed 2026-06-01.
- README, `package.json`, license/root files under [upstream repository inspection](https://github.com/BlockRunAI/ClawRouter).
- Repomix pack: a temporary Repomix inspection pack — 194 files / ~292k tokens; no suspicious files detected.
- Targeted evidence: `openclaw.plugin.json`, `openclaw.security.json`, local signing docs, proxy safeguards, request deduplication, balance checks, fallback/free-model logic, request/model limits.

## Strengths

- Explicit Hermes/OpenClaw relevance.
- MIT license and concrete TypeScript implementation.
- Local proxy/fallback/cost logic could inform Hermes routing.

## Risks / caveats

- Payment risk around wallet keys, mnemonic handling, USDC, and x402 signing.
- Proxy trust risk: prompts/tool payloads may transit BlockRun/upstreams.
- Install docs include `curl | bash`; avoid for production.
- Feature scope includes image/video/phone/voice/crypto/stock tools, expanding attack/cost surface.

## Integration ideas

- Use only with throwaway/unfunded wallet in a network-observed sandbox.
- Extract routing/fallback policy ideas into Hermes without payment dependencies.
- Compare with current Hermes model/provider configuration before testing.

## Alternatives / related repos

- [decolua/9router](decolua--9router.md)
- OpenRouter
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)

## Review candidates and context

- Candidate: sandbox-audit ClawRouter with unfunded wallet and captured network traffic before any real use.
