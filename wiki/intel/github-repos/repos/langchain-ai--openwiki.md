---
title: langchain-ai/openwiki
type: repo-intel
aliases:
  - OpenWiki
  - GitHub repo: langchain-ai/openwiki
source: https://github.com/langchain-ai/openwiki
category: codebase-documentation
topics: [github-repo, codebase-documentation, agent-docs, llm-wiki, okf, langchain]
status: deep-analyzed
usefulness_score: 76
recommendation: defer
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-09-07
license: MIT
---

# langchain-ai/openwiki

> Reference-stack fit as reviewed 2026-09-07; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `76/100` — a mature and differentiated agent-doc generator, but it solves a secondary repo-documentation problem rather than the reference stack's OKF interoperability need.
- **Recommendation:** `defer` — do not adopt personal mode, do not integrate it with the canonical second-brain, and do not build a wrapper without a concrete repo-documentation pain point.
- **Usage observed 2026-09-07:** `pattern-in-use`. Sandbox-first, credential-scrub and review-gated patterns, not use of the upstream runtime.
- **Confidence:** `high`
- **Revisit trigger:** a repo repeatedly costs agents time to understand despite maintained `AGENTS.md`, skills, and repo docs. At that point, benchmark OpenWiki code mode in a disposable worktree before considering adoption.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 17/25 | Code-mode documentation can complement Hermes/SStack, but personal mode would duplicate the canonical second-brain/GBrain stack. |
| Leverage | 16/25 | Incremental source-grounded repo docs could reduce repeated exploration, but no current repo-doc bottleneck justifies another maintained runtime. |
| Reuse readiness | 17/20 | Released CLI, multiple provider/auth options, coding-agent integrations, resumable jobs, visualizer, and PR automation. Safe use still needs sandboxing and review. |
| Maturity/trust | 14/15 | MIT, LangChain-owned, active development, v0.5.0 release, substantial adoption, and stronger validation than the original v0.0.1 review. |
| Differentiation | 12/15 | Claim-level source grounding and incremental wiki maintenance are distinctive; OKF output alone is no longer a reason to adopt because Wikic checks this vault against OKF v0.2. |
| **Total** | **76/100** | Strong external reference and conditional benchmark candidate, not a current adoption target. |

## Verdict

OpenWiki is an LLM-powered **wiki generator and maintainer** that emits OKF; it is not merely an OKF compatibility tool. Its defensible fit for the reference stack is narrowly **code mode**: generate and incrementally maintain repo-local agent documentation with claim-level source evidence, then surface changes through reviewable PRs. Its **personal mode** would create another knowledge writer/store beside the canonical second-brain, Wikic, and GBrain and should not be adopted.

The recent second-brain/Wikic OKF work removes the original interoperability motivation for trying OpenWiki. Wikic validates the normative OKF v0.2 document rules and separately applies this vault's configured `vault_policy` taxonomy, provenance, field, and export-shape rules. OpenWiki is not needed to keep the vault governable or OKF-oriented.

Default disposition: preserve useful patterns and run no sandbox until a concrete repo-documentation problem makes the benchmark worth its model cost, content egress, and review burden.

## What it is

OpenWiki is a TypeScript CLI built on LangChain/Deep Agents with two modes:

- **Code mode:** generates and maintains an `openwiki/` Markdown wiki from a repository. It tracks per-page jobs, source-grounded Claims, update state, provenance, and OKF metadata; it can run through coding-agent integrations or CI-created documentation PRs.
- **Personal mode:** creates a separate personal wiki from repositories and connectors such as Gmail, Notion, Slack, Hacker News, web search, and X/Twitter.

Both modes emit Open Knowledge Format v0.2 bundles. OpenWiki also provides a local graph/Markdown visualizer and static export.

## OpenWiki versus authored-vault validation

| Concern | Wikic + second-brain | OpenWiki |
|---|---|---|
| Canonical role | Validates the reference stack's authored canonical vault | Generates and maintains a separate wiki artifact |
| Core operation | Deterministic, non-mutating readiness checks | Model-backed knowledge generation and updates |
| OKF relationship | Local compatibility/export-readiness profile | Emits OKF v0.2 bundles |
| Provenance | Checks required local provenance presence/shape | Produces generation, verification, source, and Claims metadata |
| Repo documentation | Existing authored repo docs and agent instructions | Generates `openwiki/` pages from repository evidence |
| Personal knowledge | Second-brain remains canonical; GBrain indexes it | Personal mode would duplicate ownership and ingestion |

Clean complementary use, if ever justified:

