---
title: nrslib/takt
type: repo-intel
source: https://github.com/nrslib/takt
category: agent-workflow-orchestration
status: deep-analyzed
usefulness_score: 88
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# nrslib/takt

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `88/100` — Best final-batch candidate: YAML-defined multi-agent coordination, review loops, guardrails, and provider roles for Claude/Codex/OpenCode/Cursor/GitHub Copilot/Kiro.
- Recommendation: `adopt-now`.
- **Usage observed 2026-06-03:** `not-used`.
- Review candidate: Run a no-secret sandbox on a toy repo with a tiny YAML workflow and compare its review-loop semantics against current Hermes/Codex delegation.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 22/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 22/25 | Potential to save time, improve autonomy, or increase optionality. |
| Reuse readiness | 17/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 13/15 | Maintenance, tests, license, security posture, and governance. |
| Differentiation | 14/15 | Unique value versus current stack and prior repo-intelligence notes. |

## Verdict

Best final-batch candidate: YAML-defined multi-agent coordination, review loops, guardrails, and provider roles for Claude/Codex/OpenCode/Cursor/GitHub Copilot/Kiro. Keep the boundary tight: use the durable pattern/catalog value, but do not add a competing runtime, memory store, or account-connected automation surface without a separate sandbox and security pass.

## Workload fit

- This review covers orchestration, MCP discovery, memory, personal AI OS, automation workflows, prompt research, and agent operations UI patterns.
- MIT package with CLI bin, tests/e2e, Docker, docs, builtins/tools, AGENTS/CLAUDE files, and explicit structured review/permission loops.
- The useful output is mostly safer orchestration/catalog/UX patterns for Hermes/SStack rather than more global runtime installs.

## What it is

GitHub description: TAKT Agent Koordination Topology - Define how AI agents coordinate, where humans intervene, and what gets recorded — in YAML.

Metadata captured: `1109` stars, `70` forks, last pushed `2026-06-03T14:47:46Z`, archived `False`, fork `False`, topics: agent-orchestration, ai-agents, claude-code, multi-agent, agent-team, codex, opencode.

## Evidence checked

- GitHub metadata via `gh repo view nrslib/takt`.
- [Upstream README/root listing](https://github.com/nrslib/takt) inspected.
- License/package/security/docker files when present in the upstream repository.
- Root files sampled: .coderabbit.yaml, .devcontainer, .dockerignore, .github, .gitignore, .npmignore, .takt, AGENTS.md, CHANGELOG.md, CLAUDE.md, CODE_OF_CONDUCT.md, CONTRIBUTING.md, Dockerfile, LICENSE, README.md, bin, builtins, docker-compose.yml, docs, e2e.

## Strengths

- MIT package with CLI bin, tests/e2e, Docker, docs, builtins/tools, AGENTS/CLAUDE files, and explicit structured review/permission loops.
- Recent activity, archive status, root structure, package/license/security files were checked where available.

## Risks / caveats

- Could become another orchestration layer; needs bounded toy workflow before adoption.
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
