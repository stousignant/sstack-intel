---
title: pingchesu/hermes-curator-evolver
type: repo-intel
created: 2026-10-06
updated: 2026-10-06
aliases: [Hermes Curator Evolver, curator-evolver]
source: https://github.com/pingchesu/hermes-curator-evolver
category: hermes-self-improvement
topics: [github-repo, hermes, skill-governance, evidence, rollback]
status: deep-analyzed
usefulness_score: 81
recommendation: watch
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-06
license: MIT
---

# pingchesu/hermes-curator-evolver

> Reference-stack evaluation as reviewed 2026-10-06; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness:** 81/100 — a concrete evidence/proposal/promotion pattern source, not demonstrated agent-performance improvement.
- **Recommendation:** `watch`; study guarded application and reviewer-only mining, rather than enabling unattended edits.
- **Usage observed 2026-10-06:** `reference-only` — the review did not install/activate the plugin, schedule maintenance, make model calls or mutate canonical skills.
- **Confidence:** medium. Source boundaries are inspectable, but live Hermes integration, full tests, crash/concurrency safety and behavioral efficacy were not exercised.

## Scorecard

| Factor | Points | Evidence-based rationale |
|---|---:|---|
| General fit | 23/25 | Native Hermes hook/plugin and local evidence surfaces. |
| Leverage | 21/25 | Makes candidate evidence, stale-target checks and recovery inspectable. |
| Reuse readiness | 17/20 | Small default dependency set, CLI, manifests, examples and tests; scheduling needs separate authority. |
| Maturity/trust | 10/15 | MIT, CI/test fixtures and recent maintenance; small ecosystem and important recovery limits. |
| Differentiation | 10/15 | More concrete promotion/rollback mechanics than reflection-only loops; not an efficacy evaluator. |
| **Total** | **81/100** | Judgment, not a benchmark or install score. |

## Verdict

Preserve this project as a watched pattern source. Its strongest assets are separation of evidence capture from reviewer-only candidate mining, source-provenance eligibility, exact-content checks and backups. The default bootstrap is an automation setup, not a passive reporting command: it enables daily bounded updates. An external source-owned skill tree is intentionally ineligible for unattended mutation. That is a useful boundary, not a reason to bypass it through manual targeting.

## Reusable intelligence

### Observation and candidate lane

The [manifest](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/plugin.yaml) and [registration](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/__init__.py) register post-tool, post-LLM and session-end hooks plus an evidence-report tool. [Hooks](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/hooks.py) collect tool arguments/results and turn/session metadata into [local SQLite storage](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/storage.py). Storage bounds previews, but truncation is not secret redaction: compact tool arguments and user/assistant text can still be sensitive.

The [candidate miner](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/candidates.py) classifies supplied redacted snippets into memory, existing/new skill, replay-benchmark or ignore records. Its constructor rejects auto-apply and requires review. This is a local review queue, not memory/skill writeback or a canonical work tracker. The heuristics include explicit workflow, error, ephemeral-state and source-dump patterns; confidence numbers are heuristic, not measured probabilities.

### Mutation and ownership

[Source classification](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/skill_sources.py) resolves paths and checks external roots before bundled/hub/local membership. External, bundled, hub and unknown sources are non-writable for unattended updates. Remaining local paths are classified as local-agent-created; that label is a filesystem/provenance inference, not cryptographic proof of original authorship. Missing or malformed source metadata warrants independent review.

[Auto-evolution](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/auto_evolve.py) defaults to dry-run and requires both apply-low-risk and auto-approval for actual writes. It appends/replaces a managed evidence block, can spill support into references, protects core/channel-bound skills, and offers up to four deterministic variants. These variants score local safety/quality signals; selecting one does not establish better future task behavior. Restore-drill enforcement is optional by default.

[Guarded apply](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/guarded_apply.py) requires approval and an expected SHA-256, snapshots prior content, writes a manifest, and restores the target if configured verification fails. Rollback refuses a subsequently changed target unless forced. Manual target application is not the same source-eligibility gate as unattended auto-evolution.

### October 3 maintenance delta

