---
title: CodeGraphContext/CodeGraphContext
type: repo-intel
aliases:
  - CodeGraphContext
  - CGC
  - GitHub repo: CodeGraphContext/CodeGraphContext
source: https://github.com/CodeGraphContext/CodeGraphContext
category: code-intelligence
topics: [github-repo, mcp, codegraph, static-analysis, coding-agents]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-27
license: MIT
---

# CodeGraphContext/CodeGraphContext

> Reference-stack evaluation as reviewed 2026-05-27. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — strong code-graph/MCP reference, but less immediately obvious than Serena because GBrain already provides structural code graph tools locally.
- **Recommendation:** `distill-pattern`; sandbox only if we need a separate live graph DB for code analysis.
- **Usage observed 2026-05-27:** `not-used`.
- **Review candidate:** compare against GBrain code graph APIs before installing as another persistent index.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | MCP + CLI code graph maps to Hermes, but overlaps with GBrain code indexing. |
| Leverage | 21/25 | Could help large-codebase navigation and visualization. |
| Reuse readiness | 17/20 | `pip install codegraphcontext`, CLI, MCP wizard, embedded DB options, docs/tests. |
| Maturity/trust | 13/15 | MIT, active release, tests, community files; development status is still Alpha in `pyproject.toml`. |
| Differentiation | 12/15 | Database-backed graph and visual reports are useful; less differentiated where GBrain already has call graph tools. |

## Verdict

CodeGraphContext is worth keeping as a **pattern/reference** for code graph tooling and may be a sandbox candidate for visualization/reporting. An existing GBrain code-index/query layer already provides structural code search, so adoption should depend on a demonstrated capability gap. Compare CGC's persistent graph DB, multi-DB backends, report/visualization, and MCP server with GBrain's native `code_def`, `code_callers`, `code_flow`, and `code_refs` tools.

## Workload fit

- Helps answer “what should a code-aware Hermes know about a repo?” with concrete graph-backed commands.
- Could provide visual reports and dead-code/complexity analysis around Hermes/GBrain repos.
- Provides implementation patterns for bundled indexed repos and MCP exposure of graph queries.

## What it is

CodeGraphContext is a Python CLI + MCP server that indexes local code into a graph database. It extracts symbols and relationships from multiple languages, then supports queries for callers/callees, complexity, dead code, call chains, and graph visualization.

## Evidence checked

- Live GitHub metadata via `gh repo view` on 2026-05-27: 3,453 stars, 601 forks, MIT, Python, latest release `v0.4.7` on 2026-05-07, pushed 2026-05-27.
- README inspected: features, supported languages, DB backends, SCIP indexing, CLI/MCP quickstart, ignore file, MCP client config.
- `pyproject.toml` inspected: package `codegraphcontext` version `0.4.12`, Python `>=3.10`, development status Alpha, Typer/Rich/FastAPI/Neo4j/Falkor/Kuzu/Ladybug dependencies, test config.
- Local bounded smoke test: `uvx --from codegraphcontext codegraphcontext --help` (using a disposable cache) succeeded and listed commands including `doctor`, `index`, `stats`, `report`, `visualize`, `mcp`, `find`, `analyze`, `bundle`, and `datasource`.

## Strengths

- Broad static code graph feature set with 20 language parsers and optional SCIP indexing.
- Multiple graph backends: embedded Kuzu/Ladybug/FalkorDB Lite and external Neo4j/Nornic-style setups.
- Agent and human surfaces: standalone CLI, MCP server, reports, graph visualization, watch mode.
- Good direct smoke-test result; CLI is installable and starts.

## Risks / caveats

- Overlaps heavily with GBrain's code-index/query layer, so adoption could create a second code truth store.
- Alpha classifier despite recent activity; expect rough edges.
- Requires a persistent DB/config footprint in its per-user configuration directory if used for real.
- README suggests a `curl | bash` post-install fix; avoid that path unless audited.

## Integration ideas

- Use as a comparison baseline for GBrain code graph ergonomics.
- Steal/report patterns: `CGC_REPORT.md`, dead-code/complexity reports, bundle export/load for pre-indexed projects.
- Only install permanently if it provides a capability GBrain lacks after a direct side-by-side test.

## Alternatives / related repos

- [oraios/serena](oraios--serena.md) — better immediate MCP coding-agent sidecar.
- [garrytan/gbrain](garrytan--gbrain.md) — current active index/query layer.

## Review candidates and context

- Candidate: compare CodeGraphContext side by side with the reference GBrain code-graph tools before adding a persistent index.
