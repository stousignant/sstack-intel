---
title: EveryInc/compound-engineering-plugin
type: repo-intel
source: https://github.com/EveryInc/compound-engineering-plugin
category: agent-engineering-workflows
status: deep-analyzed
usefulness_score: 85
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-27
license: MIT
---

# EveryInc/compound-engineering-plugin

> Reference-stack evaluation as reviewed 2026-05-27. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `85/100` — Excellent compound-workflow/skillpack reference — strategy, ideation, brainstorm, plan, work, debug, review, compound, pulse — but the best move is to distill into Hermes skills rather than install another command vocabulary wholesale.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-27:** `not-used`.
- Review candidate: Distill Every’s compound loop into Hermes skill authoring/review and daily project-state reporting.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22 | Directly aligns with workflows that aim to turn completed agent work into reusable context rather than one-off task completion. |
| Leverage | 23 | Strong workflow primitives for planning, review, learning capture, and product pulse. |
| Reuse readiness | 18 | MIT npm package, converter supports Claude/Codex/Cursor/Copilot/OpenCode-style targets; local help works. |
| Maturity/trust | 13 | Active releases and CI; npm lag observed vs repo release metadata. |
| Differentiation | 9 | Overlaps heavily with existing Hermes planning/review/skill workflows, but packaging and naming are strong. |

## Verdict

Excellent compound-workflow/skillpack reference — strategy, ideation, brainstorm, plan, work, debug, review, compound, pulse — but the best move is to distill into Hermes skills rather than install another command vocabulary wholesale.

## Reference-stack relevance

- This is almost a manifesto for compounding agent workflows: work should create reusable context and skills, not just ship changes.
- Useful as a source of skill design and command taxonomy; risky as a parallel workflow language.

## What it is

Agent workflow plugin/skillpack from Every for compound engineering: make each unit of work leave better strategy, plans, reviews, learnings, and pulse reports behind.

## Live metadata checked

- Source: https://github.com/EveryInc/compound-engineering-plugin
- Homepage: https://every.to/guides/compound-engineering
- Primary language: TypeScript
- Stars / forks at review: 17528 / 1347
- Last pushed: 2026-05-27T22:21:37Z
- Latest release: compound-engineering-v3.9.2
- License signal: MIT License
- Topics: compound, engineering

## Evidence checked

- README says compound engineering is 80% planning/review, 20% execution, with commands for strategy, ideation, brainstorm, plan, work, debug, code review, doc review, compound, and product pulse.
- `package.json` exposes `compound-plugin` CLI and scripts for convert/list/install/test/release validation.
- Local smoke test: `npx --yes @every-env/compound-plugin --help` succeeded, listing cleanup/convert/install/list/plugin-path. The installed npm version reported 3.8.3 while repo metadata showed release 3.9.2.
- Fetched `plugins/compound-engineering/README.md` plus large `ce-plan` and `ce-compound` skill files as evidence.

## Strengths

- Best language so far for “work should make future work easier.”
- Strong command taxonomy and cross-agent conversion story.
- Product pulse and compounding notes map well to agent learning reviews and project-state reporting derived from the existing work tracker.

## Risks / caveats

- Installing wholesale may conflict with existing Hermes skills and locally defined workflow conventions.
- Some commands may assume Claude plugin surfaces more than Hermes native tools.
- Need to inspect skill prompts for instruction hygiene before use.

## Integration ideas

- Distill `/ce-compound` into post-task learning: update the appropriate skill, memory or knowledge owner; keep task status in the existing work tracker.
- Distill `/ce-product-pulse` into daily project-state report.
- Compare `/ce-plan` against existing Hermes planning skills and patch gaps rather than duplicate.

## Alternatives / related repos

- [paperclipai/paperclip](paperclipai--paperclip.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [Agent Work Orchestration Repo Comparison](../comparisons/agent-work-orchestration.md)

## Review candidates and context

- Distill Every’s compound loop into Hermes skill authoring/review and daily project-state reporting.