> OpenWiki code mode generates candidate repo-local docs in a disposable worktree → review the diff → retain selected repo docs or curate durable insights into second-brain → Wikic validates canonical vault pages with `--profile vault-policy` → GBrain indexes them downstream.

## Evidence checked

- Repository: [langchain-ai/openwiki](https://github.com/langchain-ai/openwiki) — 16,200 stars, 1,171 forks, MIT, pushed 2026-09-07.
- Release: [v0.5.0](https://github.com/langchain-ai/openwiki/releases/tag/v0.5.0), published 2026-09-01.
- Official documentation: [overview](https://docs.langchain.com/oss/openwiki/overview), [code mode](https://docs.langchain.com/oss/openwiki/code-mode), and [personal mode](https://docs.langchain.com/oss/openwiki/personal-mode).
- Current README/source contract: two modes, resumable page jobs, grounded Claims, coding-agent integrations, CI update workflows, visualizer/static export, OKF v0.2 output, and ChatGPT/Codex OAuth plus GitHub Copilot authentication.
- Reference validation distinction: Wikic's `doctor` and `summary` check OKF v0.2 plus separately configured vault policy; validation is not generation or model-output attestation.
- Historical local test: OpenWiki v0.0.1 `--help` and source build/lint/format checks succeeded; the model-backed documentation run did not complete, so no generated-output quality claim is carried forward.

## Strengths

- Generates durable, agent-readable repository documentation rather than burying repo understanding in chat transcripts.
- Tracks material claims with source evidence and can detect stale evidence as code changes.
- Supports resumable per-page generation and incremental updates instead of unconditional full rewrites.
- Offers review-gated CI/PR patterns and coding-agent integrations for Codex, Claude, OpenCode, and Cursor.
- Emits portable OKF v0.2 Markdown bundles with provenance and validation metadata.
- Supports ChatGPT/Codex subscription login and GitHub CLI/Copilot authentication, removing the original OpenRouter-only blocker.

## Risks / caveats

- Personal mode would duplicate the second-brain/GBrain ingestion and canonical-knowledge boundary.
- Model-backed generation adds nondeterminism, content egress, cost, and continuing review burden.
- Code mode manages root `AGENTS.md` and `CLAUDE.md`; disabling this remains unresolved in [issue #556](https://github.com/langchain-ai/openwiki/issues/556), and [PR #557](https://github.com/langchain-ai/openwiki/pull/557) is open and conflicting.
- Scoped updates can restructure unrelated wiki pages ([issue #797](https://github.com/langchain-ai/openwiki/issues/797)).
- The update planner may receive changed paths without commit intent, weakening semantic update accuracy ([issue #822](https://github.com/langchain-ai/openwiki/issues/822)).
- Provider credentials/config can be stored under the per-user OpenWiki credential/config directory; canonical or sensitive repositories still require a credential-scrubbed disposable worktree and explicit provider/privacy review.
- Wikic's OKF checks validate the normative v0.2 document rules; the separate `vault-policy` profile enforces the reference stack's local governance contract. Neither means Wikic generates OpenWiki's claim or attestation metadata.

## Patterns retained in SStack

- Disposable copy/worktree before any model-backed repo-doc run.
- Credential and runtime-state scrub before content egress.
- Version-pinned, explicitly recorded tool/provider/model configuration.
- Review generated `openwiki/` pages and all instruction-file mutations.
- Produce candidate diffs/PRs, never silent direct changes to canonical repositories.
- Adopt one active canonical knowledge stack; treat alternative wiki runtimes as pattern sources unless a bounded benchmark proves clear incremental value.

## Alternatives / related repos

- [atomicstrata/llm-wiki-compiler](atomicstrata--llm-wiki-compiler.md) — bounded compiler/review-mode precedent for local Markdown inputs.
- [kytmanov/obsidian-llm-wiki-local](kytmanov--obsidian-llm-wiki-local.md) — Obsidian/local-first LLM Wiki candidate with review-state patterns.
- [nashsu/llm_wiki](nashsu--llm_wiki.md) — deeper conceptual LLM Wiki implementation, but not a replacement for the canonical vault.
- [AsyncFuncAI/deepwiki-open](AsyncFuncAI--deepwiki-open.md) — heavier repo-to-wiki product benchmark.
- [langchain-ai/langgraph](langchain-ai--langgraph.md) — related LangChain substrate evaluated separately for bounded workflows.

## Follow-up disposition

No standing implementation action. Revisit only when a named repository has measurable recurring documentation/reconnaissance pain. Any future evaluation should be a new, narrow code-mode benchmark rather than a broad personal-wiki or OKF-adoption project.
