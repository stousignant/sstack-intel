---
title: punkpeye/awesome-mcp-servers
type: repo-intel
source: https://github.com/punkpeye/awesome-mcp-servers
category: mcp-catalog
status: deep-analyzed
usefulness_score: 82
recommendation: reference-only
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: MIT
---

# punkpeye/awesome-mcp-servers

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `82/100` — Strong MCP discovery directory, useful for sourcing server candidates, but every server remains untrusted until individually audited.
- Recommendation: `reference-only`.
- **Usage observed 2026-06-03:** `reference-only`.
- Review candidate: Use as a source map when selecting MCP servers; create per-server audit notes before installing any server with account/filesystem/browser access.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 22/25 | Fit with Hermes/GBrain/second-brain/SStack workflows. |
| Leverage | 22/25 | Potential to save time, improve autonomy, or increase optionality. |
| Reuse readiness | 17/20 | Installability, docs, examples, and integration cost. |
| Maturity/trust | 13/15 | Maintenance, tests, license, security posture, and governance. |
| Differentiation | 8/15 | Unique value versus current stack and prior repo-intelligence notes. |

## Verdict

Strong MCP discovery directory, useful for sourcing server candidates, but every server remains untrusted until individually audited. Keep the boundary tight: use the durable pattern/catalog value, but do not add a competing runtime, memory store, or account-connected automation surface without a separate sandbox and security pass.

## Reference-stack relevance

- This review covers orchestration, MCP discovery, memory, personal AI OS, automation workflows, prompt research, and agent operations UI patterns.
- MIT, massive maintained multilingual MCP server list with clients/tutorials/community and Glama directory tie-in.
- The useful output is mostly safer orchestration/catalog/UX patterns for Hermes/SStack rather than more global runtime installs.

## What it is

GitHub description: A collection of MCP servers..

Metadata captured: `88439` stars, `11061` forks, last pushed `2026-05-27T05:34:55Z`, archived `False`, fork `False`, topics: ai, mcp.

## Evidence checked

- GitHub metadata via `gh repo view punkpeye/awesome-mcp-servers`.
- [Upstream README/root listing](https://github.com/punkpeye/awesome-mcp-servers) inspected.
- License/package/security/docker files when present in the upstream repository.
- Root files sampled: .github, CONTRIBUTING.md, LICENSE, README-fa-ir.md, README-ja.md, README-ko.md, README-pt_BR.md, README-th.md, README-zh.md, README-zh_TW.md, README.md.

## Strengths

- MIT, massive maintained multilingual MCP server list with clients/tutorials/community and Glama directory tie-in.
- Recent activity, archive status, root structure, package/license/security files were checked where available.

## Risks / caveats

- Catalog supply-chain risk; MCP servers can expose dangerous account/filesystem tools.
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
