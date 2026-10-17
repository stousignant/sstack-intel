---
title: Zie619/n8n-workflows
type: repo-intel
source: https://github.com/Zie619/n8n-workflows
category: automation-workflow-catalog
status: deep-analyzed
usefulness_score: 78
recommendation: reference-only
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# Zie619/n8n-workflows

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `78/100` — Large n8n workflow corpus and API/search app are useful automation inspiration, but workflows are credential-bearing templates that must be sanitized before reuse.
- Recommendation: `reference-only`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Use as an automation pattern catalog only; copy no workflows into live n8n without secret stripping and node-by-node review.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 20/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 20/25 | Potential to save time, improve autonomy, or increase optionality. |
| Reuse readiness | 15/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 12/15 | Maintenance, tests, license, security posture, and governance. |
| Differentiation | 11/15 | Unique value versus current stack and prior repo-intelligence notes. |

## Verdict

Large n8n workflow corpus and API/search app are useful automation inspiration, but workflows are credential-bearing templates that must be sanitized before reuse. Keep the boundary tight: use the durable pattern/catalog value, but do not add a competing runtime, memory store, or account-connected automation surface without a separate sandbox and security pass.

## Reference-stack relevance

- This review group covers orchestration, MCP discovery, memory, personal AI OS, automation workflows, prompt research, and agent operations UI patterns.
- MIT corpus of 4k+ workflows, Docker/API/search app, tests, security policy, workflow DB, docs/helm/k8s, and security-fix history.
- The useful output is mostly safer orchestration/catalog/UX patterns for Hermes/SStack rather than more global runtime installs.

## What it is

GitHub description: all of the workflows of n8n i could find (also from the site itself).

Metadata captured: `54945` stars, `7261` forks, last pushed `2026-05-31T14:09:36Z`, archived `False`, fork `False`, topics: none captured.

## Evidence checked

- GitHub metadata via `gh repo view Zie619/n8n-workflows`.
- README/root listing under a disposable source-inspection workspace.
- License/package/security/docker files when present in the evidence directory.
- Root files sampled: .devcontainer, .dockerignore, .env.example, .github, .gitignore, .playwright-mcp, .trivyignore, CLAUDE.md, CLAUDE_ZH.md, DELIVERY-SUMMARY.md, DEPLOYMENT.md, Dockerfile, LICENSE, README.md, SECURITY.md, ai-stack, api_server.py, context, docker-compose.dev.yml, docker-compose.prod.yml.

## Strengths

- MIT corpus of 4k+ workflows, Docker/API/search app, tests, security policy, workflow DB, docs/helm/k8s, and security-fix history.
- Recent activity, archive status, root structure, package/license/security files were checked where available.

## Risks / caveats

- Workflow supply-chain and credential exfiltration risk; many workflows may be stale or unsafe.
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

- Candidates above remain non-binding; execution state belongs to the established issue tracker.
