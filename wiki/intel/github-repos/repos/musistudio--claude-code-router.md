---
title: "musistudio/claude-code-router"
type: repo-intel
source: https://github.com/musistudio/claude-code-router
category: coding-tools
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# musistudio/claude-code-router

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision
- Usefulness score: `[('Stack fit', 19, 25, 'Useful provider-router reference, but duplicate with Hermes config.'), ('Leverage', 20, 25, 'Could reduce Claude Code provider friction.'), ('Reuse readiness', 18, 20, 'Simple npm install and docs.'), ('Maturity/trust', 12, 15, 'Popular and maintained enough; release channel unclear.'), ('Differentiation', 11, 15, 'Good routing grammar; not unique outside Claude Code.')]/100` — Claude Code Router is a strong provider-routing reference for people living inside Claude Code.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- Review candidate: Do not install globally now; distill its provider-routing/config/auth/logging ideas into Hermes model/provider docs and only test if Claude Code provider-routing becomes a real bottleneck.

## Scorecard
| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 19/25 | Useful provider-router reference, but duplicate with Hermes config. |
| Leverage | 20/25 | Could reduce Claude Code provider friction. |
| Reuse readiness | 18/20 | Simple npm install and docs. |
| Maturity/trust | 12/15 | Popular and maintained enough; release channel unclear. |
| Differentiation | 11/15 | Good routing grammar; not unique outside Claude Code. |

## Verdict

Claude Code Router is a strong provider-routing reference for people living inside Claude Code. For the reference stack, Hermes already owns provider/model configuration, so the reusable value is the routing grammar, auth defaults, logging split, UI mode, presets, and environment-variable interpolation — not another always-on local server.

## Workload fit
- The reference lens covers multi-provider local AI; provider routing and preset export/import are recurring pain points.
- The README’s default security rule — force localhost when no API key is set — is a good guardrail pattern.
- Could help a Claude Code subprocess use non-Anthropic providers while still benefiting from Claude Code updates.

## What it is

A TypeScript monorepo/npm CLI (`ccr`) that proxies/routes Claude Code model calls across providers such as OpenRouter, DeepSeek, Ollama, Gemini, Volcengine, and SiliconFlow, with config, UI mode, presets, and logs.

## Evidence checked
- GitHub metadata via `gh repo view` on 2026-05-30: stars `34546`, forks `2819`, primary language `TypeScript`, archived `False`, fork `False`.
- Maintenance signal: pushed `2026-03-04T05:48:17Z`, updated `2026-05-30T21:43:07Z`, latest release `none detected` ``.
- License: `MIT` from GitHub/license file.
- README: `https://raw.githubusercontent.com/musistudio/claude-code-router/main/README.md`.
- Top-level manifests/docs inspected locally under temporary upstream inspection material: README, package/pyproject when present, license, security file when present, top-level contents.
- Repository topics: none listed.

## Strengths
- High adoption signal: ~34.5k stars / 2.8k forks; pushed 2026-03-04.
- MIT license and npm package `@musistudio/claude-code-router` with `ccr` binary.
- README documents auth via APIKEY, HOST behavior, routing rules, env-var interpolation, logs, UI mode, and presets.
- Provider-routing surface is concrete and understandable.

## Risks / caveats
- Mostly solves a Claude Code-specific routing problem, while Hermes already has model/provider abstractions.
- Local proxy handling API keys/model requests is sensitive; logs and config need review before real use.
- No latest GitHub release detected; npm/version may be the real release channel.

## Integration ideas
- Add “localhost unless authenticated” as an explicit Hermes/plugin gateway design rule.
- Use presets/export-import concept for Hermes profile/model routing if config UX becomes painful.
- If Claude Code is delegated often, test CCR in a disposable profile with a non-sensitive provider key.

## Alternatives / related repos
- [Claude Code Ecosystem Comparison](../comparisons/claude-code-ecosystem.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [oraios/serena](oraios--serena.md)
- [microsoft/skills](microsoft--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)

## Review candidates and context
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.

## Score breakdown

| Dimension | Score | Max | Note |
|---|---:|---:|---|
| Stack fit | 19 | 25 | Useful provider-router reference, but duplicate with Hermes config. |
| Leverage | 20 | 25 | Could reduce Claude Code provider friction. |
| Reuse readiness | 18 | 20 | Simple npm install and docs. |
| Maturity/trust | 12 | 15 | Popular and maintained enough; release channel unclear. |
| Differentiation | 11 | 15 | Good routing grammar; not unique outside Claude Code. |
