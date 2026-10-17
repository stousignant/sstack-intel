---
title: tinyhumansai/openhuman
type: repo-intel
source: https://github.com/tinyhumansai/openhuman
category: personal-ai-os
status: deep-analyzed
usefulness_score: 72
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: GPL-3.0
---

# tinyhumansai/openhuman

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `72/100` — Ambitious private personal AI harness with desktop/app/core/server evidence, but GPL and broad personal-data scope make it watch/pattern-only.
- Recommendation: `watch`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Watch personal-AI UX/privacy architecture; do not ingest personal data or run as a competing PAI/Hermes system.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 18/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 18/25 | Potential to save time, improve autonomy, or increase optionality. |
| Reuse readiness | 14/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 10/15 | Maintenance, tests, license, security posture, and governance. |
| Differentiation | 12/15 | Unique value versus current stack and prior repo-intelligence notes. |

## Verdict

Ambitious private personal AI harness with desktop/app/core/server evidence, but GPL and broad personal-data scope make it watch/pattern-only. Keep the boundary tight: use the durable pattern/catalog value, but do not add a competing runtime, memory store, or account-connected automation surface without a separate sandbox and security pass.

## Reference-stack relevance

- This review covers orchestration, MCP discovery, memory, personal AI OS, automation workflows, prompt research, and agent operations UI patterns.
- Active Rust/Node/Tauri-style monorepo with Docker, tests/e2e, docs, app/packages/src, security policy, and multilingual READMEs.
- The useful output is mostly safer orchestration/catalog/UX patterns for Hermes/SStack rather than more global runtime installs.

## What it is

GitHub description: Your Personal AI super intelligence. Private, Simple and extremely powerful..

Metadata captured: `30564` stars, `2936` forks, last pushed `2026-06-03T13:10:54Z`, archived `False`, fork `False`, topics: none captured.

## Evidence checked

- GitHub metadata via `gh repo view tinyhumansai/openhuman`.
- [Upstream README/root listing](https://github.com/tinyhumansai/openhuman) inspected.
- License/package/security/docker files when present in the upstream repository.
- Root files sampled: .agents, .claude, .codex, .do, .dockerignore, .env.example, .fly, .gitattributes, .github, .gitignore, .gitmodules, .husky, .vscode, AGENTS.md, CLAUDE.md, CODEX_WORKPAD.md, CODE_OF_CONDUCT.md, CONTRIBUTING-BEGINNERS.md, CONTRIBUTING.md, Cargo.lock.

## Strengths

- Active Rust/Node/Tauri-style monorepo with Docker, tests/e2e, docs, app/packages/src, security policy, and multilingual READMEs.
- Recent activity, archive status, root structure, package/license/security files were checked where available.

## Risks / caveats

- GPL, huge personal-data/control surface, hype-heavy positioning, and overlap with PAI/Hermes.
- Treat README claims and star counts as weak evidence unless matched by files, tests, package manifests, or a local sandbox.
- Do not connect secrets, provider accounts, financial accounts, personal data, browser sessions, or production files during repo-intelligence evaluation.

## Integration ideas

- Route orchestration ideas into Hermes/SStack delegation semantics: owner, role, review loop, evidence bundle, rollback, and heartbeat.
- Treat MCP and workflow catalogs as sourcing maps that require individual security review before installation.
- Treat memory/personal-AI systems as bakeoff candidates only when existing Hermes/GBrain/session_search boundaries fail a concrete task.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [Final Orchestration / Memory / Automation Stars Comparison](../comparisons/final-orchestration-memory-automation-stars.md)

## Review guidance

- Candidates above are evaluation guidance, not executable commitments or runtime adoption.
