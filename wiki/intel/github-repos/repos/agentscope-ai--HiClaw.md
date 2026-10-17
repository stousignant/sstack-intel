---
title: agentscope-ai/HiClaw
type: repo-intel
source: https://github.com/agentscope-ai/HiClaw
category: agent-orchestration
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-05-27
license: Apache-2.0
---

# agentscope-ai/HiClaw

> Opinionated reference-stack evaluation, reviewed 2026-05-27. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `82/100` — High-signal enterprise multi-agent orchestration reference — Matrix rooms, Manager/Workers, shared filesystem, gateway, declarative resources — but Kubernetes/enterprise scope makes it pattern material, not a proportionate runtime for local Hermes workflows.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-27:** `not-used`.
- Review candidate: Reference-only for now; distill transparent collaboration semantics into subagent/Kanban guidance.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20 | Mentions Hermes workers and human-visible agent rooms, but assumes heavier enterprise/Kubernetes deployment. |
| Leverage | 22 | Strong collaboration and governance semantics could improve multi-agent transparency. |
| Reuse readiness | 12 | Install path exists but includes IM server, gateway, shared FS, Kubernetes/Helm style architecture. |
| Maturity/trust | 14 | Apache-2.0, releases, docs, DeepWiki badge, active pushes; still new and complex. |
| Differentiation | 14 | Best human-visible Matrix-room coordination model in the batch. |

## Verdict

High-signal enterprise multi-agent orchestration reference — Matrix rooms, Manager/Workers, shared filesystem, gateway, declarative resources — but Kubernetes/enterprise scope makes it pattern material rather than a proportionate runtime for local Hermes workflows.

## Reference-stack relevance

- Useful where multi-agent work needs Discord/Matrix-like visibility rather than hidden background processes.
- Pattern can improve Hermes delegation transparency without importing a Kubernetes-scale stack.

## What it is

Collaborative multi-agent runtime platform where Manager and Worker agents coordinate in auditable Matrix rooms with shared filesystems, gateway-managed credentials, and declarative resources.

## Live metadata checked

- Source: https://github.com/agentscope-ai/HiClaw
- Homepage: https://hiclaw.io
- Primary language: Go
- Stars / forks at review: 4680 / 560
- Last pushed: 2026-05-27T16:43:43Z
- Latest release: v1.1.2
- License signal: Apache License 2.0
- Topics: agent-teams, openclaw

## Evidence checked

- README describes Manager-Workers architecture, multi-runtime collaboration, MinIO shared filesystem, Higress AI Gateway, Element/Tuwunel Matrix stack, and human-in-the-loop visibility.
- News section claims Kubernetes-native control plane, Hermes autonomous coding runtime, declarative resource management, worker templates, and MCP server management.
- `docs/declarative-resource-management.md` and `docs/architecture.md` were fetched as supporting architecture evidence.
- License is Apache-2.0; latest release v1.1.2 on 2026-05-27.

## Strengths

- Strong auditable-room metaphor for multi-agent collaboration.
- Explicit security/gateway/shared-filesystem design surfaces real operational concerns.
- Apache license and active release cadence.

## Risks / caveats

- Potentially way overbuilt for one-person local Hermes workflows.
- External services/containers increase setup and maintenance burden.
- Claims about Hermes worker support need hands-on verification.

## Integration ideas

- Steal “manager room + worker room + shared artifact folder + human interrupt” semantics for Hermes multi-agent jobs.
- Use Matrix-room architecture as reference if Discord thread UX becomes insufficient.

## Alternatives / related repos

- [paperclipai/paperclip](paperclipai--paperclip.md)
- [openclaw/openclaw](openclaw--openclaw.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [Agent Work Orchestration Repo Comparison](../comparisons/agent-work-orchestration.md)

## Review candidates and context

- Reference-only for now; distill transparent collaboration semantics into subagent/Kanban guidance.
