---
title: bmad-code-org/BMAD-METHOD
type: repo-intel
aliases:
  - BMAD-METHOD
  - BMad Method
  - GitHub repo: bmad-code-org/BMAD-METHOD
source: https://github.com/bmad-code-org/BMAD-METHOD
category: agent-methodology
topics: [github-repo, repo-intelligence, agile, ai-development, skills, workflows]
status: deep-analyzed
usefulness_score: 86
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT
---

# bmad-code-org/BMAD-METHOD

> Opinionated reference-stack evaluation, reviewed 2026-05-28. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `86/100` — rich methodology/skillpack reference for AI-driven agile workflows, but too broad to install wholesale into Hermes.
- **Recommendation:** `distill-pattern` — study agent roles, workflow maps, installer/module architecture, and quality gates; keep Hermes' own skill system as the active substrate.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Extract only the gaps: help/next-step guidance, scale-adaptive planning depth, and role-based workflow menus.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 22/25 | Strong overlap with Hermes skills, PAI workflows, and AI-driven project planning. |
| Leverage | 22/25 | Could improve project lifecycle discipline and “what next?” guidance. |
| Reuse readiness | 17/20 | npm installer, docs, modules, tests, security policy, MIT; but large framework surface. |
| Maturity/trust | 13/15 | Active, popular, quality scripts, security policy; trademark constraints should be respected. |
| Differentiation | 12/15 | Rich agent/persona workflow library, more methodology than tool primitive. |

## Verdict

BMad is a high-value pattern source, not a direct adoption target. It is a full AI-driven agile framework with agents, workflows, modules, and installable skills. Where Hermes already supplies skills and workflow policy, importing a second large ritual system risks conflict; harvest only patterns that close a demonstrated gap.

## Reference-stack relevance

- BMad's “bmad-help tells you exactly what's next” is a strong UX pattern for Hermes proactive guidance.
- Role-based agents (Analyst, PM, Architect, Developer, UX, Technical Writer) can sharpen planning and review workflows.
- Scale-adaptive planning depth helps prevent process from exceeding the risk and scope of the work.

## What it is

BMad Method is an AI-driven agile development framework. It installs skills/agents/workflows into AI IDEs and offers modules for core agile development, builder tools, test architecture, creative intelligence, and game development. The README positions it as “Build More Architect Dreams” with structured workflows, 12+ domain experts, and complete lifecycle support.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 48,200 stars, 5,617 forks, JavaScript primary language, pushed 2026-05-26, GitHub license metadata `Other` but repository `package.json` and `LICENSE` indicate MIT with trademark notice.
- README: quick start `npx bmad-method install`, non-interactive install, modules, `bmad-help`, roadmap.
- `package.json`: package `bmad-method` 6.8.0, Node >=20.12, scripts for install/uninstall, quality, tests, docs build, URL/ref/skill validation.
- `LICENSE`: MIT plus BMad trademark notice.
- `SECURITY.md`: includes prompt injection, path traversal, dependency/supply-chain, and agent/workflow security scope.
- `bmad-modules.yaml`: official module registry for Test Architect, Builder, Automator, Creative Intelligence Suite, Game Dev Studio, etc.
- `docs/index.md`: docs structure and explanation/tutorial/reference split.
- `docs/reference/agents.md`: default agents and workflow triggers.

## Strengths

- Mature-looking methodology packaging, not just loose prompts.
- Installer/module architecture and validation scripts are strong references for Hermes skillpack design.
- Explicit security policy covers agent definitions and prompt injection concerns.
- Good “help me decide what step is next” UX.

## Risks / caveats

- Heavy framework/process surface can become ceremony.
- Direct install could conflict with Hermes skill naming, behavior, and locally defined workflows.
- Trademark notice matters if reusing naming/branding.
- Agent personas can dilute accountability if not tied to proof/evidence.

## Integration ideas

- Add a Hermes “what next?” diagnostic that checks project phase and suggests the next skill/action.
- Distill BMad's role menu into optional planning/review lenses rather than persistent personas.
- Borrow module registry/validation patterns for private Hermes skillpack hygiene.

## Alternatives / related repos

- [microsoft/skills](microsoft--skills.md) and [addyosmani/agent-skills](addyosmani--agent-skills.md) — skillpack/skill-authoring references.
- [github/spec-kit](github--spec-kit.md) — more focused spec-driven workflow.
- [eyaltoledano/claude-task-master](eyaltoledano--claude-task-master.md) — concrete task/dependency manager.
- [EveryInc/compound-engineering-plugin](EveryInc--compound-engineering-plugin.md) — compound workflow/plugin reference.

## Review candidates and context

- Non-binding guidance; executable state belongs to the established issue tracker.
