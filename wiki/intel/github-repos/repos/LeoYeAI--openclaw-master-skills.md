---
title: LeoYeAI/openclaw-master-skills
type: repo-intel
source: https://github.com/LeoYeAI/openclaw-master-skills
category: skill-catalog
status: deep-analyzed
usefulness_score: 68
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# LeoYeAI/openclaw-master-skills

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `68/100` — Curated weekly OpenClaw skill catalog powered by MyClaw; useful discovery/list-shape reference, but platform-marketing heavy.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Use as OpenClaw skill discovery only; sample individual high-signal skills through SStack safety review before any port.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 16/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 17/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 13/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 12/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 10/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

OpenClaw Master Skills is a useful external catalog, especially for watching how OpenClaw skill packaging evolves. It is not a trustworthy install source by default: the repo is a huge curated list with platform marketing and weekly churn.

## Reference-stack relevance

- This repo belongs to the skill/prompt/library ecosystem that could improve SStack shared skills across Hermes, Claude Code, Codex, and future harnesses.
- The main question is not whether it can be installed, but which patterns merit durable shared-skill policy, catalog structure, safety validation, or reusable workflow guidance.
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

🧠 Curated collection of 1209+ best OpenClaw skills — weekly updated by MyClaw.ai

## Evidence checked

- GitHub metadata: stars `2010`, forks `306`, pushed `2026-06-01T02:00:48Z`, archived `False`.
- Topics: ai-agent, curated, myclaw, openclaw, skills, weekly, agentskills, skill-collection.
- Inspected upstream repository: [source](https://github.com/LeoYeAI/openclaw-master-skills); capture location omitted.
- Files fetched: README.md, LICENSE, SKILL.md, root-contents.json, recent-commits.json.

## Strengths

- MIT license, weekly updates, SKILL.md, skill index, multilingual README, and large categorized skill directory.
- Useful for observing OpenClaw ecosystem skill conventions.
- Could source candidate skills for SStack after individual review.

## Risks / caveats

- Huge catalog; curation quality is not equivalent to security review.
- MyClaw platform funnel; not neutral infrastructure.
- OpenClaw-specific skill discovery is lower priority under the Hermes-first reference-stack lens.

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

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
