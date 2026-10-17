---
title: fallow-rs/fallow
type: repo-intel
source: https://github.com/fallow-rs/fallow
category: coding-tools
status: deep-analyzed
usefulness_score: 84
recommendation: adopt-now
usage: sandboxed
score_confidence: high
last_reviewed: 2026-08-10
license: MIT
---

# fallow-rs/fallow

> Opinionated reference-stack evaluation, reviewed 2026-08-10. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — a fast, deterministic TypeScript/JavaScript code-intelligence CLI with a credible agent/CI contract; a strong bounded addition for JS/TS repos, not a replacement for GBrain or general code navigation.
- **Recommendation:** `adopt-now` for a report-only, project-local trial on a TypeScript/JavaScript repo; graduate only if it finds actionable issues with low false-positive cost.
- **Usage observed 2026-08-10:** `sandboxed`. Isolated dead-code fixture found the intentional unused export; exit `1` meant findings.
- **Review candidate:** Add it as a dev dependency to one active JS/TS project and run `fallow recommend`, then a non-blocking PR-scoped `fallow audit`; defer its MCP server, agent hooks, auto-fix, and paid Runtime until that trial earns them.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Complements Hermes/Codex code work with deterministic, typed structural evidence for JS/TS; it is deliberately not a competing memory/index layer. |
| Leverage | 20/25 | Can turn cleanup/refactor uncertainty into concrete unused-code, impact, boundary, duplication, and changed-PR evidence. |
| Reuse readiness | 17/20 | One `npx` invocation or project dev dependency; JSON/SARIF/GitHub Action/MCP interfaces and a safe recommendation command are documented. |
| Maturity / trust | 14/15 | MIT; active daily development; v3.14.0 release on 2026-08-04; explicit security policy, signed binary verification, broad CI, benchmarks, and tests. |
| Differentiation | 13/15 | Unusually complete single static-analysis pipeline plus a PR “new findings only” gate; less unique than dedicated type checking/linting and limited to JS/TS. |

## Verdict

Fallow is worth a **bounded adoption** for TypeScript or JavaScript repositories where deterministic dead-code and architecture evidence is needed. Its best contribution is not “another linter”: it produces deterministic, machine-readable proof for deletion, refactoring, architectural-boundary review, and PR-scoped regressions without running project code. Start report-only. The paid runtime-coverage layer, MCP server, agent commit/push hooks, and any `fix` command all expand authority or operational scope and should wait until one project establishes useful signal quality.

## Reference-stack relevance

- Gives Hermes/Codex an evidence-producing companion for JS/TS changes: stable JSON, explicit exit semantics, symbol impact, and safe re-runs rather than model guesswork about dead code.
- The changed-file `audit` gate is exactly the right rollout shape for legacy repositories: only newly introduced findings block, rather than inheriting the whole cleanup backlog.
- Its security stance is unusually relevant for agentic workflows: static analysis does not execute project code; remote config inheritance is opt-in; config/plugin paths are containment-validated; agent-instruction surfaces are scanned for hidden Unicode.
- The repo’s design is worth copying even outside JS/TS: deterministic tools should have typed output, “findings vs operational error” exit codes, dry-run fixes, a baseline path, and small authority ramps.

## What it is

