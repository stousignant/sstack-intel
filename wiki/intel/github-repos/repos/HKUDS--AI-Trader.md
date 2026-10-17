---
title: HKUDS/AI-Trader
type: repo-intel
source: https://github.com/HKUDS/AI-Trader
category: trading-agent
status: deep-analyzed
usefulness_score: 62
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: NOASSERTION
---

# HKUDS/AI-Trader

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `62/100` — High-signal automated trading-agent demo, but financial automation is outside the current core stack and carries obvious capital/credential risk.
- Recommendation: `watch`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Watch architecture only; never connect brokerage/API keys or trade real funds without a separate risk policy and paper-trading eval.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 18/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 17/25 | Potential to save time or increase optionality. |
| Reuse readiness | 14/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 10/15 | Maintenance, tests, license, security, and governance. |
| Differentiation | 3/15 | Unique value versus current stack and existing notes. |

## Verdict

High-signal automated trading-agent demo, but financial automation is outside the current core stack and carries obvious capital/credential risk. The default is to keep this repo as a **bounded source of examples/patterns**, not a new canonical subsystem, unless the next action explicitly calls for a disposable sandbox.

## Reference-stack relevance

- This batch covers practical AI app/product building, learning catalogs, voice/media, backend substrate, and trading-agent examples.
- Active agent-native trading project with service/skills/research folders and UI dependency evidence.
- Useful signals should be routed into specific SStack/Hermes experiments rather than expanding the star queue endlessly.

## What it is

GitHub description: "AI-Trader: 100% Fully-Automated Agent-Native Trading"  .

Metadata captured: `19121` stars, `2915` forks, last pushed `2026-06-03T02:58:32Z`, archived `False`, fork `False`, topics: none captured.

## Evidence checked

- GitHub metadata via `gh repo view HKUDS/AI-Trader`.
- README/root listing under [upstream repository inspection](https://github.com/HKUDS/AI-Trader).
- License/package/security/docker files when present in the evidence directory.
- Root files sampled: .env.example, .gitignore, README.md, README_ZH.md, assets, docs, impeccable.context.tmp, package-lock.json, package.json, research, service, skills, tsconfig.json.

## Strengths

- Active agent-native trading project with service/skills/research folders and UI dependency evidence.
- Recent activity and root-structure evidence were checked before scoring.

## Risks / caveats

- Financial automation, .env/API-key surface, README license claim not backed by fetched LICENSE file, and likely benchmark/hype risk.
- Treat README claims and star counts as weak evidence unless matched by docs, tests, package manifests, or a local sandbox.
- Do not connect secrets, financial accounts, user data, voice data, or production backend resources during repo-intelligence evaluation.

## Integration ideas

- Use catalogs/courses as discovery and learning aids only when tied to a concrete project or question.
- Use app/example repos to seed small prototypes, not as global Hermes behavior.
- Backend and CLI-generation tools require disposable sandbox evaluation before adoption into an active runtime.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [AI App / Business / Learning Catalogs Comparison](../comparisons/ai-app-business-catalogs.md)

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
