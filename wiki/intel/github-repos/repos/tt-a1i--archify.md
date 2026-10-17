---
title: tt-a1i/archify
type: repo-intel
aliases: [Archify]
source: https://github.com/tt-a1i/archify
category: codebase-understanding
topics: [github-repo, architecture-diagrams, source-provenance, artifact-validation, agent-skills]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: sandboxed
score_confidence: high
last_reviewed: 2026-10-03
license: MIT
observed_revision: d5a1333d7447c866a765adac7d4d062f2f02e4d2
---

# tt-a1i/archify

> Reference-stack evaluation as reviewed 2026-10-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness:** 82/100 — strong source-provenance, structured repair, and guarded artifact-publication patterns; useful interactive diagrams without becoming an architecture truth store.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-10-03:** `sandboxed`. synthetic CLI render/check and selected tests only; no host skill installation or activation.
- **Confidence:** high for the inspected implementation and bounded tests, not for comprehensive security or visual quality.

## Scorecard

| Factor | Score | Rationale |
|---|---:|---|
| Stack fit | 22/25 | Local, agent-authored architecture/workflow communication with explicit source evidence. |
| Leverage | 21/25 | Reviewable interactive diagrams and actionable repair receipts can reduce explanation and retry effort; no measured productivity gain. |
| Reuse readiness | 17/20 | Bundled CLI works without dependency installation; documented community Hermes integration. |
| Maturity/trust | 11/15 | MIT project, stable release, substantial selected passing tests; publication and asset-license limits remain. |
| Differentiation | 11/15 | Stronger provenance and artifact lifecycle than basic diagrams, but more complex than Mermaid plus source-linked prose. |
| **Total** | **82/100** | Evidence-informed judgment, not a benchmark. |

## Verdict

Archify is an agent Skill and Node.js diagram compiler, not a general drawing editor or agent runtime. Preserve its typed diagram inputs, exact-commit evidence references, repair receipts and last-good publication behavior as reusable design references. Consider direct use only for a concrete need for interactive, standalone architecture artifacts. Keep simpler Markdown/Mermaid and narrative ownership documentation for ordinary engineering notes; diagrams are companions, not canonical runtime state.

## Reusable intelligence

- **Typed JSON intermediate representation:** architecture, workflow, sequence, dataflow and lifecycle modes have schema/example contracts. Agents author topology rather than relying on generic automatic layout. [Source: [Skill](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/archify/SKILL.md)]
- **Verified source references:** optional repository evidence requires a full commit SHA, credential-free repository identity, matching Git origin, safe relative paths and valid cited line ranges. The verifier checks Git objects at the selected revision. It proves referenced code exists there, not completeness, correct interpretation, or live-system truth. [Source: [evidence verifier](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/archify/renderers/shared/repository-evidence.mjs)]
- **Structured repair:** diagnostics expose stable rule codes, exact subjects, measured evidence and supported repair controls. Failed delivery preserves existing verified output in tested failure cases. [Source: [repair tests](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/archify/test/repair-receipt.test.mjs)]
- **Guarded and recoverable publication:** exclusive candidate staging, target identity checks, lock ownership, journals and explicit recovery constrain accidental replacement. Publication is **not crash-atomic replacement**: interruption can leave the public name absent while previous bytes survive in a private recovery backup. Guarantees target cooperating local processes, not distributed filesystems or hostile external writers. [Source: [delivery contract](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/archify/references/delivery-contract.md)]
- **Last-good preview:** optional loopback-only preview serves the last verified candidate and rejects invalid/superseded replacements; useful as a general candidate-versus-published-state pattern. This preview was inspected, not launched. [Source: [preview implementation](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/archify/bin/preview.mjs)]

## Evidence checked

