---
title: opensesh/KARIMO
type: repo-intel
source: https://github.com/opensesh/KARIMO
category: coding-tools
status: deep-analyzed
usefulness_score: 80
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-02
license: Apache-2.0
---

# opensesh/KARIMO

> Reference-stack evaluation as reviewed 2026-06-02; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- Usefulness score: `80/100` — interesting PRD-driven Claude Code harness plugin, but smaller and less proven than the top candidates.
- Recommendation: `watch`; sandbox only after Superpowers / AgentRC / Claude Code Harness.
- **Usage observed 2026-06-02:** `not-used`.
- Review candidate: revisit if product-design-driven agent orchestration becomes the team's bottleneck.

## Scorecard
| Factor | Score | Notes |
|---|---:|---|
| Software-dev fit | 21/25 | PRD → plan → tasks → review orchestration maps to dev work. |
| Work adoption safety | 17/20 | Apache-2.0; plugin packaging; still agent-team orchestration. |
| Maturity/activity | 9/15 | Active enough but much smaller community. |
| Integration friction | 12/15 | Claude plugin; methodology may be opinionated. |
| Differentiation/leverage | 13/15 | Strong product/design angle. |
| Team usefulness | 8/10 | Useful for teams that need PRD discipline. |

## Evidence checked
- GitHub search result for Claude Code harness alternatives.
- README: PRD-driven autonomous agent orchestration harness plugin for Claude Code.
- Top-level files: `.claude-plugin`, `.claude`, `.karimo`, `tests`, `CHANGELOG.md`, `LICENSE`, `NOTICE`.
- License: Apache-2.0.

## Verdict
KARIMO is worth knowing about, not worth choosing first. It may be excellent for product/design-heavy teams, but the evidence base is thinner than Superpowers or Claude Code Harness.