A Rust-native static-analysis suite for TypeScript and JavaScript. It builds a dependency graph to find unused files/exports/dependencies, cycles, duplication, complexity hotspots, architecture-boundary violations, CSS/design-system drift, optional security candidates, and optional TypeScript-checker-backed evidence. It ships CLI, LSP, GitHub Action, Node bindings, MCP launcher, and an optional paid production-runtime evidence layer. [Source: GitHub README, https://github.com/fallow-rs/fallow, 2026-08-10]

## Evidence checked

- GitHub metadata: 4,297 stars, 146 forks, MIT, 7 open issues, security policy, active commits on 2026-08-08–09, and v3.14.0 published 2026-08-04. [Source: GitHub API, https://github.com/fallow-rs/fallow, 2026-08-10]
- README: CLI contracts, agent/MCP support, staged PR audit behavior, no-Node default analysis, free-vs-paid Runtime boundary, and CI integration. [Source: https://github.com/fallow-rs/fallow/blob/main/README.md, 2026-08-10]
- `Cargo.toml`: Rust 2024 workspace, Oxc parsing/resolution, Rayon parallelism, LSP and test/benchmark dependencies. [Source: https://github.com/fallow-rs/fallow/blob/main/Cargo.toml, 2026-08-10]
- `BENCHMARKS.md`: reproducible Criterion and comparative methodology; it explicitly reports cases where competitors win. [Source: https://github.com/fallow-rs/fallow/blob/main/BENCHMARKS.md, 2026-08-10]
- `SECURITY.md`: project-code non-execution claims, restricted analysis-path process spawning, config containment, signed binary policy, dependency controls, and agent-instruction scanning. [Source: https://github.com/fallow-rs/fallow/blob/main/SECURITY.md, 2026-08-10]
- CI workflow: default-deny permissions; Rust tests, clippy, contract generation checks, hidden-Unicode scan, and dependency-safe npm installation are present. [Source: https://github.com/fallow-rs/fallow/blob/main/.github/workflows/ci.yml, 2026-08-10]
- **Sandbox smoke test:** `npx --yes fallow@3.14.0 dead-code --format json --quiet` in a disposable source-inspection workspace reported exactly one intentional unused export (`src/lib.ts:orphan`) in 38ms. It returned exit `1`, matching the documented normal-findings contract. [Source: local sandbox run, 2026-08-10]

## Strengths

- **Verified:** Typed JSON output and explicit exit codes distinguish clean (`0`), findings (`1`), and real error (`2`), which makes agent/CI orchestration reliable.
- **Verified:** `fallow audit` scopes enforcement to a PR’s introduced findings; that avoids turning historical debt into day-one gate noise.
- **Verified:** The static analyzer does not run repository code or package lifecycle scripts; ordinary analysis avoids network config fetches unless remote inheritance is explicitly enabled.
- **Verified:** Mature delivery hygiene: benchmark methodology, dedicated security policy, signed release binaries, pinned CI actions, Rust tests/clippy, hidden-Unicode scanning, and dependency controls.
- **Plausible:** `--type-aware` reduces syntactic false positives for aliases/re-exports when a cleanup needs semantic certainty, while retaining a fast Rust-native default path.

## Risks / caveats

- **Scope limit:** it is a TypeScript/JavaScript tool; it has no direct role in Hermes itself, GBrain, Python, Rust, or non-code specialist analysis.
- **False-positive budget:** first runs need entry-point/generated-code configuration; trust should be earned in a non-blocking trial before any CI gate.
- **Authority expansion:** `fix` mutates source files; `hooks install --target agent` gates commits/pushes; MCP and CI feedback/comment features broaden the surface. Do not enable any by default.
- **Optional SaaS boundary:** Fallow Runtime merges production execution evidence and continuous monitoring requires a license. Keep production coverage uploads and licensing outside the initial evaluation.
- **README claim, not independently audited:** npm/Action binary signature verification and the full security design were inspected in project documentation, not independently supply-chain audited.

## Integration ideas

1. **Best first trial:** in a disposable branch of an active JS/TS repository, add `fallow` as a dev dependency, run `fallow recommend --format json`, review its proposed config, and save no config automatically.
2. **Evidence bakeoff:** run `fallow audit --format json --quiet` on one PR-sized change and compare findings against ESLint/TypeScript/Knip outcomes. Measure useful findings, false positives, runtime, and whether an agent can act safely from the JSON.
3. **Only then:** add a report-only GitHub Action using an exact CLI version/package lock. Prefer `audit` over the full blocking pipeline for staged adoption.
4. **Pattern to steal now:** adapt its exit-code discipline and `findings ≠ tool failure` convention to Hermes/SStack deterministic validators.

## Alternatives / related repos

- [oraios/serena](oraios--serena.md) — semantic code navigation/editing candidate; Fallow is more focused on static cleanup/quality evidence.
- [CodeGraphContext/CodeGraphContext](CodeGraphContext--CodeGraphContext.md) — code-graph/MCP reference; Fallow is a narrower, deterministic JS/TS analyzer.
- [microsoft/agentrc](microsoft--agentrc.md) — AI-readiness/reporting candidate; Fallow can supply concrete code-quality evidence to a repo-readiness workflow.

## Review candidates and context

- Use only if a near-term JS/TS repo change provides a real, low-cost trial surface.
- Revisit after the report-only trial; promote to a PR audit gate only if precision is good and configuration stays small.
