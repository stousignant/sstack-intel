---
title: obra/superpowers
type: repo-intel
source: https://github.com/obra/superpowers
category: coding-tools
status: deep-analyzed
usefulness_score: 92
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-02
license: MIT
---

# obra/superpowers

> Reference-stack evaluation as reviewed 2026-06-02; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- Usefulness score: `92/100` — best overall Claude Code harness enhancer for a work-safe software-development pilot.
- Recommendation: `adopt-now` for a bounded pilot; start with the core SDLC/TDD skills, not the whole universe.
- **Usage observed 2026-06-02:** `not-used`.
- Review candidate: pilot on a non-sensitive repo/fork and compare against vanilla Claude Code + `CLAUDE.md`.

## Scorecard
| Factor | Score | Notes |
|---|---:|---|
| Software-dev fit | 24/25 | Strong spec/plan/TDD/debug/review methodology. |
| Work adoption safety | 18/20 | MIT, multi-harness, smaller blast radius than orchestration platforms. |
| Maturity/activity | 14/15 | Very active and widely starred; plugin metadata checked. |
| Integration friction | 14/15 | Claude Code plugin plus Codex/Cursor/OpenCode/Gemini/Copilot paths. |
| Differentiation/leverage | 14/15 | Turns Claude Code into a disciplined engineering workflow without a new runtime. |
| Team usefulness | 8/10 | Team can standardize method if the subset is curated. |

## Verdict
Superpowers is the default pick for the reviewed team-development use case: a methodology/skills layer, not a giant control plane. It should improve Claude Code behavior around specs, planning, TDD, debugging, review, and collaboration while staying easy to explain to teammates.

## Evidence checked
- GitHub metadata: active repo, very high star/fork count, pushed 2026-06-02.
- README: describes a complete software development methodology and multi-harness quickstart.
- License: `LICENSE` and plugin metadata identify MIT.
- Top-level files: `.claude-plugin`, `.codex-plugin`, `.cursor-plugin`, `.opencode`, `AGENTS.md`, `CLAUDE.md`, `hooks`, `skills`, `tests`.

## Strengths
- Best balance of software development rigor and adoption simplicity.
- Multi-harness portability reduces lock-in.
- Method maps well to job/team practices: specification, plan, TDD, review.

## Risks / caveats
- Still a prompt/skill dependency; review installed skills before broad work use.
- Installing multiple skillpacks at once risks contradictory instructions.

## Integration ideas
- Pair with [microsoft/agentrc](microsoft--agentrc.md) for repo context.
- Compare against [Claude Code Harness](Chachamaru127--claude-code-harness.md) on the same ticket.

## Review guidance
- Review candidate: run a bounded Superpowers vs vanilla Claude Code bakeoff on non-sensitive inputs.
