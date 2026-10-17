---
title: agno-agi/agno
type: repo-intel
aliases:
  - agno
  - GitHub repo: agno-agi/agno
source: https://github.com/agno-agi/agno
category: agent-orchestration
topics: [github-repo, agent-orchestration, ai-agents, framework]
status: deep-analyzed
usefulness_score: 82
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-07-03
license: Apache-2.0
---

# agno-agi/agno

> Opinionated reference-stack evaluation, reviewed 2026-07-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — promising lightweight agent-platform candidate, but overlaps reference-stack ownership boundaries until a bakeoff proves value.
- **Recommendation:** `watch`
- **Usage observed 2026-07-03:** `not-used`.
- **Confidence:** `medium`
- **Review candidate:** Sandbox Agno against the same tiny workflow used for LangGraph only if LangGraph proves too heavy or if Agno offers a simpler implementation boundary.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 19/25 | Fit with Hermes/Paperclip/GBrain/second-brain/SStack boundaries. |
| Leverage | 20/25 | Potential to improve autonomy, workflow reliability, and time sovereignty. |
| Reuse readiness | 17/20 | Docs, examples, release/install surface, and integration cost. |
| Maturity/trust | 14/15 | Maintenance, stars/forks, license, release signal, and org backing. |
| Differentiation | 12/15 | Unique value versus Hermes/Paperclip/current worker lanes. |
| **Total** | **82/100** | promising lightweight agent-platform candidate, but overlaps reference-stack ownership boundaries until a bakeoff proves value. |

## Verdict

Agno is the strongest watch/sandbox candidate after LangGraph. Its positioning around building, running, and managing agent platforms is relevant, and Apache-2.0 is clean, but direct adoption risks duplicating Hermes tools/skills, Paperclip control-plane state, and GBrain memory/index ownership.

## Reference-stack relevance

- Could be useful for quick agent-platform prototypes or bounded tool-agent experiments.
- Worth comparing against Hermes+Paperclip+LangGraph on one small real workflow before rejecting or adopting.
- Clean license and active release cadence make it a credible candidate rather than a random framework.

## What it is

GitHub description: Build, run, and manage agent platforms.

Homepage/docs: https://docs.agno.com

## Evidence checked

- GitHub metadata via `gh repo view agno-agi/agno` on 2026-07-03: 40982 stars, 5593 forks, license `Apache-2.0`, pushed `2026-07-03T15:23:41Z`, created `2022-05-04T15:23:02Z`, archived `False`.
- Latest release checked: v2.6.22 (2026-07-03T15:23:41Z).
- Topics: developer-tools, python, agents, ai, ai-agents.
- Root files/directories sampled through GitHub contents API: .cursorrules, .editorconfig, .github, .gitignore, AGENTS.md, CLAUDE.md, CODEOWNERS, CODE_OF_CONDUCT.md, CONTRIBUTING.md, LICENSE, README.md, cookbook, libs, scripts.
- README fetched to [upstream README](https://github.com/agno-agi/agno) for description/docs surface review.
- Local smoke test: not run. These are broad frameworks; immediate value is architectural fit and bounded future bakeoff, not installing all four into the reference environment.
- repomix pack: not generated; metadata, README, and root-structure inspection were enough for current stack-positioning decision.

## Strengths

- Apache-2.0, active releases, large adoption signal, docs/cookbook surface.
- Root includes AGENTS.md/CLAUDE.md and cookbook/libs layout, suggesting agent-facing development ergonomics.

## Risks / caveats

- Likely overlaps with Hermes, Paperclip, and GBrain if adopted as a broad platform.
- Needs a clear winning use case; otherwise it becomes another half-owned runtime.

## Integration ideas

- Keep Hermes as cockpit/verifier and Paperclip/GitHub as work-state/evidence layers; use framework code only inside bounded worker lanes.
- Compare against the reference architecture before adoption; do not let a framework become a second operating system by default.
- If promoted, wrap the first workflow behind a deterministic SStack CLI or GitHub/Paperclip issue contract so validation remains visible.

## Alternatives / related repos

- [langchain-ai/langgraph](langchain-ai--langgraph.md) — strongest selective state-machine candidate.
- [agno-agi/agno](agno-agi--agno.md) — watch/sandbox platform candidate.
- [crewAIInc/crewAI](crewAIInc--crewAI.md) — role-team demo/reference framework.
- [microsoft/autogen](microsoft--autogen.md) — research/reference framework.
- [paperclipai/paperclip](paperclipai--paperclip.md) — workboard/control-plane layer, not a Python framework replacement.

## Review candidates and context

- Sandbox Agno against the same tiny workflow used for LangGraph only if LangGraph proves too heavy or if Agno offers a simpler implementation boundary.
