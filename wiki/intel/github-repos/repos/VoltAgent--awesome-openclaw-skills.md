---
title: VoltAgent/awesome-openclaw-skills
type: repo-intel
source: https://github.com/VoltAgent/awesome-openclaw-skills
category: skill-catalog
status: deep-analyzed
usefulness_score: 64
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# VoltAgent/awesome-openclaw-skills

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `64/100` — Large awesome-list of OpenClaw skills; discovery index only, not an operational dependency.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Keep as a low-priority discovery source for OpenClaw skill categories; do not spend active batch time unless OpenClaw returns to scope.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 13/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 15/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 12/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 14/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 10/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

This is a broad discovery list, not a high-confidence engineering artifact. Use it to identify categories or candidate OpenClaw skills when a concrete evaluation question needs them; each linked skill requires its own quality and safety review.

## Workload fit

- This catalog is relevant when curating skills across Hermes, Claude Code, Codex, and other agent harnesses.
- The useful question is not “can we install it?” but which candidates merit durable shared-skill policy, a catalog entry, safety validation, or reusable workflow documentation.
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

The awesome collection of OpenClaw skills. 5,400+ skills filtered and categorized from the official OpenClaw Skills Registry.🦞

## Evidence checked

- GitHub metadata: stars `49731`, forks `4851`, pushed `2026-06-03T10:24:11Z`, archived `False`.
- Topics: agent-skills, awesome-list, clawdbot, clawdbot-skill, clawd, clawdhub, moltbot, moltbot-skills, openclaw, openclaw-skills, awesome, awesome-lists.
- Inspected upstream repository: [source](https://github.com/VoltAgent/awesome-openclaw-skills); capture location omitted.
- Files fetched: README.md, LICENSE, root-contents.json, recent-commits.json.

## Strengths

- MIT license, active updates, and large category structure.
- Useful for OpenClaw ecosystem map and skill taxonomy.
- Low adoption cost as a reference link.

## Risks / caveats

- Awesome-list shape gives weak evidence about individual skill quality.
- OpenClaw focus limits direct use in environments that do not run OpenClaw.
- May duplicate LeoYeAI/openclaw-master-skills discovery value.

## Integration ideas

- Use as a source of candidate patterns for shared skills, not as an automatic installation target.
- Any skill or prompt copied into SStack needs license review, runtime-neutral rewriting, support-file projection checks, and safety-scan/doctor validation.
- Prefer a small curated skill-recommendation flow over bulk importing thousands of community skills.

## Alternatives / related repos

- [Skills / prompt libraries comparison](../comparisons/skills-prompt-libraries.md)
- [microsoft/skills](microsoft--skills.md)
- [google/skills](google--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)
- [steipete/agent-scripts](steipete--agent-scripts.md)

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
