---
title: Chachamaru127/claude-code-harness
type: repo-intel
source: https://github.com/Chachamaru127/claude-code-harness
category: coding-tools
status: deep-analyzed
usefulness_score: 88
recommendation: watch
usage: not-used
score_confidence: high
last_reviewed: 2026-06-02
license: MIT
---

# Chachamaru127/claude-code-harness

> Reference-stack evaluation as reviewed 2026-06-02. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- Usefulness score: `88/100` — strongest external find for a literal Claude Code development harness.
- Recommendation: `sandbox`; do not standardize before comparing against Superpowers + AgentRC.
- **Usage observed 2026-06-02:** `not-used`.
- Review candidate: run a copied-repo smoke test of its Plan → Work → Review loop.

## Scorecard
| Factor | Score | Notes |
|---|---:|---|
| Software-dev fit | 24/25 | Direct Plan → Work → Review → Release operating loop. |
| Work adoption safety | 16/20 | MIT and SECURITY.md; more invasive than a skill subset. |
| Maturity/activity | 13/15 | Active, plugin packaged, docs/security files present. |
| Integration friction | 13/15 | Claude Code v2.1+ oriented; broader install surface. |
| Differentiation/leverage | 14/15 | More harness-like than most skillpacks. |
| Team usefulness | 8/10 | Good if team wants one explicit delivery loop. |

## Verdict
Among non-starred repos, this merits deep analysis because it is more targeted than generic best-practice lists and more delivery-loop oriented than many plugin catalogs.

## Evidence checked
- GitHub search result for `claude code harness` surfaced it as the top relevant external repo.
- README: “Plan. Work. Review. Ship” and dedicated Claude Code development harness framing.
- Top-level files: `.claude-code-harness.config.yaml`, `.claude-plugin`, `.codex-plugin`, `.githooks`, `SECURITY.md`, `agents`, `benchmarks`, `bin`, `docs`.
- License: `LICENSE.md` is MIT.

## Strengths
- Explicit artifact contract: spec/plan/work/review/release.
- Security policy exists.
- Good fit for software delivery teams that want more structure than raw Claude Code.

## Risks / caveats
- More adoption surface than Superpowers.
- Needs runtime smoke test; README claims are not enough.

## Integration ideas
- Use as bakeoff challenger against [Superpowers](obra--superpowers.md).
- Distill its review/release gates into team `CLAUDE.md` even if not adopted.
