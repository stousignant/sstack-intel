---
title: NousResearch/hermes-agent-self-evolution
type: repo-intel
aliases:
  - hermes-agent-self-evolution
  - GitHub repo: NousResearch/hermes-agent-self-evolution
source: https://github.com/NousResearch/hermes-agent-self-evolution
category: hermes-self-improvement
topics: [github-repo, hermes-agent, self-improvement, skill-optimization, dspy, gepa, evals]
status: deep-analyzed
usefulness_score: 53
recommendation: defer
usage: not-used
score_confidence: high
last_reviewed: 2026-09-10
license: MIT
---

# NousResearch/hermes-agent-self-evolution

> Reference-stack evaluation as reviewed 2026-09-10; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `53/100` — strong problem fit, but the shipped path cannot currently produce and validate a usable candidate for the 42,116-character operational-skill target.
- **Recommendation:** `defer`
- **Usage observed 2026-09-10:** `not-used`.
- **Confidence:** `high` in the parked disposition because the blockers were reproduced against current `main`; this is not a claim that optimization quality is proven.
- **Evaluation disposition:** **deferred under the reviewed evidence; not operationally ready.**
- **Revisit only when:** the core fixes ship on the default branch or in a release, the target size is supported, and a real run produces a non-empty skill artifact plus external end-to-end evaluation evidence.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | It targets Hermes skill evolution directly, but its text-only predictor does not execute Hermes tools or workflows. |
| Leverage | 15/25 | A working review-gated optimizer could help, but there is no stable working path for the target now. |
| Reuse readiness | 3/20 | Current `main` has blocking GEPA, writeback, validation, and size-limit defects. |
| Maturity/trust | 4/15 | Unit tests are green, but there are no tags/releases and the tests do not prove the end-to-end optimization path. |
| Differentiation | 8/15 | Hermes-specific targeting remains interesting, but it has not produced verified target artifacts and overlaps the broader skill-optimization problem space. |
| **Total** | **53/100** | Preserve as research evidence; do not operate it until the revisit gates are met. |

## Verdict

