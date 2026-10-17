---
title: wshobson/agents
type: repo-intel
source: https://github.com/wshobson/agents
category: coding-tools
status: deep-analyzed
usefulness_score: 84
recommendation: watch
usage: not-used
score_confidence: high
last_reviewed: 2026-06-02
license: MIT

---

# wshobson/agents

> Reference-stack evaluation as reviewed 2026-06-02; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- Usefulness score: `84/100` — strong multi-harness plugin marketplace and discovery/reference layer.
- Recommendation: `watch/sandbox`; do not install wholesale in a job repo.
- **Usage observed 2026-06-02:** `not-used`.
- Review candidate: inspect specific plugins/agents only when a concrete need appears.

## Scorecard
| Factor | Score | Notes |
|---|---:|---|
| Software-dev fit | 22/25 | Large catalog of agents/skills/commands for development workflows. |
| Work adoption safety | 14/20 | Breadth increases prompt-surface and review burden. |
| Maturity/activity | 13/15 | Active, popular, multi-harness docs. |
| Integration friction | 12/15 | Marketplace model; install only subsets. |
| Differentiation/leverage | 14/15 | One-source-to-many-harness artifact model is valuable. |
| Team usefulness | 9/10 | Could standardize reusable agents if curated. |

## Verdict
The key idea is not “install 191 agents”; it is **single source of truth with native projections per harness**. This can inform portable cross-agent skill systems, but the catalog is too broad for a default working set.

## Evidence checked
- README claims: 83 plugins, 191 agents, 155 skills, 102 commands; Claude Code, Codex, Cursor, OpenCode, Gemini, Copilot support.
- Top-level files: `.claude-plugin`, `.cursor-plugin`, `.gemini`, `.agents`, `plugins`, `tools`, docs and architecture files.
