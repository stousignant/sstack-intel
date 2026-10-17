---
title: NateBJones-Projects/OB1
type: repo-intel
source: https://github.com/NateBJones-Projects/OB1
category: personal-knowledge-infra
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: FSL-1.1-MIT
---

# NateBJones-Projects/OB1

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `80/100` — Strong open-brain architecture reference — shared database, AI gateway, chat capture, MCP, and prompts — but overlaps directly with GBrain/second-brain.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Distill OB1’s source-neutral memory/gateway/channel architecture into Hermes/GBrain notes; do not migrate the canonical brain into Supabase unless a specific gap appears.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 22/25 | Directly maps to the existing stack's memory-ownership and integration boundaries. |
| Leverage | 20/25 | Can save time or sharpen agent work if bounded. |
| Reuse readiness | 13/20 | Evidence from README/root files/package/license. |
| Maturity/trust | 13/15 | Based on activity, docs, tests/security/license surface. |
| Differentiation | 12/15 | Distinctive pattern/tool relative to Hermes/GBrain/Obsidian. |

## Verdict

OB1 addresses the general requirement for durable knowledge shared across multiple AI clients. Where Obsidian/Git is the canonical vault, GBrain the index, and Hermes the runtime/interface, OB1 is an architecture comparator rather than a replacement. Its most useful comparisons are shared protocols, capture channels, and onboarding prompts.

## Reference-stack relevance

- Relevant to long-running Hermes/Codex workloads where less context waste, better retrieval, safer memory boundaries, or higher-quality repo/document ingestion are measurable needs.
- The key decision boundary is whether the repo is a **bounded sidecar** or a **new owner of memory/context**. Sidecars can be sandboxed; parallel truth stores should be pattern sources until they beat Hermes/GBrain/session_search.
- Evidence from this batch should feed concrete improvements to SStack, GBrain, Wikic, and repo-intelligence workflows rather than spawning another ungoverned tool layer.

## What it is

Open Brain — The infrastructure layer for your thinking. One database, one AI gateway, one chat channel — any AI plugs in. No middleware, no SaaS.

## Evidence checked

- GitHub metadata: stars `3551`, forks `676`, pushed `2026-06-02T12:52:48Z`, archived `False`.
- Topics: ai-agents, mcp, memory-layer, memory-layer-for-ai, open-brain, open-source, personal-knowledge, personal-knowledge-management, supabase.
- Inspected upstream repository: [source](https://github.com/NateBJones-Projects/OB1); capture location omitted.
- Files fetched: README.md, LICENSE.md, SECURITY.md, root-contents.json, recent-commits.json.

## Strengths

- Clear “one brain, many AIs” framing with MCP, AI gateway, Slack/chat capture, schemas, extensions, recipes, dashboards, and docs.
- Active repo with substantial community attention and recent commits.
- Security policy exists, and setup docs make it accessible for non-specialists.

## Risks / caveats

- FSL-1.1-MIT is source-available/future-MIT, not clean MIT today.
- Supabase/database-centered architecture would duplicate or compete with the canonical vault/GBrain stack.
- Security policy still had placeholder reporting contact text in fetched evidence.

## Integration ideas

- Treat as part of the **context-memory-brain** decision surface, not as an automatic install.
- If sandboxed, use copied/non-sensitive data first and record whether it improves quality/time/cost versus the existing Hermes/GBrain/Obsidian path.
- Extract reusable patterns into SStack skills or Wikic/GBrain design notes only after a bounded test proves the gap; keep executable follow-ups in the established issue tracker.

## Alternatives / related repos

- [Context / memory / brain tools comparison](../comparisons/context-memory-brain-tools.md)
- [oraios/serena](oraios--serena.md)
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md)
- [kytmanov/obsidian-llm-wiki-local](kytmanov--obsidian-llm-wiki-local.md)
- [garrytan/gbrain](garrytan--gbrain.md)

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
