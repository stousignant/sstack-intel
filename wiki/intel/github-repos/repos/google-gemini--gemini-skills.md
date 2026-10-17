---
title: google-gemini/gemini-skills
type: repo-intel
source: https://github.com/google-gemini/gemini-skills
category: model-specific-skills
status: deep-analyzed
usefulness_score: 78
recommendation: reference-only
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: Apache-2.0
---

# google-gemini/gemini-skills

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `78/100` — Official Apache Gemini API skill library; useful when working with Gemini apps, less relevant to Hermes default stack.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Keep as a model/API-specific skill reference; mine only when a Gemini implementation task appears.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 17/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 18/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 18/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 15/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 10/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

Gemini Skills is clean and official, but narrow. It is valuable because it demonstrates how a model vendor encodes fast-changing SDK/API practices into skills. For the reference stack, it is not a default skill source unless Gemini app development becomes active.

## Reference-stack relevance

- This repo belongs to the skill/prompt/library ecosystem that could improve SStack shared skills across Hermes, Claude Code, Codex, and future harnesses.
- The main question is not whether it can be installed, but which patterns merit durable shared-skill policy, catalog structure, safety validation, or reusable workflow guidance.
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

Skills for the Gemini API, SDK and model/agent interactions

## Evidence checked

- GitHub metadata: stars `3594`, forks `349`, pushed `2026-05-20T10:18:44Z`, archived `False`.
- Topics: gemini, gemini-api, skills.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, LICENSE, root-contents.json, recent-commits.json.

## Strengths

- Official google-gemini repo, Apache-2.0 license, active updates, and focused skill folder.
- Clear rationale: skills patch LLM knowledge gaps around fast-changing SDK/model behavior.
- Good reference for model/API-specific skills without bloated framework ceremony.

## Risks / caveats

- Gemini-specific; relevant when a workflow actively builds Gemini apps, otherwise a low-priority skill source.
- Small category scope compared with SStack needs.
- Should not be mixed into generic Hermes behavior.

## Integration ideas

- Use as a source of candidate patterns for SStack shared skills, not as an automatic install target.
- Any skill or prompt copied into SStack needs license review, runtime-neutral rewriting, support-file projection checks, and safety-scan/doctor validation.
- Prefer building a small curated SStack skill recommendation flow over bulk importing thousands of community skills.

## Alternatives / related repos

- [Skills / prompt libraries comparison](../comparisons/skills-prompt-libraries.md)
- [microsoft/skills](microsoft--skills.md)
- [google/skills](google--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)
- [steipete/agent-scripts](steipete--agent-scripts.md)

## Review candidates and context

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
