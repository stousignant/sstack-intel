---
title: NeoVertex1/nuggets
type: repo-intel
source: https://github.com/NeoVertex1/nuggets
category: memory-management
status: deep-analyzed
usefulness_score: 79
recommendation: watch
usage: not-used
score_confidence: medium
last_reviewed: 2026-06-03
license: NOASSERTION
---

# NeoVertex1/nuggets

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `79/100` — Directly relevant memory-plugin/MCP idea for Hermes/Claude/Codex, but duplicates existing Hermes memory/GBrain/session_search boundaries and needs bakeoff before use.
- Recommendation: `watch`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: If memory recall feels weak, run a narrow copied-data bakeoff versus Hermes memory + GBrain + session_search; do not add another memory store by default.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 20/25 | Potential to save time, improve autonomy, or increase optionality. |
| Reuse readiness | 15/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 12/15 | Maintenance, tests, license, security posture, and governance. |
| Differentiation | 12/15 | Unique value versus current stack and prior repo-intelligence notes. |

## Verdict

Directly relevant memory-plugin/MCP idea for Hermes/Claude/Codex, but duplicates existing Hermes memory/GBrain/session_search boundaries and needs bakeoff before use. Keep the boundary tight: use the durable pattern/catalog value, but do not add a competing runtime, memory store, or account-connected automation surface without a separate sandbox and security pass.

## Workload fit

- This review group covers orchestration, MCP discovery, memory, personal AI OS, automation workflows, prompt research, and agent operations UI patterns.
- Personal assistant with gateway/tests/package evidence and explicit nuggets-memory-plugin MCP support for Hermes, Claude Code, and Codex.
- The useful output is mostly safer orchestration/catalog/UX patterns for Hermes/SStack rather than more global runtime installs.

## What it is

GitHub description: First AI assistant with holographic memory.

Metadata captured: `388` stars, `20` forks, last pushed `2026-04-15T02:15:44Z`, archived `False`, fork `False`, topics: none captured.

## Evidence checked

- GitHub metadata via `gh repo view NeoVertex1/nuggets`.
- README/root listing under [upstream repository inspection](https://github.com/NeoVertex1/nuggets).
- License/package/security/docker files when present in the evidence directory.
- Root files sampled: .env.example, .github, .gitignore, .pi, CLAUDE.md, NUGGETS_INSTRUCTIONS.md, README.md, blog, gateway, images, package-lock.json, package.json, src, tests, tsconfig.json.

## Strengths

- Personal assistant with gateway/tests/package evidence and explicit nuggets-memory-plugin MCP support for Hermes, Claude Code, and Codex.
- Recent activity, archive status, root structure, package/license/security files were checked where available.

## Risks / caveats

- No license captured; “holographic memory” claims need verification; high risk of memory-store duplication.
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

## Review candidates and context

- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
