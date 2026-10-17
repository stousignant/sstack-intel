---
title: Cranot/claude-code-guide
type: repo-intel
source: https://github.com/Cranot/claude-code-guide
category: tool-guide
status: deep-analyzed
usefulness_score: 74
recommendation: reference-only
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: NOASSERTION
---

# Cranot/claude-code-guide

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `74/100` — Auto-updated Claude Code guide that labels official/community/experimental material; useful documentation aggregator, not a skill source.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Use as a quick Claude Code reference when designing work-safe Claude lanes; prefer official docs for final claims.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 18/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 18/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 13/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 12/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 13/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

This is useful as a living map of Claude Code concepts, commands, MCP, settings, SDK, and changelog pointers. It is not something to install or quote as authority. Its best feature is source labeling: official vs community vs experimental.

## Reference-stack relevance

- This repo belongs to the skill/prompt/library ecosystem that could improve SStack shared skills across Hermes, Claude Code, Codex, and future harnesses.
- The main question is not “can we install it?” but “what should become durable SStack skill policy, catalog shape, safety validation, or reusable workflow memory?”
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

The Complete Claude Code CLI Guide - Live & Auto-Updated Every 2 Days

## Evidence checked

- GitHub metadata: stars `2789`, forks `316`, pushed `2026-02-14T10:24:23Z`, archived `False`.
- Topics: none.
- Inspected upstream repository: [source](https://github.com/Cranot/claude-code-guide); capture location omitted.
- Files fetched: README.md, root-contents.json, recent-commits.json.

## Strengths

- Auto-updated from official docs/releases/changelog and explicitly labels source confidence.
- Optimized for humans and AI agents, useful as an orientation layer.
- Good reference for Claude Code work-safe harness decisions.

## Risks / caveats

- No license file detected in fetched evidence.
- Last push in fetched evidence was February 2026; auto-update status should be verified before relying on it.
- Community/experimental content needs official-source verification.

## Integration ideas

- Use as a source of candidate patterns for SStack shared skills, not as an automatic install target.
- Any skill or prompt copied into SStack needs license review, runtime-neutral rewriting, support-file projection checks, and safety-scan/doctor validation.
- Prefer building a small curated SStack skill recommendation flow over bulk importing thousands of community skills.

## Alternatives / related repos

- [Skills / prompt libraries comparison](../comparisons/skills-prompt-libraries.md)
- [microsoft/skills](microsoft--skills.md)
- [google/skills](google--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)
- [steipete/agent-scripts](steipete--agent-scripts.md)

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
