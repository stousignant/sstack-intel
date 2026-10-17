---
title: kunchenguid/axi
type: repo-intel
aliases:
  - AXI
  - Agent eXperience Interface
  - "GitHub repo: kunchenguid/axi"
source: https://github.com/kunchenguid/axi
url: https://axi.md/
category: agent-interface-design
topics: [github-repo, agent-ergonomics, cli, mcp, harness-engineering, tool-design]
status: deep-analyzed
usefulness_score: 92
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-08-13
license: MIT
checked_ref: 32562f07b416f42b1b02f113ae9af901b77d5e33
---

# kunchenguid/axi

> Reference-stack fit as reviewed 2026-08-13; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `92/100` — unusually concrete agent-interface doctrine backed by inspectable implementations, benchmark harnesses, raw trajectories, tests, and a growing ecosystem; directly relevant to Hermes tool design.
- **Recommendation:** `distill-pattern` — use AXI as a design and evaluation rubric, not as a blanket “CLI beats MCP” doctrine or a new runtime dependency.
- **Usage observed 2026-08-13:** `pattern-in-use`. Concise defaults, progressive disclosure, explicit empty states, actionable errors and action-plus-observation as design influences.
- **Confidence:** `high` in the repository assessment; `medium` in benchmark generalization beyond the published model, tasks, repositories, and harness conditions.
- **Review candidate:** Apply the ten principles selectively when creating or revising Hermes/SStack tools. Require a matched-task benchmark before replacing a useful MCP surface with an AXI wrapper.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 25/25 | Direct fit for Hermes tools, GBrain output, shell-facing automations, and SStack skill/tool design. |
| Leverage | 23/25 | Better defaults can reduce turns, context growth, retries, and operator friction across every agent workflow. |
| Reuse readiness | 18/20 | Detailed installable skill, MIT SDK, official implementations, generated docs, catalog, tests, and reproducible harness commands. |
| Maturity/trust | 13/15 | Active releases and green local checks; young project, one main maintainer, no visible security policy, and benchmarks remain project-run. |
| Differentiation | 13/15 | Strong synthesis of known CLI principles into an agent-specific standard with evidence; TOON-first and hooks-first positions are useful but not universal. |
| **Total** | **92/100** | High-value design doctrine; adopt through measured distillation rather than protocol ideology. |

## Verdict

AXI is worth keeping as a **canonical external reference for agent-facing interface design**. Its best contribution is not “replace MCP with CLI.” It is the sharper claim that transport is secondary to the interaction contract: minimize default output, return enough state to avoid predictable follow-up calls, make empty/error states definitive, reject unknown input, remain non-interactive, and disclose help progressively. The repo is materially stronger than a manifesto: it contains an installable skill, a small JavaScript SDK, official implementations, source-generated documentation, tests, benchmark runners, committed result sets, and per-run trajectories.

The boundary matters. The published results establish that AXI wrappers performed very well in the project's two tested environments with Claude Sonnet 4.6; they do not prove that AXI dominates every MCP server, model, task, or stateful workflow. Hermes should use AXI as an audit rubric and experiment design—not add another universal rule or rewrite functioning tools on faith. [Source: [AXI README](https://github.com/kunchenguid/axi/blob/32562f07b416f42b1b02f113ae9af901b77d5e33/README.md), benchmark studies and raw results at reviewed revision, checked 2026-08-13]

## Reference-stack relevance

- **Hermes tool quality compounds.** Every unnecessary field, ambiguous empty response, repeated observation call, or weak error consumes tokens and attention across future sessions.
- **It sharpens CLI-first without becoming anti-MCP.** Persistent introspection, host-managed permissions, or rich stateful interaction can still justify MCP; narrow deterministic operations often benefit from an AXI-style CLI.
- **It supplies an evaluation contract.** Accuracy, cost, latency, turns, output sufficiency, and recovery behavior are better tool-design metrics than protocol branding.
- **It matches the reference stack's harness doctrine.** The repo treats agent experience as a designed system surface and validates generated docs, skill drift, release artifacts, and benchmark trajectories.
- **The implementation ecosystem is now real.** The project catalogs official GitHub, browser, review, and quota AXIs plus community tools across databases, cloud, collaboration, and terminal control. Catalog membership is evidence of ecosystem activity, not independent certification.

## What it is

AXI—Agent eXperience Interface—is a set of ten design principles for shell-executed tools used by AI agents. The project includes:

