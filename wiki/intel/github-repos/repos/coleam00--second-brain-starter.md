---
title: coleam00/second-brain-starter
type: repo-intel
aliases:
  - second-brain-starter
  - GitHub repo: coleam00/second-brain-starter
source: https://github.com/coleam00/second-brain-starter
category: personal-ai-infrastructure
topics: [github-repo, second-brain, claude-code, prd, personal-ai, skills]
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: NOASSERTION
---

# coleam00/second-brain-starter

> Opinionated reference-stack evaluation, reviewed 2026-05-28. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `80/100` — useful onboarding/planning pattern for personal second brains, but less valuable than the Hermes/GBrain/PAI reference architecture.
- **Recommendation:** `distill-pattern` — steal the requirements-template → generated PRD workflow; do not treat it as a runtime or canonical architecture.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Adapt the requirements-template pattern into PAI/Hermes planning only if a repeatable onboarding or project-agent setup flow is needed.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | Directly adjacent to second-brain/PAI workflows, but Claude Code specific and simpler than Hermes/GBrain. |
| Leverage | 21/25 | Strong for turning vague “build me a second brain” goals into a concrete plan. |
| Reuse readiness | 15/20 | Easy to copy as a `.claude` skill/template; unknown license limits reuse confidence. |
| Maturity/trust | 10/15 | Small repo with recent activity and clear README, but no detected license and limited implementation surface. |
| Differentiation | 13/15 | The differentiator is not code; it is a structured questionnaire that generates a phased PRD. |

## Verdict

This is a **planning artifact pattern**, not infrastructure. The reference architecture already includes agent execution, indexed Markdown knowledge, scheduling, interaction, skills and session search. The reusable bit is the front door: an 8-section requirements template that turns a user's life/tooling context into a phased PRD. That could become a PAI onboarding workflow or a Hermes “define ideal assistant” skill.

## Reference-stack relevance

- It validates the same direction: persistent memory, proactive monitoring, chat interface, integrations, security boundaries.
- It offers a clean human-input schema for second-brain requirements.
- Could help turn personal-AI requirements into a repeatable onboarding flow rather than bespoke notes.

## What it is

A Claude Code skill that generates a personalized PRD for building a proactive, persistent AI assistant. The README describes an 8-section requirements template and a 9-phase build plan covering memory, hooks, search, integrations, proactive systems, chat interface, security, and deployment.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 557 stars, 136 forks, no primary language, no detected license, pushed 2026-03-29, not archived.
- README: quickstart, requirements template, 9-phase build plan, Claude Code invocation `/create-second-brain-prd`.
- Root contents: the upstream `.claude` directory, README, two architecture images; small skill/template repo rather than an app.

## Strengths

- Clear requirements-driven process.
- Strong match to personal AI/second-brain market language.
- Low complexity; easy to inspect and adapt.

## Risks / caveats

- No GitHub license detected; do not copy substantial text/code wholesale without checking.
- Claude Code-specific packaging; Hermes should translate the pattern rather than import it blindly.
- It generates plans, not working infrastructure.

## Integration ideas

- Use as inspiration for a Hermes/PAI “life OS requirements interview” skill.
- Fold its security-boundary prompts into PAI/SOUL/context-capsule setup.
- Convert the 9-phase output into a Hermes plan template only when onboarding another person or project is an active requirement.

## Alternatives / related repos

- [danielmiessler/LifeOS](danielmiessler--LifeOS.md) — richer upstream LifeOS/PAI pattern stream.
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — actual local runtime.
- [garrytan/gbrain](garrytan--gbrain.md) — actual memory/search substrate.

## Review candidates and context

- Non-binding candidate: a possible PAI/Hermes requirements-template distillation.
