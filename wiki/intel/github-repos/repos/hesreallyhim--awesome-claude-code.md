---
title: "hesreallyhim/awesome-claude-code"
type: repo-intel
source: https://github.com/hesreallyhim/awesome-claude-code
category: coding-tools
status: deep-analyzed
usefulness_score: 78
recommendation: reference-only
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: CC-BY-NC-ND-4.0
---

# hesreallyhim/awesome-claude-code

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision
- Usefulness score: `[('Stack fit', 18, 25, 'Useful Claude Code map, but not Hermes-native.'), ('Leverage', 18, 25, 'Good discovery leverage, weak direct execution leverage.'), ('Reuse readiness', 16, 20, 'Easy to browse; structured data exists.'), ('Maturity/trust', 13, 15, 'Large, maintained, tested catalog.'), ('Differentiation', 13, 15, 'Best broad Claude Code catalog, but catalog-only.')]/100` — This is a high-signal catalog of the Claude Code ecosystem, not a dependency.
- Recommendation: `reference-only`.
- **Usage observed 2026-05-30:** `not-used`.
- Review candidate: Use it as a discovery index only; do not copy/adapt its curated text into SStack/second-brain artifacts because the license is non-commercial/no-derivatives.

## Scorecard
| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 18/25 | Useful Claude Code map, but not Hermes-native. |
| Leverage | 18/25 | Good discovery leverage, weak direct execution leverage. |
| Reuse readiness | 16/20 | Easy to browse; structured data exists. |
| Maturity/trust | 13/15 | Large, maintained, tested catalog. |
| Differentiation | 13/15 | Best broad Claude Code catalog, but catalog-only. |

## Verdict

This is a high-signal catalog of the Claude Code ecosystem, not a dependency. Its value is discovery: use it to find tools, hooks, skills, and orchestrators to analyze individually. The CC BY-NC-ND license makes it unsuitable for remixing into portable cross-agent infrastructure docs.

## Workload fit
- Gives a map of Claude Code extensions and adjacent tools to compare against Hermes/Codex lanes.
- Good seed list for future focused repo-intelligence batches.
- The data/tools layout suggests maintaining a curated machine-readable resources table may be more useful than prose bookmarks.

## What it is

A curated awesome-list for Claude Code resources: skills, agents, hooks, status lines, orchestrators, developer tooling, and plugins. It includes Python tooling, resource data, templates, and tests.

## Evidence checked
- GitHub metadata via `gh repo view` on 2026-05-30: stars `45223`, forks `3922`, primary language `Python`, archived `False`, fork `False`.
- Maintenance signal: pushed `2026-04-27T14:40:18Z`, updated `2026-05-30T22:56:30Z`, latest release `none detected` ``.
- License: `CC-BY-NC-ND-4.0` from GitHub/license file.
- README: `https://raw.githubusercontent.com/hesreallyhim/awesome-claude-code/main/README.md`.
- Top-level manifests/docs inspected locally under temporary upstream inspection material: README, package/pyproject when present, license, security file when present, top-level contents.
- Repository topics: anthropic, anthropic-claude, awesome, awesome-list, awesome-lists, awesome-resources, claude, claude-code, agentic-code, agentic-coding, ai-workflow-optimization, ai-workflows.

## Strengths
- Huge ecosystem signal: ~45k stars / 3.9k forks; pushed 2026-04-27.
- Has structured repository assets: `THE_RESOURCES_TABLE.csv`, an upstream resources directory, `data/`, scripts, docs, tests, and Python packaging.
- Useful discovery surface for future Claude Code / coding-agent batches.

## Risks / caveats
- License is Creative Commons Attribution-NonCommercial-NoDerivatives 4.0, despite GitHub showing “Other”; this blocks remixing/adaptation.
- Awesome lists age quickly and can reward popularity over operational fit.
- Direct-install value is low; decision-making benefits more from evaluated tools than from another bookmark pile.

## Integration ideas
- Use as a source queue, then analyze candidate repos from primary sources.
- If building a cross-agent resource catalog, use original decision records with source links rather than derivative copies.

## Alternatives / related repos
- [Claude Code Ecosystem Comparison](../comparisons/claude-code-ecosystem.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [oraios/serena](oraios--serena.md)
- [microsoft/skills](microsoft--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)

## Review candidates and context
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.

## Score breakdown

| Dimension | Score | Max | Note |
|---|---:|---:|---|
| Stack fit | 18 | 25 | Useful Claude Code map, but not Hermes-native. |
| Leverage | 18 | 25 | Good discovery leverage, weak direct execution leverage. |
| Reuse readiness | 16 | 20 | Easy to browse; structured data exists. |
| Maturity/trust | 13 | 15 | Large, maintained, tested catalog. |
| Differentiation | 13 | 15 | Best broad Claude Code catalog, but catalog-only. |
