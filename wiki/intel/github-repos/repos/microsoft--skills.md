---
title: microsoft/skills
type: repo-intel
aliases:
  - GitHub repo: microsoft/skills
source: https://github.com/microsoft/skills
category: agent-skills
topics: [github-repo, agent-skills, hermes-skills, skillpacks]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-26
license: MIT
---

# microsoft/skills

> Reference-stack fit as reviewed 2026-05-26; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `84/100` — Best enterprise-scale skillpack reference: selective loading, cross-agent config, MCP/server bundles, AGENTS templates, and test harnesses; strongest as a pattern source, not as a direct dependency unless the operator is doing Azure work.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-26:** `reference-only`.
- **Review candidate:** Distill the useful skill-design patterns into Hermes skill authoring/review conventions; do not bulk-import the catalog.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22 | Strong Hermes skillpack architecture reference; direct content mostly Azure-specific. |
| Leverage | 21 | Selective skill loading, MCP configs, tests, and cross-agent setup directly inform Hermes skill operations. |
| Reuse readiness | 18 | Install/clone flow is clear; adopting individual skills is easy, adopting whole catalog would cause context rot. |
| Maturity/trust | 14 | MIT, Microsoft-backed, pushed 2026-05-25, security policy enabled. |
| Differentiation | 9 | Differentiates through enterprise scale and test harness, less through reference-workflow-specific domains. |

## Verdict

Treat `microsoft/skills` as the strongest **large-scale skillpack operating reference** in this batch. Its main value is not the Azure content itself; it is the distribution shape: selectively installed skills, cross-agent symlinks, MCP configs, AGENTS templates, and per-skill testing. Use it to improve Hermes skillpack conventions; avoid dumping the whole catalog into context.

## Workload fit

- Agent workflows benefit from skills that are selectively loaded, auditable, safe, and validated against intended tasks.
- This repo belongs to the **agent-skill ecosystem** category: useful less as another app to run, more as evidence for how skill libraries should be designed, validated, distributed, and secured.
- The immediate stack target is Hermes skill quality, not a new parallel skill runtime.

## What it is

A Microsoft-backed catalog of agent skills, MCP server configs, custom agents, and AGENTS.md templates mainly for SDKs, Azure services, AI Foundry, and language-specific development contexts.

## Live metadata checked

| Field | Value |
|---|---|
| GitHub URL | https://github.com/microsoft/skills |
| Description | Skills, MCP servers, Custom Agents, Agents.md for SDKs to ground Coding Agents |
| Stars / forks | 2386 / 267 |
| Primary language | TypeScript |
| Last push | 2026-05-25T12:08:55Z |
| Archived? | False |
| License | MIT |
| Security policy | https://github.com/microsoft/skills/security/policy |

## Evidence checked

- GitHub metadata via `gh repo view microsoft/skills` on 2026-05-26.
- README fetched via GitHub API into temporary upstream inspection material.
- Top-level repository contents fetched via GitHub API into the captured upstream metadata snapshot.
- Existing migrated repo note in `wiki/intel/github-repos/repos/microsoft--skills.md`.
- README headings/features inspected for install, test, security, and workflow claims.

## Strengths

- Large real-world catalog with Microsoft-backed maintenance.
- Clear warnings against loading everything at once — good context-rot discipline.
- Includes testing guidance and cross-agent installation patterns.
- MIT license and active 2026 maintenance.

## Risks / caveats

- Most concrete skills are Azure/Microsoft-specific; not all should enter Hermes.
- Bulk importing would recreate context rot.
- Need to inspect individual skills before trusting them.

## Integration ideas

- Steal the catalog/testing structure for Hermes skillpack QA.
- Mirror the anti-context-rot rule in Hermes skill authoring: load one relevant skill, not the universe.
- Compare Microsoft skill manifest/testing patterns against `hermes-agent-skill-authoring`.

## Alternatives / related repos

- [microsoft/skills](microsoft--skills.md)
- [google/skills](google--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)
- [cisco-ai-defense/skill-scanner](cisco-ai-defense--skill-scanner.md)
- [mgechev/skills-best-practices](mgechev--skills-best-practices.md)
- [Agent Skills Ecosystem Comparison](../comparisons/agent-skills-ecosystem.md)

## Review candidates and context

- Distill useful conventions into Hermes skill authoring/review guidance when working on skills.
- No standalone install action unless a concrete project needs this repo's domain-specific content.
