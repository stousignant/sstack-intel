---
title: Agent Frameworks and Reference-Stack Boundaries
created: 2026-07-03
type: comparison
status: active
tags: [github-repos, agent-frameworks, hermes, paperclip, langgraph, sai]
sources:
  - wiki/intel/github-repos/repos/langchain-ai--langgraph.md
  - wiki/intel/github-repos/repos/agno-agi--agno.md
  - wiki/intel/github-repos/repos/crewAIInc--crewAI.md
  - wiki/intel/github-repos/repos/microsoft--autogen.md
  - wiki/intel/github-repos/repos/paperclipai--paperclip.md
last_reviewed: 2026-07-03
---

# Agent Frameworks and Reference-Stack Boundaries

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Install/use selectively:** [langchain-ai/langgraph](../repos/langchain-ai--langgraph.md) — use when a workflow needs explicit state, checkpoints, and deterministic transitions.
- **Watch / sandbox:** [agno-agi/agno](../repos/agno-agi--agno.md) — credible platform candidate, but only after a tiny bakeoff proves it adds value beyond Hermes/Paperclip/GBrain.
- **Reference-only:** [crewAIInc/crewAI](../repos/crewAIInc--crewAI.md) — useful examples and role-team demos; not core reference stack infrastructure.
- **Reference-only / skip for core:** [microsoft/autogen](../repos/microsoft--autogen.md) — historically important and researchy, but broad-runtime fit and license complexity make it a poor core substrate.

## Recommended reference-stack layer split

```text
Operator interface
  → Hermes cockpit
  → optional persistent workboard/control-plane layer
  → bounded local or coding-CLI workers; selective LangGraph workflows
  → repository review and source-linked evidence
```

Paperclip is not a replacement for LangGraph/CrewAI/AutoGen/Agno. It sits one level above them as the workboard/control-plane layer: issue state, assignment, runs, approvals, artifacts, handoff, and reviewer/worker lane evidence. Hermes remains the cockpit and verifier. Framework code should live inside bounded worker lanes only when it earns the complexity.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [langchain-ai/langgraph](../repos/langchain-ai--langgraph.md) | 91 | high | medium | MIT | yes | `adopt-now` selectively for stateful workflows |
| [agno-agi/agno](../repos/agno-agi--agno.md) | 82 | high | medium | Apache-2.0 | likely | `watch` / sandbox bakeoff |
| [crewAIInc/crewAI](../repos/crewAIInc--crewAI.md) | 70 | high | low-medium | MIT | yes | `reference-only` examples/demos |
| [microsoft/autogen](../repos/microsoft--autogen.md) | 62 | high | medium | CC-BY-4.0 + LICENSE-CODE | yes | `reference-only` research patterns |

## Category map

- **State-machine workflow framework:** LangGraph. Best fit for deterministic, inspectable pipelines.
- **Agent platform framework:** Agno. Potentially useful, but must not duplicate reference stack ownership layers.
- **Role-team orchestration framework:** CrewAI. Useful mental model for demos; risky as core methodology.
- **Research/programming framework:** AutoGen. Useful ecosystem reference; not a near-term reference stack substrate.
- **Control-plane / work-state layer:** Paperclip. Separate category: it coordinates work and evidence, not Python graph logic.

## Reference-stack recommendation

Under the reviewed reference-stack criteria, default to **Hermes + Paperclip + selective LangGraph**.

Use LangGraph for the first real framework experiment. Candidate first slice: a research/evaluation or repo-intelligence workflow with explicit states like `collect evidence → run deterministic job → summarize → judge → write proof → stop`. Keep run evidence attached to the existing commitment owner rather than introducing a second backlog.

Do not add CrewAI or AutoGen to the core stack. Mine examples only. Put Agno behind a later bakeoff if LangGraph feels too heavy or Agno offers a simpler implementation boundary for a real task.

## Open questions

- Which first workflow should become the LangGraph pilot: research backtest/eval, repo-intel ingestion, source-intel enrichment, or stack maintenance?
- Should Paperclip own the pilot's issue/run wrapper, or should the first pass stay GitHub/Hermes-only and add Paperclip after the workflow contract is stable?
- What acceptance proof makes the framework worth keeping: fewer manual steps, better checkpoint/resume, clearer evidence, lower review time, or easier replay?
