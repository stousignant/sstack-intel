---
title: multica-ai/andrej-karpathy-skills
type: repo-intel
source: https://github.com/multica-ai/andrej-karpathy-skills
category: agent-instructions
status: deep-analyzed
usefulness_score: 86
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-06-03
license: NOASSERTION
---

# multica-ai/andrej-karpathy-skills

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `86/100` — Tiny high-signal behavioral guideline layer that maps directly to Hermes anti-overengineering / clarify-confusion / protect-comments discipline.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `pattern-in-use`.
- **Review candidate:** Compare its four principles against current SStack/Hermes instruction hygiene and patch only missing crisp wording, not the whole CLAUDE.md.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 24/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 22/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 18/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 10/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 12/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

This is a small, useful corrective against common coding-agent failure modes. It is already spiritually aligned with the reference stack’s Hermes persona and SStack skill hygiene: push back, avoid overbuilding, preserve intent, and surface uncertainty. Treat it as a wording/policy reference, not a new command framework.

## Reference-stack relevance

- This repo belongs to the skill/prompt/library ecosystem that could improve SStack shared skills across Hermes, Claude Code, Codex, and future harnesses.
- The main question is not “can we install it?” but “what should become durable SStack skill policy, catalog shape, safety validation, or reusable workflow memory?”
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

A single CLAUDE.md file to improve Claude Code behavior, derived from Andrej Karpathy's observations on LLM coding pitfalls.

## Evidence checked

- GitHub metadata: stars `166467`, forks `17038`, pushed `2026-04-20T10:05:04Z`, archived `False`.
- Topics: none.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- Single-file CLAUDE.md plus examples and Cursor support make it easy to audit.
- Directly targets LLM coding pitfalls the reference lens cares about: assumptions, confusion management, overcomplication, accidental side effects.
- Low adoption surface if distilled into existing SStack/Hermes guidance.

## Risks / caveats

- No license file detected in fetched evidence; avoid copying text wholesale.
- Extremely popular/starred but still just guidance, not validated workflow infrastructure.
- Could become redundant if layered on top of existing Hermes persona and skill instructions.

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
