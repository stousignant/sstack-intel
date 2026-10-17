---
title: mattpocock/skills
type: repo-intel
source: https://github.com/mattpocock/skills
category: agent-skills
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-09-05
license: MIT
---

# mattpocock/skills

> Reference-stack fit as reviewed 2026-09-05; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `88/100` — best small/composable real-engineering skill corpus in this batch; mine into SStack/Hermes rather than importing wholesale.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-09-05:** `pattern-in-use`. Grilling/domain-modeling influence, not wholesale skillpack adoption.
- **Review candidate:** selectively distill `to-spec`, `to-tickets`, and situational `wayfinder` methods into an existing portable planning owner.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 23/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 23/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 17/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 13/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 12/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

Matt Pocock’s skills are the highest-quality human-scale skill corpus in this batch: focused, pragmatic, composable, and explicitly anti-process-sprawl. For systems with an established shared-skill layer, selective distillation is safer than bulk installation that creates duplicate behavioral layers.

### 2026-09-05 refresh

- Current metadata: 252,584 stars, 21,317 forks, MIT, latest release `v1.2.3` published 2026-08-06.
- `to-spec` adds codebase/domain/ADR grounding, test-seam selection, and a compact durable parent specification.
- `to-tickets` adds vertical tracer-bullet slices, fresh-context sizing, blocking edges, and expand–migrate–contract handling for wide refactors.
- `wayfinder` is useful only when a named destination genuinely cannot be resolved in one session; upstream documentation acknowledges that it is slower and denser than grilling for ordinary work.
- Direct installation is not the canonical path: upstream documentation records inconsistent GitHub sub-issue/blocking-link creation and unreliable ticket closeout. SStack should own deterministic publication/readback while GitHub remains task truth.
- Do not import Matt's full setup, implementation, or review layers; they overlap SStack, Archon, and Hermes verification.

## Workload fit

- This repo belongs to the skill/prompt/library ecosystem that could improve SStack shared skills across Hermes, Claude Code, Codex, and future harnesses.
- The useful question is not “can we install it?” but which ideas merit durable shared-skill policy, a catalog entry, safety validation, or reusable workflow documentation.
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

Skills for Real Engineers. Straight from my .claude directory.

## Evidence checked

- GitHub metadata: stars `115799`, forks `10156`, pushed `2026-06-02T20:07:33Z`, archived `False`.
- Topics: none.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, LICENSE, CLAUDE.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, active repo, clear engineering/productivity buckets, and real-world daily-use framing.
- Explicitly argues for small/adaptable/composable skills rather than all-in process ownership.
- Good fit for SStack shared-skill authoring standards and cross-harness portability.

## Risks / caveats

- Blind import would duplicate existing Hermes/SStack skills and create prompt-policy conflict.
- Need to inspect individual skills before adopting; repository popularity is not skill-quality proof.
- Some skills may be Claude-oriented and require runtime-neutral rewriting.

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
