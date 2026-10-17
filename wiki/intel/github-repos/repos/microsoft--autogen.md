---
title: microsoft/autogen
type: repo-intel
aliases:
  - autogen
  - GitHub repo: microsoft/autogen
source: https://github.com/microsoft/autogen
category: agent-orchestration
topics: [github-repo, agent-orchestration, ai-agents, framework]
status: deep-analyzed
usefulness_score: 62
recommendation: reference-only
usage: not-used
score_confidence: high
last_reviewed: 2026-07-03
license: CC-BY-4.0 plus LICENSE-CODE
---

# microsoft/autogen

> Reference-stack fit as reviewed 2026-07-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `62/100` — important historical/research framework, but too broad and license-weird for core reference-stack adoption.
- **Recommendation:** `reference-only`
- **Usage observed 2026-07-03:** `not-used`.
- **Confidence:** `high`
- **Review candidate:** Keep as reference-only; inspect only when a specific AutoGen technique is relevant.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 11/25 | Fit with Hermes/Paperclip/GBrain/second-brain/SStack boundaries. |
| Leverage | 15/25 | Potential to improve autonomy, workflow reliability, and time sovereignty. |
| Reuse readiness | 13/20 | Docs, examples, release/install surface, and integration cost. |
| Maturity/trust | 13/15 | Maintenance, stars/forks, license, release signal, and org backing. |
| Differentiation | 10/15 | Unique value versus Hermes/Paperclip/current worker lanes. |
| **Total** | **62/100** | important historical/research framework, but too broad and license-weird for core reference-stack adoption. |

## Verdict

AutoGen should stay reference-only for the reference stack. It remains important in the agentic-AI ecosystem, but it is framework-heavy, research-oriented, and less aligned with the reference stack's “Hermes cockpit + Paperclip workboard + deterministic worker lanes” architecture. The license metadata is also not as clean as LangGraph/CrewAI/Agno for direct reuse decisions.

## Reference-stack relevance

- Useful when a specific AutoGen paper/tutorial has a pattern worth comparing.
- Can provide research references for multi-agent communication or evaluation patterns.
- Not a good default substrate for active reference-stack workflows.

## What it is

GitHub description: A programming framework for agentic AI

Homepage/docs: https://microsoft.github.io/autogen/

## Evidence checked

- GitHub metadata via `gh repo view microsoft/autogen` on 2026-07-03: 59469 stars, 8953 forks, license `CC-BY-4.0 plus LICENSE-CODE`, pushed `2026-04-15T11:59:09Z`, created `2023-08-18T11:43:45Z`, archived `False`.
- Latest release checked: python-v0.7.5 (2025-09-30T06:18:26Z).
- Topics: chatgpt, llm-agent, llm-framework, agentic, agentic-agi, agents, ai, autogen, framework, autogen-ecosystem.
- Root files/directories sampled through GitHub contents API: .azure, .devcontainer, .gitattributes, .github, .gitignore, CODE_OF_CONDUCT.md, CONTRIBUTING.md, FAQ.md, LICENSE, LICENSE-CODE, README.md, SECURITY.md, SUPPORT.md, TRANSPARENCY_FAQS.md, autogen-landing.jpg, codecov.yml, docs, dotnet.
- README fetched to temporary upstream inspection material for description/docs surface review.
- Local smoke test: not run. These are broad frameworks; immediate value is architectural fit and bounded future bakeoff, not installing all four into the reference stack's active environment.
- repomix pack: not generated; metadata, README, and root-structure inspection were enough for current stack-positioning decision.

## Strengths

- Huge adoption signal, Microsoft-backed, multi-language/research docs surface, security/support docs.
- Good reference material for agent conversations and ecosystem history.

## Risks / caveats

- CC-BY-4.0 repo license metadata plus separate LICENSE-CODE means direct reuse requires care.
- Broad programming framework risks becoming a second operating system.
- Less directly aligned with the reference stack's near-term Paperclip/Hermes/LangGraph split.

## Integration ideas

- Keep Hermes as cockpit/verifier and Paperclip/GitHub as work-state/evidence layers; use framework code only inside bounded worker lanes.
- Compare against the intended ownership boundaries before adoption; do not let a framework become a second operating system by default.
- If promoted, wrap the first workflow behind a deterministic SStack CLI or GitHub/Paperclip issue contract so validation remains visible.

## Alternatives / related repos

- [langchain-ai/langgraph](langchain-ai--langgraph.md) — strongest selective state-machine candidate.
- [agno-agi/agno](agno-agi--agno.md) — watch/sandbox platform candidate.
- [crewAIInc/crewAI](crewAIInc--crewAI.md) — role-team demo/reference framework.
- [microsoft/autogen](microsoft--autogen.md) — research/reference framework.
- [paperclipai/paperclip](paperclipai--paperclip.md) — workboard/control-plane layer, not a Python framework replacement.

## Review candidates and context

- Keep as reference-only; inspect only when a specific AutoGen technique is relevant.
