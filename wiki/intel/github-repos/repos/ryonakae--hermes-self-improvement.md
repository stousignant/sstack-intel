---
title: ryonakae/hermes-self-improvement
type: repo-intel
created: 2026-10-06
updated: 2026-10-06
aliases: [Hermes Self Improvement, hermes-self-improvement]
source: https://github.com/ryonakae/hermes-self-improvement
category: hermes-self-improvement
topics: [github-repo, hermes, evidence-packs, outcomes, prompt-optimization]
status: watch
usefulness_score: 68
recommendation: watch
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-06
license: MIT
---

# ryonakae/hermes-self-improvement

> Reference-stack evaluation as reviewed 2026-10-06; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness:** 68/100 — promising observation/evidence/outcome architecture, with adoption and evaluation caveats.
- **Recommendation:** `watch`; lightweight pattern reference, not an installed self-improvement service.
- **Confidence:** medium for architecture/caveats, low for practical efficacy. This is deliberately a light ingest, not a complete security review.

## Verdict and reusable intelligence

The [README](https://github.com/ryonakae/hermes-self-improvement/blob/c952380c72e2dd32c6115b52a558d31979e6da4c/README.md) describes hooks → event log → deduplicated evidence packs → planner transactions → constrained editor → outcome/evaluation ledgers → DSPy/GEPA role-prompt overlays. The reusable idea is to group repeated failures/corrections into target-specific evidence and track later outcomes, rather than equating every reflection with a useful change.

Four roles separate planning, editing, evaluation and calibration. Edits go through official Hermes skill/memory tools rather than direct skill or provider-store writes. This does not make them non-mutating: improve/calibrate mutate by default, can involve model calls, and need explicit dry-run/authority/provider boundaries. Memory and user-profile edits broaden the surface beyond skill hygiene. README instructs regular operators to pause Curator's scheduled maintenance to avoid competing editors; this review does not endorse or perform that change.

[Curator telemetry](https://github.com/ryonakae/hermes-self-improvement/blob/c952380c72e2dd32c6115b52a558d31979e6da4c/hermes_self_improvement/curator_telemetry.py) enumerates configured/native external skill roots, rejects ambiguous and protected local candidates, and treats external records as read-only. Native integration and exact live eligibility were not executed here. README explicitly excludes built-in, hub, plugin, external, pinned and archived targets.

## Evidence checked

- October 6, 2026 parent REST snapshot: **5 stars, 0 forks, MIT**; last push **September 6, 2026**. Pinned SHA `c952380c72e2dd32c6115b52a558d31979e6da4c` is unchanged from the October 2 comparison. No independent adoption/efficacy signal was established.
- README, configuration example, pyproject (version 1.0.0; dependency `dspy>=3.1,<4`), calibration orchestration, prompt GEPA adapter and selected Curator telemetry source inspected.
- **Static check:** all **153 Python files** in the pinned archive parsed with Python AST. This is a cheap syntax check, not a deep review or upstream-test result.
- No install, upstream tests, runtime mutation, private-transcript replay, model calls or benchmark reproduction. No repomix/DeepWiki needed for this bounded light review.

## Strengths

- Evidence packs and explicit apply/defer/skip/block dispositions offer a stronger unit than unstructured reflections.
- Outcome, episode and credit-assignment artifacts distinguish attempted changes from downstream observations.
- Tool-mediated edits and source exclusions make intended ownership visible.

## Risks / caveats

- **Evaluation leakage:** [prompt_gepa_adapter.py](https://github.com/ryonakae/hermes-self-improvement/blob/c952380c72e2dd32c6115b52a558d31979e6da4c/hermes_self_improvement/prompt_gepa_adapter.py), lines 317–333, constructs `valset = list(trainset)`. This path's optimization validation is not a held-out test; it cannot establish generalization. The separate [gepa_adapter.py](https://github.com/ryonakae/hermes-self-improvement/blob/c952380c72e2dd32c6115b52a558d31979e6da4c/hermes_self_improvement/gepa_adapter.py) supports train/val paths but defaults both to the same case file. Do not overgeneralize this into claiming every downstream check is identical.
- **Recovery:** README expressly states there is no general rollback pipeline; weak/failed changes become later corrective evidence. Prompt-overlay promotion is not equivalent to package-wide skill/memory rollback.
- Broader mutation scope, DSPy dependency and provider-visible evidence/optimization cost need a separate trial contract. Local event capture is not an approval to send private history to a provider.
- Stars/fixtures/ledgers are not proof of useful accepted improvements. Small ecosystem and a month without a push lower adoption confidence, not automatically source quality.

## Alternatives / related repos

- [pingchesu/hermes-curator-evolver](pingchesu--hermes-curator-evolver.md) — narrower guarded file apply and review-only mining.
- [aiming-lab/MetaClaw](aiming-lab--MetaClaw.md) — proxy/training approach; distinct integration/privacy surface.
- [hermes native self improvement](../comparisons/hermes-native-self-improvement.md) — bounded comparison.

## Evaluation boundary

This note records reusable evaluation evidence, not confidential operating policy, runtime installation or project state.

## Review candidates

- Rank 1 — inspect failure clustering and outcome attribution if an existing evidence owner cannot already provide them; promotion requires one separately authorized, useful attributable fixture result.
- Rank 2 — revisit only after independent held-out evaluation and general recovery improve; no automatic revisit scheduled.

## Commitment disposition

Not promoted. No optimizer, editor, scheduler, memory mutation or provider switch adopted.
