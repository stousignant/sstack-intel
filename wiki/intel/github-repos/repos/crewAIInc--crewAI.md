---
title: crewAIInc/crewAI
type: repo-intel
aliases:
  - crewAI
  - GitHub repo: crewAIInc/crewAI
source: https://github.com/crewAIInc/crewAI
category: agent-orchestration
topics: [github-repo, agent-orchestration, ai-agents, framework]
status: deep-analyzed
usefulness_score: 70
recommendation: reference-only
usage: not-used
score_confidence: high
last_reviewed: 2026-07-03
license: MIT
---

# crewAIInc/crewAI

> Opinionated reference-stack evaluation, reviewed 2026-07-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `70/100` — popular and active, but role-play team abstraction is a poor default for workflows that need durable work state and deterministic checks.
- **Recommendation:** `reference-only`
- **Usage observed 2026-07-03:** `not-used`.
- **Confidence:** `high`
- **Review candidate:** Mine examples/patterns only; do not add CrewAI to core stack unless one bounded prototype clearly wins.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 14/25 | Fit with Hermes/Paperclip/GBrain/second-brain/SStack boundaries. |
| Leverage | 16/25 | Potential to improve autonomy, workflow reliability, and time sovereignty. |
| Reuse readiness | 16/20 | Docs, examples, release/install surface, and integration cost. |
| Maturity/trust | 14/15 | Maintenance, stars/forks, license, release signal, and org backing. |
| Differentiation | 10/15 | Unique value versus Hermes/Paperclip/current worker lanes. |
| **Total** | **70/100** | popular and active, but role-play team abstraction is the wrong default core for the reference stack. |

## Verdict

CrewAI is useful inspiration and example material, but role-playing team abstractions can add ceremony and prompt theater to workloads where durable work state, deterministic checks, and clear Hermes/Paperclip/GitHub ownership boundaries matter more.

## Workload fit

- Good source for business automation examples and role/crew prompt patterns.
- Can help when a quick prototype benefits from a simple “researcher/writer/reviewer” setup.
- Not the right foundation for specialized analysis, repo intelligence, or SStack/Hermes operations.

## What it is

GitHub description: Framework for orchestrating role-playing, autonomous AI agents. By fostering collaborative intelligence, CrewAI empowers agents to work together seamlessly, tackling complex tasks.

Homepage/docs: https://crewai.com

## Evidence checked

- GitHub metadata via `gh repo view crewAIInc/crewAI` on 2026-07-03: 54841 stars, 7686 forks, license `MIT`, pushed `2026-07-03T08:22:51Z`, created `2023-10-27T03:26:59Z`, archived `False`.
- Latest release checked: 1.15.1 (2026-06-27T06:50:46Z).
- Topics: agents, ai, ai-agents, llms, aiagentframework.
- Root files/directories sampled through GitHub contents API: .editorconfig, .env.test, .github, .gitignore, .pre-commit-config.yaml, .python-version, AGENTS.md, LICENSE, README.md, conftest.py, docs, lib, pyproject.toml, scripts, uv.lock.
- README fetched to [upstream README](https://github.com/crewAIInc/crewAI) for description/docs surface review.
- Local smoke test: not run. These are broad frameworks; immediate value is architectural fit and bounded future bakeoff, not installing all four into the reference environment.
- repomix pack: not generated; metadata, README, and root-structure inspection were enough for current stack-positioning decision.

## Strengths

- MIT, active, large community, current release, substantial docs/examples.
- Simple mental model for demo teams and business-workflow automation.

## Risks / caveats

- Role-agent framing can hide state and verification behind chatty abstractions.
- CrewAI examples repo is archived; do not over-index on old examples as current practice.
- Adopting it core would add another orchestration layer beside Paperclip and Hermes.

## Integration ideas

- Keep Hermes as cockpit/verifier and Paperclip/GitHub as work-state/evidence layers; use framework code only inside bounded worker lanes.
- Compare against existing orchestration and task-state ownership before adoption; do not let a framework become a second operating system by default.
- If promoted, wrap the first workflow behind a deterministic SStack CLI or GitHub/Paperclip issue contract so validation remains visible.

## Alternatives / related repos

- [langchain-ai/langgraph](langchain-ai--langgraph.md) — strongest selective state-machine candidate.
- [agno-agi/agno](agno-agi--agno.md) — watch/sandbox platform candidate.
- [crewAIInc/crewAI](crewAIInc--crewAI.md) — role-team demo/reference framework.
- [microsoft/autogen](microsoft--autogen.md) — research/reference framework.
- [paperclipai/paperclip](paperclipai--paperclip.md) — workboard/control-plane layer, not a Python framework replacement.

## Review candidates and context

- Mine examples/patterns only; do not add CrewAI to core stack unless one bounded prototype clearly wins.
