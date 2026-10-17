---
title: lobehub/lobehub
type: repo-intel
source: https://github.com/lobehub/lobehub
category: agent-operations-platform
status: deep-analyzed
usefulness_score: 76
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: LobeHub-Community-License
---

# lobehub/lobehub

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- Usefulness score: `76/100` — Huge active agent-operations/chat platform with strong UI/plugin/multimodal patterns, but custom community license and platform breadth make it pattern-only for the reference stack.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Distill 24/7 agent-operator reporting/scheduling UI patterns only; do not adopt as a parallel Hermes runtime.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 20/25 | Potential to save time, improve autonomy, or increase optionality. |
| Reuse readiness | 15/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 12/15 | Maintenance, tests, license, security posture, and governance. |
| Differentiation | 9/15 | Unique value versus current stack and prior repo-intelligence notes. |

## Verdict

Huge active agent-operations/chat platform with strong UI/plugin/multimodal patterns, but custom community license and platform breadth make it pattern-only for the reference stack. Keep the boundary tight: use the durable pattern/catalog value, but do not add a competing runtime, memory store, or account-connected automation surface without a separate sandbox and security pass.

## Reference-stack relevance

- This review group covers orchestration, MCP discovery, memory, personal AI OS, automation workflows, prompt research, and agent operations UI patterns.
- Large active monorepo with apps/packages/docs/docker/security policy, tests/CI badges, agent/plugin/multimodal positioning, and massive ecosystem traction.
- The useful output is mostly safer orchestration/catalog/UX patterns for Hermes/SStack rather than more global runtime installs.

## What it is

GitHub description: 🤯 LobeHub is your Chief Agent Operator, organizing your agents into 7×24 operations by hiring, scheduling, and reporting on your entire AI team..

Metadata captured: `78134` stars, `15367` forks, last pushed `2026-06-03T14:53:21Z`, archived `False`, fork `False`, topics: chatgpt, openai, ai, gpt, claude, gemini, knowledge-base, deepseek, agent, mcp.

## Evidence checked

- GitHub metadata via `gh repo view lobehub/lobehub`.
- README/root listing under temporary upstream inspection material.
- License/package/security/docker files when present in the evidence directory.
- Root files sampled: .agents, .bunfig.toml, .changelogrc.cjs, .claude, .codex, .conductor, .console-log-whitelist.json, .cursor, .cursorindexingignore, .devcontainer, .dockerignore, .editorconfig, .env.desktop, .env.example, .env.example.development, .gitattributes, .githooks, .github, .gitignore, .i18nrc.js.

## Strengths

- Large active monorepo with apps/packages/docs/docker/security policy, tests/CI badges, agent/plugin/multimodal positioning, and massive ecosystem traction.
- Recent activity, archive status, root structure, package/license/security files were checked where available.

## Risks / caveats

- Custom license, SaaS/platform surface, env/provider complexity, and likely overlap with Hermes/GBrain.
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

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
