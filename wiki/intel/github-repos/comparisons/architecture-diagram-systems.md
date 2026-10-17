---
title: Architecture Diagram Systems — Diagram Design vs Archify
type: comparison
category: architecture-diagrams
created: 2026-10-03
updated: 2026-10-06
last_reviewed: 2026-10-06
status: draft
confidence: medium
sources:
  - wiki/intel/github-repos/repos/cathrynlavery--diagram-design.md
  - wiki/intel/github-repos/repos/tt-a1i--archify.md
tags: [architecture, diagrams, agent-skills, provenance, artifact-validation]
---

# Architecture Diagram Systems — Diagram Design vs Archify

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

**Diagram Design emphasizes how to explain a system clearly; Archify emphasizes compiling, validating and safely publishing an authored system diagram.** This is a difference of emphasis, not a clean separation: both contain visual guidance, agent skills and artifact checks. Diagram Design is now adopted as a full external package after a separate bounded trial; Archify remains a sandboxed pattern reference. The dated usage disposition is recorded in the selected Diagram Design repo card.

Do not treat ingestion as adoption or the single Diagram Design trial as a comparative win. Prefer ordinary source-linked Markdown/Mermaid when a visual artifact adds little. For a concrete diagram task, choose based on the audience and required output contract rather than the repo score.

This draft records the **2026-10-03 initial** source comparison. It is **not a side-by-side generation benchmark**; comparative recommendations remain provisional.

## Decision matrix

| Dimension | Diagram Design | Archify |
|---|---|---|
| Main emphasis | Editorial design skill: reader question, behavioral semantics, visual grammar and complexity control | Agent skill plus Node.js compiler: typed inputs, renderer-backed checks, provenance and output lifecycle |
| Input approach | Agent-authored explanation; bounded importers for Mermaid, draw.io and Excalidraw structural digests | Typed JSON intermediate representation; examples and schemas for five renderer-backed modes |
| Output emphasis | Static-first HTML/SVG; accessible, print/reduced-motion meaning; optional motion | Interactive standalone HTML and export paths; optional local last-good preview |
| Strongest reusable patterns | Story before layout, overview/detail split, density budgets, before/after change ledger, import fidelity ledger | Exact-commit reference verification, stable repair receipts, candidate promotion, identity-bound publication and explicit recovery |
| Source fidelity | Preserve meaning and disclose merged/dropped elements; source truth still needs review | Optional verifier checks repository identity, commit, files and cited lines; semantic truth still needs review |
| Validation | Static safety/accessibility, geometry and browser-check tooling inspected | Synthetic validate/render/static-check passed; selected publication/repair/integration tests repeated locally |
| Hermes evidence | Later bounded artifact trial succeeded; broad host compatibility not established | Community Skill-only integration inspected and contract-tested; no installation or activation |
| License boundary | MIT core; separately attributed assets | MIT core; separately licensed marks/fonts |
| Initial disposition (2026-10-03) | `distill-pattern`, `reference-only` at source review; later superseded by full-package adoption | `distill-pattern`, sandboxed |

Source detail and canonical scores remain in [Diagram Design](../repos/cathrynlavery--diagram-design.md) and [Archify](../repos/tt-a1i--archify.md). This comparison does not maintain a second adoption tracker.

## Choose by use case

### Architecture summaries, onboarding and presentation artifacts

**Provisional preference: Diagram Design's methods.** Its reader-first framing, restrained visual language, complexity budgets and architecture-delta format are strong communication references. A later single-tool bounded trial succeeded, but does not establish superior generated output; no side-by-side generation comparison was performed.

### Interactive technical maps with reproducible checks

**Provisional preference: Archify.** Its typed source, structured diagnostics and checked artifact lifecycle are more directly suited to repeatable diagram production. Commit-pinned references can help readers inspect evidence. They do not prove the diagram is complete, correct, or representative of a live deployment.

### Redrawing an existing diagram

**Provisional preference: Diagram Design's import workflow.** Its Mermaid/draw.io/Excalidraw importers produce bounded structural digests and a fidelity ledger rather than executing the imported renderer. Archify explicitly excludes automatic Mermaid parsing. This remains a source-based preference, not a trial result; retain the original source when round-trip editing matters.

### Routine repository documentation

**Default: source-linked prose plus a simple text diagram.** Neither richer system is necessary merely because the repository is architectural. An authored visual companion should not become a competing source of truth for runtime state, ownership or implementation facts.

## Evidence and confidence

- **Diagram Design initial source evaluation:** pinned source, examples, import/check/export code and upstream CI were inspected; parent observed 11 successful checks and one skipped publishing job. No local upstream tests were run. A later task-specific unchanged-package trial succeeded, but does not constitute broad host-compatibility testing.
- **Archify:** reviewed at `d5a1333d7447c866a765adac7d4d062f2f02e4d2`. Synthetic workflow validation, rendering and static checking passed; parent repeated 81 selected tests with no failures or skips. No browser/visual acceptance, complete suite, preview-server trial or end-to-end source-evidence trial.
- **No comparative performance result:** neither test count, star count nor usefulness score establishes better readability, faster authoring or greater semantic fidelity.

The asymmetric execution evidence supports more confidence in Archify's tested paths—not a visual-quality winner. The two repo-note scores are judgment estimates, not directly measured performance.

## Risks that affect selection

- **Diagram Design:** observed mobile/example contract drift and small labels; examples contain external Google Fonts; optional motion adds JavaScript. One task-specific trial is limited evidence; broad host-specific skill/write-path behavior remains untested.
- **Archify:** guarded publication is recoverable, not crash-atomic replacement. An interruption can leave the public output absent while old bytes remain in a recovery backup. Its concurrency contract targets cooperating processes on local filesystems. Update checks and brand capture can use the network unless appropriately disabled/excluded.
- **Both:** chosen asset licenses and trademarks need review for public/commercial output. Neither prettier rendering nor valid cited lines establishes semantic accuracy. Sensitive sources require explicit data/export boundaries.

## Complementarity without overbuilding

An editorial checklist from Diagram Design could inform an Archify-authored artifact, but this is a **hypothesis**, not a shipped integration or demonstrated improvement. Distill narrow ideas into an existing workflow only after identifying a real failure or repeated need. Avoid installing two broad skills, adding conflicting authoring instructions, or building an adapter before a trial shows value.

## Review candidates

1. **Same-topology comparison:** still unperformed. Use one public synthetic system, one audience and one destination size. Evaluate a simple Mermaid/prose baseline against each candidate on semantic fidelity, readability, accessibility, editability, repair effort and total authoring time. Preserve the same source facts; report omissions and unsupported claims. The prior single-tool Diagram Design trial does not satisfy this comparative gate.
2. **Narrow pattern reuse:** assess whether complexity budgets, fidelity ledgers or structured repair receipts address a demonstrated gap in an existing artifact workflow. Promote only with a named consumer and a small verification probe.

## Usage boundary

The selected repo card and single repo rollup carry the dated usage disposition; this comparison does not maintain a second adoption tracker.

## Commitment disposition

Comparison capture only. This document did not authorize installation, activation, scheduled jobs, executable work or the separate trial; the dated usage disposition is recorded on the selected repo card.

## Source notes

- [Diagram Design pinned evaluation](../repos/cathrynlavery--diagram-design.md) — source-backed facts, risks and upstream evidence.
- [Archify pinned evaluation](../repos/tt-a1i--archify.md) — source-backed facts, bounded execution and publication caveats.
