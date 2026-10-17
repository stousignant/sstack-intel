---
title: openai/symphony
type: repo-intel
source: https://github.com/openai/symphony
category: agent-orchestration
status: deep-analyzed
usefulness_score: 90
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-27
license: Apache-2.0
---

# openai/symphony

> Reference-stack evaluation as reviewed 2026-05-27; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `90/100` — Best compact architecture/spec reference for autonomous implementation runs: proof-of-work, CI/PR/review evidence, safe landing, and trusted-environment warning. Distill into Hermes/Kanban, do not treat the Elixir preview as the default runtime.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-27:** `not-used`.
- Review candidate: Distill proof-of-work/run lifecycle into Hermes Kanban/repo-action schema.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23 | Directly addresses the shift from supervising agents to managing durable work units. |
| Leverage | 24 | Proof-of-work and higher-level work management could unlock more parallel repo maintenance. |
| Reuse readiness | 16 | Spec-first and Apache-licensed; reference implementation exists but Elixir/Phoenix adds adoption cost. |
| Maturity/trust | 13 | OpenAI-backed but explicitly low-key experimental preview for trusted environments; no latest GitHub release. |
| Differentiation | 14 | Cleaner spec/proof model than many agent dashboards; less productized than Multica. |

## Verdict

Best compact architecture/spec reference for autonomous implementation runs: proof-of-work, CI/PR/review evidence, safe landing, and trusted-environment warning. Distill into Hermes/Kanban, do not treat the Elixir preview as the default runtime.

## Workload fit

- Matches the exact Hermes direction: stop babysitting agents; manage work, proofs, reviews, and acceptance.
- The spec is more valuable than the implementation because Hermes already has runtime, cron, tools, GitHub, and GBrain context.

## What it is

OpenAI’s orchestration concept/spec plus experimental Elixir implementation for turning Linear/project work into isolated autonomous coding-agent implementation runs.

## Live metadata checked

- Source: https://github.com/openai/symphony
- Homepage: https://openai.com/index/open-source-codex-orchestration-symphony/
- Primary language: Elixir
- Stars / forks at review: 24716 / 2450
- Last pushed: 2026-05-20T22:28:55Z
- Latest release: none detected
- License signal: Apache License 2.0
- Topics: none

## Evidence checked

- README says Symphony monitors work boards, spawns agents, collects proof of work including CI status, PR review feedback, complexity analysis, and walkthrough videos, then safely lands PRs when accepted.
- README explicitly warns it is a low-key engineering preview for trusted environments.
- README recommends harness engineering as prerequisite and offers either implementing the SPEC or using the Elixir reference implementation.
- `SPEC.md` is large (~80 KB), making the protocol/design the primary artifact.

## Strengths

- Spec-first: easy to distill without adopting another platform.
- Proof-of-work framing is exactly what Hermes needs for autonomous coding trust.
- Apache-2.0 removes licensing friction.

## Risks / caveats

- Preview maturity; should not be pointed at sensitive repos without sandboxing.
- Elixir stack may not be worth operating just to test the ideas.
- Likely assumes a higher CI/harness maturity than all local projects currently have.

## Integration ideas

- Add “proof bundle” requirement to Hermes coding-agent handoffs: diff, tests, CI, review notes, complexity/risk, rollback path.
- Use as design oracle for repo action lifecycle and autonomous implementation runs.

### Concept connections

Symphony's proof-of-work is an **execution/return artifact** within [the agentic development lifecycle](../../../concepts/ai-engineering/agentic-development-lifecycle.md). It complements, rather than replaces, [agent work packets](../../../concepts/ai-engineering/agent-work-packets.md): a packet gives the worker scoped inputs and acceptance criteria; proof-of-work records what the run actually produced. The [orchestration comparison](../comparisons/agent-work-orchestration.md) places Symphony among related external patterns without implying runtime adoption.

## Alternatives / related repos

- [paperclipai/paperclip](paperclipai--paperclip.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [agent work orchestration](../comparisons/agent-work-orchestration.md)

## Review guidance

- Distill proof-of-work/run lifecycle into Hermes Kanban/repo-action schema.