Pinned revision `1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd` moves databases/backups/logs outside the install tree into profile-aware `plugin-data/curator-evolver`. [Paths](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/hermes_curator_evolver/paths.py) use Hermes' supported storage API when importable and refuse nonempty or broken-symlink legacy state rather than silently moving a live SQLite database. [Regression fixtures](https://github.com/pingchesu/hermes-curator-evolver/blob/1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd/tests/test_state_location.py) check unchanged install fingerprints, explicit overrides and offline migration. This directly addresses install-tree hashing/dependency synchronization interference; fixtures were inspected, not run.

## Evidence checked

- Parent GitHub REST snapshot, October 6, 2026: **44 stars, 5 forks, MIT**; last push/commit **October 3, 2026**. Small popularity is an ecosystem-confidence limit, not disproof of code value. No independently verified adoption/efficacy signal was established.
- Immutable source archive at `1aab2a9a7f80b0cd33ec4998e4067c6f355f6ffd`; package/manifest version 0.10.0, while package `__version__` remains 0.8.0. Version drift is a maintenance caveat.
- README, manifest, pyproject, registration, hooks/storage, paths, skill_sources, auto_evolve, candidate miner, guarded_apply, CI and state-location/conftest fixtures inspected.
- **Static check:** Python AST parsing succeeded for all **40 Python files** in the archive. This proves parseability only.
- DeepWiki not used; primary code/docs were sufficient. No repomix generated: small pinned archive was inspected selectively instead.
- No upstream test suite, bootstrap, scheduler, plugin runtime or model-dependent benchmark run. The reviewed pinned archive is upstream evidence; the findings here do not depend on a local artifact.

## Strengths

- Candidate mining has explicit review-only invariants instead of silently promoting text.
- Source-aware unattended eligibility, backup manifests and stale-target refusal are concrete code mechanisms.
- Install code and mutable runtime state are separated, with migration refusal and regression fixtures.

## Risks / caveats

- **Verification can be absent:** `_run_verify(None, ...)` returns disabled-but-passed. Staged structural checks and behavioral commands are configurable; an applied receipt alone is not efficacy or even configured-check proof.
- **Not transactional:** hash-check followed by normal file write is not an atomic compare-and-swap or concurrency lock. Do not claim race/crash safety from the SHA guard.
- **Support-file boundary:** auto_evolve writes reference spillover after guarded target application and records post-write snapshots. Main-file rollback restores SKILL.md; it does not restore/delete all prior support-file content. Restore drills and full-package rollback are different claims.
- **Shell authority:** verification runs operator-provided strings with `shell=True`; commands must be trusted and scoped. Approval flags are operator assertions, not an independent authorization service.
- Default bootstrap adds a separate scheduler; optional semantic/model paths add dependency/provider/data exposure. Local storage does not remove private-evidence or prompt-injection risk.
- No measured improvement, independent security audit, or broad adoption was reproduced. Test existence is not test success.

## Alternatives / related repos

- [ryonakae/hermes-self-improvement](ryonakae--hermes-self-improvement.md) — broader evidence/planner/editor/outcome loop, but greater mutation surface and weaker general rollback.
- [nousresearch/hermes-agent-self-evolution](nousresearch--hermes-agent-self-evolution.md) — offline optimizer, not this evidence/promotion lane.
- [hermes native self improvement](../comparisons/hermes-native-self-improvement.md) — bounded comparison.

## Evaluation boundary

This note records reusable evaluation evidence, not confidential operating policy, runtime installation or project state.

## Review candidates

- Rank 1 — inspect evidence-only mining as an optional adapter; question: does it replace real manual evidence collection? Promotion requires a separately authorized redacted-fixture trial and attributable useful output.
- Rank 2 — compare exact-revision promotion and recovery receipts against the existing source-change owner; question: is any safety mechanism genuinely missing? Promote only a specific demonstrated gap, not a competing editor.
- Rank 3 — monitor package-level rollback, mandatory configured verification and held-out Hermes behavior evidence; revisit direct adoption only after those boundaries improve.

## Commitment disposition

Not promoted to executable work. Ingestion/watch is not installation, recurring monitoring, scheduler or mutation authorization.