**Pinned source:** `d5a1333d7447c866a765adac7d4d062f2f02e4d2`, tree `a804f94cd2b9f3688a19da94111b40fbecb105b1`. Latest stable release observed: [v3.0.1](https://github.com/tt-a1i/archify/releases/tag/v3.0.1), published 2026-09-28, tag commit `2ab3cae7ac2c2a55d7386ca789d03c4fcd31816c`. Main-branch tests below are not release-archive validation.

Metadata snapshot on 2026-10-03: 76,597 stars, 5,162 forks, non-archived, push timestamp `2026-10-03T15:10:38Z`. Counts are observations, not adoption-quality proof. [Source: [repository API](https://api.github.com/repos/tt-a1i/archify)]

Inspected README, Skill, schemas, manifest, source verifier, renderer/publication implementation, delivery/authoring contracts, preview and update-check paths, brand-fetch safeguards, license/third-party notices, Hermes integration and relevant tests. A selective pinned clone was used rather than a repomix pack; no raw source pack is committed to the vault.

### Bounded execution

Security-reviewed commands used synthetic bundled examples, isolated HOME/TMPDIR/output, no credentials, and `ARCHIFY_UPDATE_CHECK_DISABLED=1`. No dependencies were installed, no browser launched, no preview server started, and no private repository data used.

From the clone's `archify/` directory:

```text
node bin/archify.mjs --help
node bin/archify.mjs validate workflow examples/agent-tool-call.workflow.json --quality showcase --json
node bin/archify.mjs render workflow examples/agent-tool-call.workflow.json <scratch>/workflow.html
node bin/archify.mjs check <scratch>/workflow.html --json
```

All returned exit 0. Validation and static artifact checking each passed all nine reported checks. Synthetic HTML: 767,770 bytes, SHA-256 `3edbb38a05430865ee2f620c35de49f8e78dfd8788be14840d9e134b5912230d`. This is static validation, **not browser/visual acceptance**.

Parent independently repeated these selected tests from the pinned clone root with isolated HOME/TMPDIR: **81 passed, 0 failed, 0 skipped**.

```text
node --test archify/test/renderer-atomic-write.test.mjs \
  archify/test/repair-receipt.test.mjs \
  archify/test/atomic-output-recovery.test.mjs \
  archify/test/delivery-contract.test.mjs \
  integrations/hermes-agent/test/plugin-contract.test.mjs
```

The complete suite, browser export/visual checks and end-to-end source-evidence verification were not run. Scratch report/test output are ephemeral evidence, not required for understanding this note.

## Strengths

- Source-linked claims are pinned to exact Git objects rather than decorative URLs.
- Machine-readable failure feedback constrains repair scope and supports truthful completion.
- Last-good candidate promotion and no-clobber/recovery tests make output lifecycle explicit.
- Direct CLI example worked without a package-manager install.

## Risks / caveats

- Semantic fidelity remains an author/reviewer responsibility even when cited lines verify.
- Local static tests do not establish diagram readability, complete security, performance or real-workflow benefit.
- Project code is MIT; bundled marks/fonts have separate terms, including restrictions for some assets. Audit chosen export assets before public/commercial reuse. [Source: [third-party notices](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/THIRD_PARTY_NOTICES.md)]
- Community Hermes integration registers a Skill that invokes Node; it is not an official Nous integration or native rendering tool. No installation was performed. [Source: [integration](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/integrations/hermes-agent/README.md)]
- `deliver`/`finalize` can check updates over the network unless disabled; brand capture is also network-capable, with a private-address override. Selected smoke paths excluded these features. [Source: [update gate](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/archify/bin/delivery-update.mjs), [brand capture](https://github.com/tt-a1i/archify/blob/d5a1333d7447c866a765adac7d4d062f2f02e4d2/archify/renderers/shared/brand-marks.mjs)]
- Guarded publication can require explicit recovery after interruption; do not generalize its lock protocol to distributed storage.

## Alternatives / related repos

- [Diagram Design vs Archify comparison](../comparisons/architecture-diagram-systems.md) — complementary strengths, overlap and evidence limits; no adoption commitment.

- [Mermaid](https://mermaid.js.org/intro/) keeps concise diagram definitions in Markdown/code review; choose it when interactivity and provenance verification do not justify another artifact compiler. Archify does not automatically parse Mermaid.
- [ContextPlus](forloopcodes--contextplus.md) and [Graphify](Graphify-Labs--graphify.md) provide code/context graphs; they are not substitutes for a reviewed authored architecture narrative.
- [Codebase to Course](zarazhangrui--codebase-to-course.md) targets teaching artifacts; related communication value, different output contract.

## Evaluation boundary

This note records reusable evaluation evidence, not confidential operating policy, runtime installation or project state.

## Review candidates

1. **One public synthetic architecture artifact:** compare readability and repair effort with Mermaid plus source-linked prose. Promote only if an actual communication need and a bounded comparison justify direct use.
2. **Source-provenance and repair receipts:** assess transfer to an existing artifact workflow. Promote only after identifying a concrete failure that current validation does not catch.

## Commitment disposition

Ingestion only. No executable follow-up, GitHub issue, runtime adoption, skill installation or scheduling has been promoted.
