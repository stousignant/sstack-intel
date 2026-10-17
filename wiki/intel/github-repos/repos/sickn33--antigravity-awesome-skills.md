---
title: sickn33/antigravity-awesome-skills
type: repo-intel
source: https://github.com/sickn33/antigravity-awesome-skills
category: skill-catalog
status: deep-analyzed
usefulness_score: 76
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# sickn33/antigravity-awesome-skills

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `76/100` — Huge installable multi-harness skill catalog with CLI/bundles/schemas; valuable architecture/reference source but too broad to trust wholesale.
- **Recommendation:** `watch`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Inspect its catalog schema, installer safety model, and skill validation pipeline before considering any one skill; use as discovery queue only.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit against Hermes/SStack/GBrain/Claude/Codex skill needs. |
| Leverage | 20/25 | Can improve reusable workflows or skill curation. |
| Reuse readiness | 14/20 | Based on license, structure, docs, and install surface. |
| Maturity/trust | 12/15 | Based on activity, ownership, security policy, and catalog risk. |
| Differentiation | 10/15 | Unique skill/catalog pattern worth preserving. |

## Verdict

This repo is useful because it packages the shape of a modern skill registry: installable bundles, schemas, indexes, plugins, docs, and multi-harness targeting. Do not blindly install it: 1,494+ skills mean uneven quality and high prompt-supply-chain risk.

## Reference-stack relevance

- This repo belongs to the skill/prompt/library ecosystem that could improve SStack shared skills across Hermes, Claude Code, Codex, and future harnesses.
- The main question is not “can we install it?” but “what should become durable SStack skill policy, catalog shape, safety validation, or reusable workflow memory?”
- Bulk skill imports are dangerous. Prefer selective distillation, license checks, and sandboxed projection tests.

## What it is

Installable GitHub library of 1,494+ agentic skills for Claude Code, Cursor, Codex CLI, Gemini CLI, Antigravity, and more. Includes specialized plugins, installer CLI, bundles, workflows, and official/community skill collections.

## Evidence checked

- GitHub metadata: stars `39563`, forks `6413`, pushed `2026-06-03T07:43:52Z`, archived `False`.
- Topics: agentic-skills, ai-agents, antigravity, claude-code, mcp, ai-workflows, codex-cli, developer-tools, gemini-cli, skill-library, agent-skills, ai-agent-skills, antigravity-skills, claude-code-skills, codex-skills, cursor-skills, gemini-skills, ai-coding, cursor, kiro.
- Upstream evidence: https://github.com/sickn33/antigravity-awesome-skills; the following fetched files were inspected at review time.
- Files fetched: README.md, LICENSE, SECURITY.md, package.json, root-contents.json, recent-commits.json.

## Strengths

- MIT license, active updates, security policy, package/installer, schemas, `skills_index.json`, catalog, plugins, and docs.
- Targets Claude Code, Codex CLI, Gemini CLI, Cursor, Antigravity, OpenCode, and more — relevant to SStack cross-harness thinking.
- Good source for registry/installer/schema patterns.

## Risks / caveats

- Massive community skill surface creates prompt-injection/supply-chain risk.
- SEO/hype-heavy positioning; individual skills require review.
- Installer evaluation must not touch live skill directories without disposable sandboxing.

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

## Review guidance

- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