1. token-efficient output, currently recommending TOON;
2. minimal default schemas;
3. bounded content with explicit `--full` escape hatches;
4. pre-computed aggregates that eliminate predictable follow-up calls;
5. definitive empty states;
6. structured errors, truthful exit codes, idempotent mutations, no prompts, and rejection of unknown flags;
7. explicit opt-in session integrations plus an on-demand skill path;
8. live content rather than help as the no-argument home view;
9. contextual next-step disclosure;
10. concise per-command help and a fast version path.

The repo also owns `axi-sdk-js`, benchmark harnesses for GitHub and browser interfaces, a generated catalog, and the installable `.agents/skills/axi/SKILL.md`. [Source: [AXI skill](https://github.com/kunchenguid/axi/blob/32562f07b416f42b1b02f113ae9af901b77d5e33/.agents/skills/axi/SKILL.md), checked 2026-08-13]

## Evidence checked

### Live metadata

- GitHub metadata on 2026-08-13: 1,831 stars, 133 forks, MIT, TypeScript, not archived, created 2026-03-21, pushed 2026-08-12.
- Latest release: `axi-sdk-js-v0.1.10`, published 2026-08-07; npm reported `axi-sdk-js` version `0.1.10` with provenance-oriented release automation in the repository workflow.
- Recent GitHub Actions runs inspected were successful. Branch-protection details were unavailable through the public API endpoint.

### Source inspection

- Fresh shallow clone at exact revision `32562f07b416f42b1b02f113ae9af901b77d5e33` in a temporary upstream clone.
- Inspected `README.md`, `VISION.md`, `AGENTS.md`, `principles.yaml`, `catalog.yaml`, `.agents/skills/axi/SKILL.md`, `packages/axi-sdk-js/`, both benchmark task sets, benchmark runners/reporting surfaces, published summaries, raw GitHub result JSONL, per-run grades, and release/CI workflows.
- The benchmark artifacts are substantive: task definitions, condition definitions, usage extraction, LLM grading, raw outputs, grades, reports, and test coverage are committed rather than represented only by a marketing chart.

### Local verification

Run from the clean clone with Node `v24.11.1` and the pinned `pnpm 11.1.1`:

- `pnpm install --frozen-lockfile` — passed.
- `pnpm run docs:check` — passed; generated regions matched their sources.
- `pnpm run docs:test` — 4/4 passed.
- `pnpm run format:check` — passed.
- `pnpm run lint` — passed.
- `pnpm --dir packages/axi-sdk-js run build` — passed.
- `pnpm --dir packages/axi-sdk-js test` — 156/156 passed.
- `pnpm --dir bench-github test` — 29/29 passed.
- `pnpm --dir bench-browser test` — 52/52 passed.

No live model benchmark matrix was rerun because it would incur external model/API cost and is unnecessary for verifying repository structure and published-result integrity.

## Benchmark assessment

### GitHub benchmark

The committed result file contains 425 runs: 17 tasks × 5 conditions × 5 repeats, all using Claude Sonnet 4.6 on 2026-03-21. Independent recomputation from `results.jsonl` matched the published aggregate:

| Condition | Passed | Avg input tokens | Avg cost | Avg duration | Avg turns |
|---|---:|---:|---:|---:|---:|
| `gh-axi` | 85/85 | 46,462 | $0.0502 | 15.7s | 3.0 |
| `gh` CLI | 73/85 | 47,076 | $0.0539 | 17.4s | 3.2 |
| GitHub MCP, eager | 74/85 | 175,757 | $0.1481 | 34.2s | 5.6 |
| MCP code mode | 71/85 | 137,409 | $0.1005 | 43.4s | 7.4 |
| GitHub MCP + ToolSearch | 70/85 | 153,621 | $0.1465 | 41.1s | 8.0 |

This is strong **project-run evidence** that pre-computed totals, concise structured output, and guided follow-ups helped on the selected GitHub tasks. It is not third-party reproduction. The same model served as agent and judge according to the published study, although a task-file comment references `gpt-5.4-mini`; that internal documentation inconsistency should be resolved before treating the study as publication-grade methodology. [Source: [GitHub benchmark study](https://github.com/kunchenguid/axi/blob/32562f07b416f42b1b02f113ae9af901b77d5e33/bench-github/published-results/STUDY.md) and committed raw results, checked 2026-08-13]

### Browser benchmark

The published report contains 490 runs: 14 tasks × 7 conditions × 5 repeats with Claude Sonnet 4.6. `chrome-devtools-axi` reports 70/70 successes, 79,141 average input tokens, $0.0744 average cost, 21.5 seconds, and 4.5 turns. The closest CLI-style alternatives also reached 99% success at similar cost. This supports AXI's competitiveness more than a categorical protocol victory: task-level results show several cases where another condition was cheaper or faster, and the report notes cold-start and tool-schema visibility limitations affecting comparisons. Unlike the GitHub benchmark, the browser result directory exposes the generated report but not an equivalent top-level `STUDY.md` or `results.jsonl` in the reviewed clone, so auditability is lower. [Source: [browser benchmark report](https://github.com/kunchenguid/axi/blob/32562f07b416f42b1b02f113ae9af901b77d5e33/bench-browser/published-results/report.md), checked 2026-08-13]

## Strengths

- **Interface doctrine is operationalized.** Principles are detailed enough to review an implementation, not just inspire one.
- **Action-plus-observation is a high-leverage insight.** Pre-computing common aggregates and returning post-action state can remove whole agent turns.
- **Error semantics are excellent.** Unknown flags fail loudly, mutations are idempotent where appropriate, errors are actionable, and commands remain non-interactive.
- **Progressive disclosure is treated as interface design.** Minimal lists, bounded details, `--full`, concise help, and contextual suggestions provide a coherent retrieval gradient.
- **Evidence is inspectable.** The GitHub benchmark includes raw trajectories and grades; local aggregation reproduced the headline numbers.
- **Repository hygiene is strong for a young project.** Source-generated docs/catalogs, drift checks, tests, release automation, npm provenance, and an explicit conservative vision reduce accidental drift.
- **Permissive reuse.** MIT licensing makes selective pattern and SDK reuse straightforward.

## Risks / caveats

- **Do not turn AXI into protocol dogma.** MCP can still be the right substrate for host-mediated permissions, persistent state, streaming, rich introspection, or cross-client standardization.
- **Benchmark external validity is limited.** Published runs cover one model, selected tasks, one GitHub target, public websites, project-authored wrappers, and project-authored grading methodology.
- **Same-model judging can correlate errors.** A different judge family and deterministic ground truth would strengthen reliability claims.
- **Task drift exists.** Dynamic GitHub and web targets can change during a matrix; some grading hints are approximate or time-sensitive.
- **Browser evidence is less auditable than GitHub evidence** in the reviewed checkout because the summarized report lacks the same raw-result bundle.
- **TOON is a means, not the principle.** Token-efficient, unambiguous output matters; forcing TOON where JSON/tool-native structures are already cheap and reliable could add complexity without payoff.
- **Ambient hooks are not universally free.** Session-start context can become permanent prompt tax; Hermes should preserve opt-in, relevance, and strict token budgets.
- **No visible `SECURITY.md`.** The core repo is mostly docs, SDK, and benchmarks, but the SDK includes hook installation and self-update behavior that deserves normal supply-chain scrutiny before dependency adoption.
- **Young ecosystem and bus factor.** Momentum is strong, but the standard and official implementations are primarily driven by one maintainer.

## Integration ideas

- Use AXI's ten principles as a checklist in future Hermes tool/plugin/CLI reviews, while allowing explicit exceptions by task shape.
- Add **turn elimination** and **output sufficiency** to Hermes tool evals: did the response include the total, post-action state, and bounded detail needed for the next decision?
- Benchmark one matched Hermes workflow across its existing native tool/MCP surface and a compact CLI wrapper before changing architecture.
- Treat combined action-plus-observation as a tool-design primitive where it preserves atomicity and does not hide important intermediate state.
- Borrow the repository's single-source generation checks: canonical YAML/spec → README/docs/skill output → CI drift check.
- Keep SDK adoption optional. The principles can improve Python, shell, MCP responses, and Hermes native tools without adding `axi-sdk-js`.

## Alternatives / related repos

- [mvanhorn/cli-printing-press](mvanhorn--cli-printing-press.md) — generates agent-first CLIs from API specifications; complementary implementation strategy.
- [microsoft/playwright-mcp](microsoft--playwright-mcp.md) — strong counterexample to simplistic CLI supremacy: persistent structured browser interaction can justify MCP.
- [pasky/chrome-cdp-skill](pasky--chrome-cdp-skill.md) — compact CLI/skill access to an existing browser session.
- [harness-engineering](../../../concepts/ai-engineering/harness-engineering.md) — canonical local doctrine where AXI's durable interface-design lessons belong.
- Discovery context: a Kun Chen workflow interview introduced AXI; the pinned public repository and benchmark sources above support this assessment independently.

## Review candidates and context

No executable backlog item created. The durable action is a standing design rule: apply AXI selectively when a Hermes/SStack tool is being built or revised, and only launch a CLI-vs-MCP benchmark when a real repeated workflow makes the outcome decision-relevant.
