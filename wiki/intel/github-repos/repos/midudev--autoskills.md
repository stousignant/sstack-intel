---
title: midudev/autoskills
type: repo-intel
source: https://github.com/midudev/autoskills
category: skill-installer
status: deep-analyzed
usefulness_score: 74
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: CC-BY-NC-4.0
---

# midudev/autoskills

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `74/100` — Interesting project-tech-stack detector and skill installer; non-commercial license and automatic mutation make it pattern-first.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Mine tech-stack detection and curated-install UX patterns; do not run against canonical repos until install plan/dry-run/safety is verified.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 19/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 11/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 13/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 11/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

Autoskills is strategically interesting because automatic project scanning → skill installation is exactly where SStack could eventually go. But the license is non-commercial and the mutating installer model is risky. Treat it as product/UX inspiration for a future SStack doctor/recommend flow.

## Reference-stack relevance

- This repo belongs to the skill/prompt/library ecosystem that could improve SStack shared skills across Hermes, Claude Code, Codex, and future harnesses.
- The main question is not “can we install it?” but “what should become durable SStack skill policy, catalog shape, safety validation, or reusable workflow memory?”
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

One command. Your entire AI skill stack. Installed.

## Evidence checked

- GitHub metadata: stars `5798`, forks `542`, pushed `2026-06-01T11:11:10Z`, archived `False`.
- Topics: none.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, LICENSE, SECURITY.md, package.json, AGENTS.md, root-contents.json, recent-commits.json.

## Strengths

- Clear one-command value prop: scan project, detect stack, install relevant AI skills.
- Active package/app repo with security policy, AGENTS.md, package, and scripts.
- Good UX reference for future SStack skill recommendation/installer flows.

## Risks / caveats

- Creative Commons Attribution-NonCommercial 4.0 license blocks clean reuse in many contexts.
- Automatic install behavior can mutate repo/agent instructions unsafely.
- Need dry-run and destination controls before any local test.

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
