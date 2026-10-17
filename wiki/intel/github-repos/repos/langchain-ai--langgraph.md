---
title: langchain-ai/langgraph
type: repo-intel
aliases:
  - langgraph
  - GitHub repo: langchain-ai/langgraph
source: https://github.com/langchain-ai/langgraph
category: agent-orchestration
topics: [github-repo, agent-orchestration, ai-agents, framework]
status: deep-analyzed
usefulness_score: 91
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-07-03
license: MIT
---

# langchain-ai/langgraph

> Reference-stack fit as reviewed 2026-07-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `91/100` — best selective framework for explicit state machines in the reference stack: state, checkpoints, routing, and boundary-only agent decisions.
- **Recommendation:** `adopt-now`
- **Usage observed 2026-07-03:** `not-used`.
- **Confidence:** `high`
- **Review candidate:** Run one bounded research/eval workflow pilot with explicit states and Paperclip/GitHub evidence.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Fit with Hermes/Paperclip/GBrain/second-brain/SStack boundaries. |
| Leverage | 23/25 | Potential to improve autonomy, workflow reliability, and time sovereignty. |
| Reuse readiness | 18/20 | Docs, examples, release/install surface, and integration cost. |
| Maturity/trust | 14/15 | Maintenance, stars/forks, license, release signal, and org backing. |
| Differentiation | 12/15 | Unique value versus Hermes/Paperclip/current worker lanes. |
| **Total** | **91/100** | best selective framework for explicit state machines in the reference stack: state, checkpoints, routing, and boundary-only agent decisions. |

## Verdict

Among the four broad Python agent frameworks, LangGraph is the strongest candidate for selective use in workflows needing explicit state machines. It should not replace Hermes or Paperclip; use it only inside bounded workflows that need explicit graph state, checkpointing, resumability, durable handoffs, or deterministic step transitions.

## Reference-stack relevance

- Maps directly to the reference stack's preference for event-driven loops where deterministic jobs wait and agents decide only at boundaries.
- Good fit for research/backtest/eval pipelines, repo-intel workflows, and RAG/document pipelines that need checkpoints instead of hidden chat loops.
- Lets Hermes/Paperclip remain the cockpit/workboard while LangGraph is just an implementation primitive inside a worker lane.

## What it is

GitHub description: Build resilient agents.

Homepage/docs: https://docs.langchain.com/oss/python/langgraph/

## Evidence checked

- GitHub metadata via `gh repo view langchain-ai/langgraph` on 2026-07-03: 36409 stars, 6092 forks, license `MIT`, pushed `2026-07-01T17:59:54Z`, created `2023-08-09T18:33:12Z`, archived `False`.
- Latest release checked: 1.2.7 (2026-06-30T01:24:26Z).
- Topics: agents, ai, ai-agents, chatgpt, deepagents, enterprise, framework, gemini, generative-ai, langchain, langgraph, llm, multiagent, open-source, openai, pydantic, python, rag.
- Root files/directories sampled through GitHub contents API: .github, .gitignore, .markdownlint.json, AGENTS.md, CLAUDE.md, LICENSE, Makefile, README.md, docs, examples, libs.
- README fetched to temporary upstream inspection material for description/docs surface review.
- Local smoke test: not run. These are broad frameworks; immediate value is architectural fit and bounded future bakeoff, not installing all four into the reference stack's active environment.
- repomix pack: not generated; metadata, README, and root-structure inspection were enough for current stack-positioning decision.

## Strengths

- MIT license, large active ecosystem, current releases, and strong docs surface.
- README/docs position it around resilient agents rather than role-play teams, which fits the reference stack better than generic multi-agent theatrics.
- Graph/state abstraction is easy to wrap behind SStack CLIs and Paperclip/GitHub issue contracts.

## Risks / caveats

- Still adds LangChain ecosystem gravity; keep it inside specific pipelines, not global runtime policy.
- Needs tiny reference-workflow-specific bakeoff before becoming a default pattern.

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

- Run one bounded research/eval workflow pilot with explicit states and Paperclip/GitHub evidence.
