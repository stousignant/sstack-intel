---
title: cathrynlavery/diagram-design
type: repo-intel
source: https://github.com/cathrynlavery/diagram-design
category: diagram-design
status: deep-analyzed
usefulness_score: 87
recommendation: adopt-now
usage: pattern-in-use
score_confidence: medium
created: 2026-10-03
updated: 2026-10-06
last_reviewed: 2026-10-06
license: MIT
tags: [agent-skills, diagrams, architecture, svg, accessibility]
---

# cathrynlavery/diagram-design

> Opinionated reference-stack evaluation, reviewed 2026-10-06. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Initial source evaluation — 2026-10-03

- **87/100 — initial `distill-pattern` recommendation; medium confidence.** Strong reference for editorial architecture diagrams and executable artifact-quality contracts. At the time of this assessment, direct host compatibility and generated-output quality remained untested.
- Review pinned to commit `f903933a534ba92cde1c85a28186267b3a317bb2` on `main`.
- Acquisition/review only at this stage: no installation, activation, local upstream test execution, or diagram-generation run.

## Dated usage observation — 2026-10-06

- Dated reference-stack observation: the full upstream package was adopted on **2026-10-05**, rather than vendored or selectively rewritten. This is not a universal adoption verdict.
- A bounded trial on **2026-10-03** succeeded with the package unchanged. The final artifact's XML, resources, layout, and mobile behavior were checked after an unwanted font import was removed from the generated output. This is evidence for that task, not broad host compatibility or a guarantee of every diagram's factual correctness.
- Keep human-facing evaluation separate from source pins and restore/update procedures. Public package guidance: [upstream README](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/README.md).
- Operational checkout paths and procedures are outside this evaluation; a dated selection does not establish every host's compatibility.

## Scorecard

This is an evidence-informed usefulness estimate, not a measured benchmark.

| Factor | Score | Reason |
|---|---:|---|
| Stack fit | 23/25 | Portable Markdown skill and HTML/SVG artifacts suit architecture explanations and documentation. Host path assumptions still need review. |
| Leverage | 23/25 | Strong before/after, complexity-control and import/redraw patterns can reduce diagram iteration and improve communication. Time savings unmeasured. |
| Reuse readiness | 16/20 | Detailed references, examples, importers and checks; stale examples and host-specific installation limit drop-in readiness. |
| Maturity/trust | 12/15 | MIT, active source, regression tests and successful upstream CI; no local runtime/security validation or GitHub releases. |
| Differentiation | 13/15 | Combines restrained visual language, semantic routing, fidelity ledgers and deterministic output checks. |
| **Total** | **87/100** | Initial source-review assessment; dated reference-stack usage is recorded above. |

## Verdict

A substantial design-oriented agent skill, not a diagram renderer or architecture-discovery engine. Preserve its behavior-before-layout method, density budgets, static accessibility and safe source-to-intermediate-representation workflow. It is a promising reference for architecture snapshots, modernization deltas, trust boundaries and professional explainers. Do not infer that a prettier diagram is factually correct or that documented multi-host support proves compatibility with another harness. [Source: [README](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/README.md), [core skill](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/SKILL.md)]

## Reusable intelligence

- **Behavior semantics before layout.** Select the reader's question and behavioral pattern first, then the visual grammar. The documented catalog covers 42 diagram types; semantic patterns separately specify primitives, caps, anti-patterns and static fallbacks.
- **Complexity as a quality contract.** State the story, remove or merge unnecessary nodes/arrows, cap visual accents and split overview/detail instead of shrinking labels.
- **Static-first output.** Inline SVG/CSS with accessible title/description and explicit status words; motion is optional and must preserve complete static, reduced-motion and print meaning.
- **Safe import, not renderer execution.** Local draw.io, Mermaid and Excalidraw extractors produce bounded structural digests. Discard source styling, links and executable content; preserve components/relationships and report what was merged, collapsed or dropped in a fidelity ledger.
- **Artifact checks as part of skill delivery.** Static safety/accessibility checks, geometry verification and browser-render checks turn visual advice into a partially executable contract.
- **Brand profiles as reviewed data.** Semantic tokens, preview/approval before style writes, strict profile slugs and project markers are reusable packaging ideas, not authority to edit unrelated projects.

Sources: [semantic patterns](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/references/semantic-patterns.md), [output spec](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/references/output-spec.md), [profiles](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/references/profiles.md), [CI](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/.github/workflows/ci.yml).

## Evidence checked — initial evaluation (2026-10-03)