The earlier `adopt-now` recommendation is withdrawn. Current `main` at [`0a929e3aa20e15cf04dc7c28492a7d41a5139125`](https://github.com/NousResearch/hermes-agent-self-evolution/tree/0a929e3aa20e15cf04dc7c28492a7d41a5139125) has no tag or release and does not provide a stable working path for the reviewed operational ingestion skill. A dry run can locate the copied skill, and the unit suite passes, but the actual optimizer path is blocked before it can supply trustworthy artifact/eval proof. Treat the repository as parked research, not a sandbox-ready operational candidate.

## What it is

`hermes-agent-self-evolution` is a standalone Python/DSPy project intended to optimize Hermes skill text and save baseline, evolved, and metric artifacts. Its internal evaluator is a text-only DSPy prediction scored primarily by lexical overlap; it does not instantiate Hermes, provide Hermes tools, capture tool trajectories, or verify filesystem/GitHub side effects. Therefore its internal holdout result cannot serve as end-to-end evidence for an operational skill such as the reviewed operational ingestion skill.

## Current preflight findings

The 2026-09-10 preflight inspected the pinned source revision below; the findings and upstream issue/repair citations are retained here.

- **Freshness:** local and live `main` matched `0a929e3aa20e15cf04dc7c28492a7d41a5139125`; GitHub reported zero tags and zero releases.
- **GEPA call is incompatible:** current code passes `max_steps` to the resolved DSPy GEPA API, which expects budget fields such as `max_full_evals`; the constructor fails before optimization. [Issue #10](https://github.com/NousResearch/hermes-agent-self-evolution/issues/10)
- **Optimized text is discarded:** `skill_text` is a plain module attribute while DSPy mutates predictor instructions/demos, then the runner reads the unchanged attribute. [Issue #141](https://github.com/NousResearch/hermes-agent-self-evolution/issues/141), [issue #172](https://github.com/NousResearch/hermes-agent-self-evolution/issues/172)
- **Constraint validation is wired to fail:** the runner passes only the skill body while the structure validator requires YAML frontmatter. [Issue #171](https://github.com/NousResearch/hermes-agent-self-evolution/issues/171)
- **Target size is unsupported:** the copied operational ingestion skill was 42,116 characters, while the CLI enforces a non-configurable 15,000-character cap.
- **Green tests are narrower than the claim:** `145 passed` confirms the unit suite, not a successful GEPA run, material evolved writeback, full-file constraint pass, Hermes tool execution, or useful held-out artifact.
- **No stable fallback:** GEPA failure enters MIPROv2, but the fresh default/dev install did not provide its required `optuna` dependency.

These defects originated in the initial [`0949dc7`](https://github.com/NousResearch/hermes-agent-self-evolution/commit/0949dc7) implementation under `forge/`; the package was later renamed to `evolution/`, where the current equivalents remain on `main`.

## Unmerged repair status

Open [PR #178](https://github.com/NousResearch/hermes-agent-self-evolution/pull/178), head [`3247dad5df2440bd6684a5e64ef08b79822db139`](https://github.com/NousResearch/hermes-agent-self-evolution/commit/3247dad5df2440bd6684a5e64ef08b79822db139), addresses the central GEPA argument, optimizable/read-back `skill_text`, full-file frontmatter validation, session import, and fallback-dependency defects. It remains unmerged, so none of those changes are shipped on `main`. Its changed files do not remove or parameterize the 15,000-character cap, so the 42,116-character target remains excluded even if the PR lands unchanged.

## Historical evidence retained

The 2026-06-12 review remains useful as historical evidence, not current operational proof:

- The then-reviewed clone passed `139` tests after a normal editable dev install.
- README/PLAN described reviewable outputs, semantic preservation, pytest gates, and future prompt/tool/code phases.
- The repository looked unusually aligned with Hermes-native skill evolution and was scored `94/100` with `adopt-now`.

The later preflight falsified the operational inference from those signals. Passing unit tests did not exercise the broken optimizer call or prove a changed, valid skill artifact. README/PLAN guardrails such as running pytest, semantic preservation, PR creation, and real Hermes execution were not implemented in the runner inspected at current `main`.

## Relationship to SkillOpt and GBrain

Keep three implementations distinct:

1. **This repository:** NousResearch's standalone Python/DSPy Hermes Self-Evolution project.
2. **Microsoft/SkillOpt:** a separate standalone Python research/package implementation with its own `skillopt-sleep` transcript-harvest surface.
3. **GBrain `skillopt`:** an independent TypeScript implementation of related validation-gated skill-optimization ideas inside GBrain; it is not the Microsoft Python package and does not make that standalone package installed or active.

Possible shared ideas include frozen evals, held-out gates, candidate diffs, and proof bundles. That conceptual overlap is not evidence that any one implementation supplies a working path for the others.

## Strengths

- Targets the right reviewable artifact: skill text rather than model weights.
- Keeps current shipped behavior proposal-oriented rather than directly mutating active skills.
- Provides a compact codebase and tests that make defects inspectable.
- Offers useful design vocabulary for candidate generation, split datasets, constraints, and human review.

## Risks / caveats

- No tags/releases; README and `pyproject.toml` claim MIT, while GitHub exposes no license object and the inspected clone had no `LICENSE` file.
- Text-only lexical evaluation can reward plausible prose without tool use or correct side effects.
- Dataset auto-splitting uses unseeded shuffle and metrics do not persist a dataset hash/version, weakening reproducibility.
- The runner's documented test, semantic-preservation, benchmark, PR, and execution-trace gates are absent or unwired.
- Any future bakeoff must use a separate fixed Hermes evaluator with identical tasks, tools, state, and objective artifact checks across candidates.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — Hermes runtime and the target environment for genuine end-to-end evaluation.
- [microsoft/SkillOpt](microsoft--SkillOpt.md) — separate standalone optimizer/harvest reference; not the same implementation as GBrain.
- [garrytan/gbrain](garrytan--gbrain.md) — reference index/query layer containing an independent TypeScript `skillopt` implementation.
- [yologdev/yoyo-evolve](yologdev--yoyo-evolve.md) — broader self-evolving-agent pattern source.
- [aiming-lab/MetaClaw](aiming-lab--MetaClaw.md) — heavier self-improving-agent/RL reference.

## Revisit criteria

Reconsider the parked disposition only when all of these are true:

1. The GEPA/writeback/full-file-validation repairs are merged into the default branch or included in a tagged release.
2. The configured size policy accepts the 42,116-character target without bypassing validation.
3. A clean install completes a real optimizer run and emits a non-empty changed `evolved_skill.md` plus reproducible dataset/config metadata.
4. The full reassembled skill passes structure/constraint checks and the repository's promised test/semantic gates.
5. A separate actual-Hermes evaluator verifies tool use and output artifacts on frozen baseline/candidate tasks; internal keyword-overlap scores are not accepted as proof.

## Commitment disposition

Evaluation only; reconsider only after the listed artifact and external-evaluation gates pass.
