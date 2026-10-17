---
title: Opinionated repository intelligence methodology
type: reference
status: active
tags: [repo-intelligence, harness-engineering, evaluation]
---

# Opinionated repository intelligence methodology

This collection evaluates tools and transferable patterns for a disclosed reference stack, not a universal best-tool ranking. Existing scores, dimension names and weights, evidence confidence, review dates, availability caveats and source attribution retain their authored meaning. This source-preparation pass does not refresh evidence or rescore repositories.

## Reference-stack assumptions

The reference stack favors a primary operator-controlled agent cockpit (Hermes), complementary coding assistants, portable skills and policy, a human-readable Markdown knowledge vault, and an independently replaceable retrieval/index layer. These are evaluation assumptions, not a claim about anyone's installed services or confidential live configuration.

- Prefer useful existing projects and bounded reuse to building another competing runtime.
- Favor local-first or self-hostable knowledge, explicit data boundaries, reversible integration and provider optionality. Hosted components can be worthwhile when their privacy, operating cost and dependencies are acceptable; local-first is a preference, not proof of security.
- Value reliable execution and evidence: scoped authority, isolated tools, visible approvals, review and verification, durable context, and recoverable long-running work.
- Prefer extracting a distinctive pattern when adopting the whole tool would duplicate a capable cockpit, memory layer, workflow engine or control plane.
- Judge leverage against integration and maintenance cost. A broad feature list, popularity or a high score alone is not an adoption decision.

Harmless tool-specific preferences and reference-stack comparisons remain intentional. They need not be rewritten as neutral product reviews. Confidential runtime state, private paths, private task links and private-owner relocation bindings do not belong in this collection.

## Deep GitHub-repository lens: usefulness_score

Deep repository cards and comparisons use an opinionated usefulness lens. Older cards may call the first factor **Stack fit**; newer cards may call it **General fit**. Preserve the authored label and score rather than retroactively normalizing them.

| Factor | Maximum | Interpretation |
|---|---:|---|
| Stack fit / General fit | 25 | Fit with the disclosed agent-cockpit, portable-skill, Markdown-vault, retrieval and local-first workflow assumptions. |
| Leverage | 25 | Transferable time saved, useful autonomy and optionality. |
| Reuse readiness | 20 | Installability, documentation, examples and integration cost. |
| Maturity/trust | 15 | Maintenance, tests, licensing and security evidence. |
| Differentiation | 15 | Advantage over alternatives or a distinctive pattern worth preserving. |

The total is 0–100. A recommendation such as `adopt-now`, `distill-pattern`, `watch`, `reference-only`, `defer` or `reject` is a non-binding evaluation under this lens, not authorization or a record of execution. Evidence depth differs by card: read its evidence checked, confidence and caveats. Historically authored totals and dimension points remain as recorded, including any explicitly disclosed inconsistencies; this methodology is not permission to repair scores silently.

## Lightweight Harness lens: harness_intel_score

The [Harness catalog](index.md) is a separate README/metadata-level intelligence layer, selected by the external Awesome Harness Engineering source. It does not inherit deep-card usefulness scores. Catalog intelligence asks how relevant and reusable an artifact's harness patterns are, with an explicit accessibility adjustment—not whether it should replace the reference stack.

| Dimension | Maximum | Anchors |
|---|---:|---|
| Harness relevance | 30 | 0 unrelated; 10 adjacent; 20 substantial component; 30 core harness function. |
| Practical pattern value | 25 | 0 none; 8 conceptual; 17 reusable; 25 directly transferable. |
| Evidence and maturity | 20 | 0 unavailable; 7 README-only/early; 14 active documented; 20 strong releases/tests/institutional evidence. |
| Novelty | 15 | 0 commodity; 5 incremental; 10 distinctive combination; 15 unusually differentiated. |
| Risk-adjusted accessibility | 10 | 0 inaccessible; 3 heavy/unclear; 7 usable and permissive; 10 easy and low-risk. |

Reviewed cards repeat the 0–100 total in frontmatter and the `## Score` body section, with five ordered point/max/rationale bullets. Unreviewed skeletons have a null total and no dimension awards; they cannot pass the full reviewed gate. An unavailable reviewed artifact receives zero evidence credit and low confidence, without guessing what missing code might do. Removed upstream identities remain provenance records, outside active totals, with explicit removal provenance. A rename or acquisition does not justify losing the original source identity or its documented attribution.

## Confidence, observation dates and provenance

Confidence qualifies the evidence behind a score; it is not another score. README claims, repository metadata, inspected code and executed tests are different evidence levels. Preserve caveats about unexecuted claims, young projects, unavailable licenses, security assumptions, capture truncation and dependency cost.

`last_reviewed` and `metadata_observed` date historical evidence; source and observed repository revisions identify different artifacts. Immutable upstream README and license URLs remain authoritative attribution. Mutable upstream links may remain as additional references, but do not imply fresh verification. Repository popularity at review time is public metadata, distinct from an individual's star-list membership.

Any retained reference-stack usage observation is explicitly dated and non-universal: `reference-only`, `not-used` or another usage label describes an observation, not intrinsic quality or current deployment. The renderer does not copy private usage, star membership, overlap paths, account ownership or snapshot fingerprints into cards or indexes. Historical acquisition and removed private joins are retained separately as private evidence, not shipped as knowledge metadata.

## Navigation and maintenance boundary

Navigation is ordinary relative Markdown in source. The catalog index is usable using its own cards and this methodology; it requires no excluded personal folder. Private links are replaced with upstream attribution or useful non-dependent prose, without discarding analysis. This source-local renderer owns source categories, identity, active/removal state and safe coverage metadata; authors own review evidence and narrative. A deterministic render is not semantic content certification, export approval, publication, indexing or proof of runtime adoption.