- Live GitHub metadata on 2026-10-03: **43,204 stars**, **2,785 forks**, public/non-archived, MIT, last push **2026-10-01T17:03:07Z**. No GitHub releases returned; plugin version `2.6.51` is package metadata, not a tagged release.
- Shallow clone pinned to the SHA above; README, core skill, semantic-pattern/style/output/profile/onboarding/animation/export/import references, privacy/security/license and third-party attribution files inspected.
- Three static examples inspected: architecture, architecture-delta and data-flow. Selected source scans found no script tags and a Google Fonts URL in each; this does not prove every possible output is script-free or offline.
- Importer, self-check and SVG-export source inspected; targeted adversarial test files and CI inspected. No repomix needed: selective source inspection was sufficient for this documentation/skill-heavy repository.
- Parent independently checked the exact clone SHA, core mobile contract and architecture example, and queried that SHA's GitHub check runs: **11 successful, one skipped publish job**. These are upstream results, not local test results.
- **Smoke test at initial evaluation: not run.** No upstream scripts executed or provider-backed generation was attempted in that source-review pass. The later bounded artifact trial is recorded above; it does not replace upstream test or broad compatibility evidence.

## Strengths

- Concrete reference layouts and output dials make audience, detail, size and export format explicit before drawing.
- Architecture-delta separates before/changes/after and uses a change ledger rather than relying on color alone.
- Bounded importers and adversarial safety tests are stronger evidence than a prompt-only promise to ignore untrusted content.
- MIT core license permits adaptation; keep required notices and separately attributed asset terms.

## Risks / caveats

1. **Observed example/contract drift.** The core checklist requires SVG `min-width` equal to `viewBox` width plus a local horizontal scroller. The architecture example uses 900px versus a 1000-wide viewBox and lacks the wrapper; delta uses 1100px versus 1200; data-flow lacks the wrapper and uses 9px/6.5px node text. Validate output at its destination size rather than copying samples unquestioningly. Parent verified the architecture mismatch directly. [Source: [core checklist](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/SKILL.md#9-pre-output-checklist-taste-gate), [architecture example](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/assets/example-architecture.html), [delta example](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/assets/example-architecture-delta.html), [data-flow example](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/skills/diagram-design/assets/example-data-flow.html)]
2. **Not fully offline by default.** Google Fonts can receive viewer network/browser metadata; the publisher's no-telemetry policy does not cover agent-provider processing. Optional motion runs JavaScript. Inspect generated HTML and font sourcing before sensitive/offline use. [Source: [privacy policy](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/PRIVACY.md)]
3. **Large, host-assuming skill.** The core is 389 lines / 29,706 bytes, with project-profile/file-write behavior and host-specific packaging. The later single-task trial is narrow evidence only; broad cross-host compatibility has not been established.
4. **License layers.** Third-party icon/font assets have separate licenses and trademark context; the root MIT license does not replace those notices. [Source: [third-party licenses](https://github.com/cathrynlavery/diagram-design/blob/f903933a534ba92cde1c85a28186267b3a317bb2/THIRD_PARTY_LICENSES.md)]
5. **Maintenance evidence is bounded.** Active main and upstream checks support maintenance, but absence of tagged releases complicates version selection. Neither popularity nor CI proves every layout's visual quality or a complete security audit.

## Alternatives / related repos

- [Diagram Design vs Archify comparison](../comparisons/architecture-diagram-systems.md) — complementary strengths, overlap and evidence limits; no adoption commitment.

- [Graphify](Graphify-Labs--graphify.md): extraction/navigation evidence, not the same product. A presentation layer must preserve the graph's evidence distinctions rather than replace source truth.
- [Understand-Anything](Egonex-AI--Understand-Anything.md): guided codebase understanding/graph UX, not editorial diagram styling.
- Mermaid, draw.io and Excalidraw are editable/source diagram formats this project can redraw; retain the original when round-trip editability matters. This review did not benchmark competing renderers.

## Operating boundary

This page retains source evidence and a dated reference-stack selection. Operational integration remains a separate owner decision; the review does not authorize runtime changes.

## Initial review candidates — 2026-10-03

1. **Bounded architecture-diagram trial:** proposed asking whether one verified topology could become a readable document/slide artifact with no semantic loss. A later authorized trial succeeded for one artifact; that does not establish broad compatibility or universal semantic fidelity.
2. **Narrow pattern distillation:** originally proposed assessing selective reuse without importing the host-specific package. The 2026-10-05 reference-stack decision instead adopted the full external package; this dated candidate is retained as provenance, not an active next step.

## Initial commitment disposition — 2026-10-03

At the initial evaluation, no executable work or installation was promoted; this page recorded repository ingestion and existing-list placement only. That dated disposition was superseded by the separately approved external-package adoption on 2026-10-05. No separate task/status tracker is created here.
