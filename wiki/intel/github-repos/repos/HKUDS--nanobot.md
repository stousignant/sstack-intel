---
title: HKUDS/nanobot
type: repo-intel
source: https://github.com/HKUDS/nanobot
category: personal-agent-framework
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# HKUDS/nanobot

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `82/100` — Strong lightweight personal-agent framework reference with Docker, tests, security policy, bridge/webui/docs, and MIT license; useful patterns without replacing Hermes.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Distill bridge/docs/webui/security patterns into Hermes/SStack only if a concrete gap appears.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 21/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 20/25 | Potential to save time or increase optionality. |
| Reuse readiness | 16/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 13/15 | Maintenance, tests, license, security, and governance. |
| Differentiation | 12/15 | Unique value versus current stack and existing notes. |

## Verdict

Strong lightweight personal-agent framework reference with Docker, tests, security policy, bridge/webui/docs, and MIT license; useful patterns without replacing Hermes. The default is to keep this repo as a **bounded source of examples/patterns**, not a new canonical subsystem, unless the next action explicitly calls for a disposable sandbox.

## Reference-stack relevance

- This batch covers practical AI app/product building, learning catalogs, voice/media, backend substrate, and trading-agent examples.
- MIT Python package, Docker compose, tests, SECURITY.md, web UI, bridge, docs, and broad tool/chat/workflow positioning.
- Useful signals should be routed into specific SStack/Hermes experiments rather than expanding the star queue endlessly.

## What it is

GitHub description: Lightweight, open-source AI agent for your tools, chats, and workflows..

Metadata captured: `43581` stars, `7712` forks, last pushed `2026-06-03T13:11:40Z`, archived `False`, fork `False`, topics: ai, ai-agent, ai-agents, anthropic, chatgpt, claude, claude-code, codex.

## Evidence checked

- GitHub metadata via `gh repo view HKUDS/nanobot`.
- README/root listing under [upstream repository inspection](https://github.com/HKUDS/nanobot).
- License/package/security/docker files when present in the evidence directory.
- Root files sampled: .agent, .dockerignore, .gitattributes, .github, .gitignore, AGENTS.md, CLAUDE.md, COMMUNICATION.md, CONTRIBUTING.md, Dockerfile, LICENSE, README.md, SECURITY.md, THIRD_PARTY_NOTICES.md, bridge, case, core_agent_lines.sh, docker-compose.yml.

## Strengths

- MIT Python package, Docker compose, tests, SECURITY.md, web UI, bridge, docs, and broad tool/chat/workflow positioning.
- Recent activity and root-structure evidence were checked before scoring.

## Risks / caveats

- Large general-purpose assistant framework duplicates Hermes runtime and may create second command/memory/tool surfaces.
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
