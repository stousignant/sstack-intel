---
title: "SuperClaude-Org/SuperClaude_Framework"
type: repo-intel
source: https://github.com/SuperClaude-Org/SuperClaude_Framework
category: coding-tools
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# SuperClaude-Org/SuperClaude_Framework

> Reference-stack evaluation as reviewed 2026-05-30. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- Usefulness score: `[('Stack fit', 20, 25, 'Strong workflow overlap, but Claude Code-specific.'), ('Leverage', 21, 25, 'Can improve Hermes skill UX and lifecycle rigor.'), ('Reuse readiness', 17, 20, 'Installable and documented; needs smoke test.'), ('Maturity/trust', 13, 15, 'Active, released, security policy.'), ('Differentiation', 13, 15, 'Broad command taxonomy and installer UX are useful patterns.')]/100` — SuperClaude is a mature Claude Code configuration framework with useful lifecycle command design, personas, modes, MCP integration, installer, and security policy.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- Review candidate: Compare its 30-command lifecycle and personas against existing Hermes planning/TDD/code-review skills; patch only missing workflow gaps, not another command framework.

## Scorecard
| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Strong workflow overlap, but Claude Code-specific. |
| Leverage | 21/25 | Can improve Hermes skill UX and lifecycle rigor. |
| Reuse readiness | 17/20 | Installable and documented; needs smoke test. |
| Maturity/trust | 13/15 | Active, released, security policy. |
| Differentiation | 13/15 | Broad command taxonomy and installer UX are useful patterns. |

## Verdict

SuperClaude is a mature Claude Code configuration framework with useful lifecycle command design, personas, modes, MCP integration, installer, and security policy. It is a pattern library for workflows already using Hermes skills and delegation; wholesale adoption would risk a parallel command universe. Distill command taxonomy, verification gates, and install/list UX.

## Reference-stack relevance
- Its spec/plan/build/test/review/deploy lifecycle overlaps directly with Hermes skills; gaps can be patched into Hermes rather than installing a second framework.
- The installer/list/MCP management UX is a good benchmark for Hermes skill/plugin ergonomics.
- Its explicit security policy and v4.3 security-hardening release are useful signals for skill-framework hygiene.

## What it is

A Python/npm Claude Code configuration framework that installs slash commands, specialized agents/personas, modes, and optional MCP servers; current stable release v4.3.0.

## Evidence checked
- GitHub metadata via `gh repo view` on 2026-05-30: stars `23067`, forks `1955`, primary language `Python`, archived `False`, fork `False`.
- Maintenance signal: pushed `2026-04-27T03:08:57Z`, updated `2026-05-30T17:35:27Z`, latest release `v4.3.0` `2026-03-22T17:34:39Z`.
- License: `MIT` from GitHub/license file.
- README: `https://raw.githubusercontent.com/SuperClaude-Org/SuperClaude_Framework/master/README.md`.
- Top-level manifests/docs inspected locally under [upstream repository inspection](https://github.com/SuperClaude-Org/SuperClaude_Framework): README, package/pyproject when present, license, security file when present, top-level contents.
- Repository topics: none listed.

## Strengths
- Active and popular: ~23k stars / 2k forks; release v4.3.0 published 2026-03-22; pushed 2026-04-27.
- MIT license; PyPI install path (`pipx install superclaude`) and `superclaude install` command.
- Documents 30 slash commands, personas/agents, modes, and MCP server installation.
- Repo includes CLAUDE/AGENTS docs, project index, quality docs, security policy, pre-commit, and tests/validation artifacts.

## Risks / caveats
- Another command/persona framework can bloat prompt surfaces and conflict with Hermes skills.
- Some package metadata looks odd (`pytest plugin` phrasing, npm package artifacts), so smoke testing is needed before trusting install docs.
- Claude Code-specific assumptions limit direct portability.

## Integration ideas
- Use as a benchmark for Hermes skill discoverability: `list`, command references, decision trees, installation verification.
- Harvest only missing lifecycle gates into `writing-plans`, TDD, code-review, and session-handoff skills.
- Avoid importing personas wholesale where task-focused assistance is required; role-play sprawl adds prompt surface without a demonstrated capability need.

## Alternatives / related repos
- [Claude Code Ecosystem Comparison](../comparisons/claude-code-ecosystem.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [oraios/serena](oraios--serena.md)
- [microsoft/skills](microsoft--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)

## Review candidates and context
- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.

## Score breakdown

| Dimension | Score | Max | Note |
|---|---:|---:|---|
| Stack fit | 20 | 25 | Strong workflow overlap, but Claude Code-specific. |
| Leverage | 21 | 25 | Can improve Hermes skill UX and lifecycle rigor. |
| Reuse readiness | 17 | 20 | Installable and documented; needs smoke test. |
| Maturity/trust | 13 | 15 | Active, released, security policy. |
| Differentiation | 13 | 15 | Broad command taxonomy and installer UX are useful patterns. |
