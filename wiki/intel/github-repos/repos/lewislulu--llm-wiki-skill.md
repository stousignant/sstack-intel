---
title: lewislulu/llm-wiki-skill
type: repo-intel
source: https://github.com/lewislulu/llm-wiki-skill
category: llm-wiki
updated: 2026-06-07
tags:
  - llm-wiki
  - github-repos
  - tool-intel
  - agent-skills
  - openclaw
  - codex
  - audit-loop
topic: llm-wiki
role: repo-card
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: medium
last_reviewed: 2026-06-03
license: NOASSERTION
---

# lewislulu/llm-wiki-skill

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

> Topic hub: [LLM-wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md)

## Decision

- **Usefulness score:** `80/100` — Compact OpenClaw/Codex skill implementation of Karpathy-style compiled LLM wikis with Obsidian/browser audit feedback loops.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `pattern-in-use`.
- **Review candidate:** Distill its audit-file/feedback-loop shape into GBrain/Wikic/wiki compiler ideas; avoid installing the skill wholesale until license and parser robustness are verified.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 23/25 | Directly maps to reference-stack boundaries. |
| Leverage | 20/25 | Can save time or sharpen agent work if bounded. |
| Reuse readiness | 12/20 | Evidence from README/root files/package/license. |
| Maturity/trust | 10/15 | Based on activity, docs, tests/security/license surface. |
| Differentiation | 15/15 | Distinctive pattern/tool relative to Hermes/GBrain/Obsidian. |

## Verdict

This repo is directly aligned with the reference stack’s existing LLM-wiki/GBrain direction. The value is not “install another wiki skill”; it is the concrete skill packaging and audit feedback loop: Obsidian comment → anchored audit Markdown → web preview → richer compiled wiki. License and maturity are weak, so keep it as a pattern source.

## Workload fit

- Fits the current push toward better long-running Hermes/Codex work: less context waste, better retrieval, safer memory boundaries, and higher-quality repo/document ingestion.
- The key decision boundary is whether the repo is a **bounded sidecar** or a **new owner of memory/context**. Sidecars can be sandboxed; parallel truth stores should be pattern sources until they beat Hermes/GBrain/session_search.
- Evidence from this batch should feed concrete improvements to SStack, GBrain, Wikic, and repo-intelligence workflows rather than spawning another ungoverned tool layer.

## What it is

Karpathy-style LLM knowledge base Agent Skill for OpenClaw/Codex. Experimental — will iterate over time.

## Evidence checked

- GitHub metadata: stars `569`, forks `99`, pushed `2026-04-16T06:01:13Z`, archived `False`.
- Topics: none.
- Local evidence cache: temporary upstream inspection material.
- Files fetched: README.md, root-contents.json, recent-commits.json.

## Strengths

- Directly implements the compile/ingest/query/lint/audit loop for persistent cross-linked Markdown knowledge bases.
- Includes companion Obsidian audit plugin, browser preview server, and shared TypeScript audit schema.
- Small enough to mine for Wikic/GBrain feedback-loop patterns.

## Risks / caveats

- No license file found in fetched evidence.
- Experimental and had recent YAML parse fix, so robustness needs verification.
- Could create skill/process sprawl if copied into Hermes rather than distilled.

## Integration ideas

- Treat as part of the **context-memory-brain** decision surface, not as an automatic install.
- If sandboxed, use copied/non-sensitive data first and record whether it improves quality/time/cost versus the existing Hermes/GBrain/Obsidian path.
- Extract reusable patterns into SStack skills or Wikic/GBrain design notes; keep executable follow-ups in the established issue tracker only after a bounded test proves the gap.

## Alternatives / related repos

- [Context / memory / brain tools comparison](../comparisons/context-memory-brain-tools.md)
- [oraios/serena](oraios--serena.md)
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md)
- [kytmanov/obsidian-llm-wiki-local](kytmanov--obsidian-llm-wiki-local.md)
- [garrytan/gbrain](garrytan--gbrain.md)

## Review candidates and context

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
