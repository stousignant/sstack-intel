---
type: concept
title: fivetaku/fablize
usage: reference-only
source: 'https://github.com/fivetaku/fablize'
status: deep-analyzed
topics:
  - github-repo
  - claude-code-harness
  - verification
  - agent-harness
  - runtime-overlay
aliases:
  - fablize
  - GitHub repo: fivetaku/fablize
license: MIT claimed in README; no recognized root license file
category: claude-code-harness
last_reviewed: '2026-06-19T09:56:31Z'
checked_ref: d338460454c340736c16648df0920ca9eea6acea
recommendation: distill-pattern
score_confidence: high
usefulness_score: 88
ingested_via: 'mcp:put_page'
ingested_at: '2026-06-18T23:05:06.267Z'
source_kind: 'mcp:put_page'
---

# fivetaku/fablize

> Opinionated reference-stack evaluation, reviewed 2026-06-19. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `88/100` — excellent fit as a verification/finish-the-work harness pattern, with real hook code and script-level tests; direct adoption is Claude Code-specific and overlaps with Hermes/SStack runtime authority.
- **Recommendation:** `distill-pattern`
- **Usage observed 2026-06-19:** `reference-only`.
- **Confidence:** `high`
- **Review candidate:** Extract the strongest patterns into Hermes/SStack review-gated self-improvement and completion-proof work: observation-led Stop gates, deep-only verification blocking, bounded anti-loop caps, and out-of-band holdout measurement.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Targets common completion failures across Hermes/Codex/Claude workflows: unfinished work, missing artifact verification, and unsupported completion claims. Claude Code plugin packaging means it is not a drop-in Hermes feature. |
| Leverage | 23/25 | High leverage for reducing fake-done / early-stop behavior and for improving agent trustworthiness. The measurement-first framing is especially useful for SStack self-evolution. |
| Reuse readiness | 17/20 | Small Python/shell repo with readable hooks, skills, setup scripts, and tests. Direct install should stay sandboxed because it mutates Claude Code plugin/always-on behavior. |
| Maturity/trust | 13/15 | Very new repo, but actively updated, released v2.1.0, has focused tests, and exposes honest limits. Caveat: GitHub license API did not recognize a root license file despite README's MIT claim. |
| Differentiation | 12/15 | Strongest differentiator is the explicit split between transferable procedure and non-transferable model capability, plus out-of-band measurement of whether the harness helps or hurts. |
| **Total** | **88/100** | Pattern source, not active-runtime adoption. |

## Verdict

fablize is a high-signal Claude Code plugin/harness for completing work with evidence: route task-specific packs, block unverified completion after meaningful code changes, and measure gate effects outside model context. Direct installation into a shared Claude/Hermes workflow is not a default because its hooks and setup scripts alter runtime behavior, while existing Hermes/SStack completion procedures may already cover that need. Preserve the gate and measurement semantics as patterns; do not import the control plane without a demonstrated gap.

## Workload fit

- It encodes a strong agent-completion contract: do the work, run the artifact, verify with tool output, and do not claim completion without evidence; procedure cannot manufacture model capability.
- The repo's strongest reusable idea is not “make Opus into Fable”; it is **measurement-gated harness engineering**: only ship behavioral constraints that have evidence, and measure whether gates create net harm via context noise.
- Its out-of-band holdout/shadow design is relevant to Hermes self-evolution: candidate skill/procedure patches should be measured with real outcome signals, not just vibes.
- The early-stop and observation-gate semantics can improve Codex/Claude worker lanes under Hermes supervision without adding another project-management substrate.

## What it is

fablize is a Claude Code plugin from `fivetaku/fablize` that packages a `fablize` skill, UserPromptSubmit/PostToolUse/Stop hooks, setup/uninstall scripts, and Python gate/shadow utilities. README claims it was built from a Fable-vs-Opus comparison and ships only procedure-level behaviors judged transferable: verification grounding, multi-story completion/evidence gates, systematic investigation, early-stop prevention, and per-task routing.

## Evidence checked

- GitHub metadata: 474 stars, 71 forks, Python primary language, created 2026-06-14, pushed 2026-06-18, latest release `v2.1.0` published 2026-06-18. GitHub license API returned `null`.
- README: documents install via Claude plugin marketplace, honest limits, transferable vs non-transferable behavior, and MIT badge/claim.
- Plugin manifest: `.claude-plugin/plugin.json` declares version `2.1.0`, a `fablize` skill, and harness keywords.
- Hook config: `hooks/hooks.json` wires `UserPromptSubmit`, `PostToolUse`, and `Stop` hooks.
- Skill definition: `skills/fablize/SKILL.md` includes multi-story goals, investigation protocol, verification grounding, working style, and capability-ceiling escalation.
- Measurement protocol: `docs/MEASUREMENT_PROTOCOL.md` defines out-of-band `events.jsonl`, holdout ON/OFF, outcome signals, stratified comparison, and sunset criteria.
- Key implementation inspected: `hooks/gate_stop.py`, `tests/test_gate.py`, `tests/test_gate_robustness.py`, `CHANGELOG.md`.
- Local smoke test: cloned to a disposable source-inspection workspace; running `python3 -m pytest -q` produced a pytest collection internal error because test files call `sys.exit()` at import time, but exit code was 0. Running each test script directly succeeded: gate, robustness, recovery, shadow M3/M4, and shadow checks all passed.
- repomix pack: not generated; direct clone and targeted file inspection were sufficient for a single runtime-overlay repo.

## Strengths

- **Honest capability boundary:** README explicitly says a harness cannot raise model ceiling; it can only enforce transferable procedures. This avoids the usual “prompt magic” lie.
- **Observation-led gate:** `gate_stop.py` blocks only when ledger evidence shows a meaningful non-quick/non-docs task changed files without observed successful verification, with fail-open behavior.
- **False-positive control:** v2.1.0 changelog says the gate became deep-only and change-aware, with max two blocks to avoid infinite traps.
- **Out-of-band measurement:** measurement protocol keeps logging outside model context and includes holdout sessions to test whether the gate itself hurts outcomes.
- **Runnable tests:** direct script test run passed all included gate, robustness, recovery, and shadow checks.

## Risks / caveats

- **Runtime authority:** Claude Code hooks can influence every prompt/tool/stop cycle; this belongs in a disposable/sandbox profile before any real always-on install.
- **Very young repo:** created 2026-06-14, so maintenance and community trust are not proven despite fast star growth.
- **License caveat:** README and badge claim MIT, but there is no recognized root license file in the cloned tree and GitHub returned `licenseInfo: null`.
- **Pytest incompatibility:** tests are executable scripts, not clean pytest modules; `python3 -m pytest -q` hits collection internal errors because tests call `sys.exit()` at import time. Direct script execution works.
- **Claude-family measurement scope:** README says the underlying comparison is small and Claude-family-specific; treat effect-size claims as project-local evidence, not universal proof.

## Integration ideas

- Distill the observation-gate rule into SStack/Hermes acceptance criteria: “changed executable artifact + no observed verification = cannot claim done,” with narrow scope and caps.
- Reuse the out-of-band holdout design for Hermes skill/procedure changes: candidate gate ON vs OFF, outcome signals from git/session transcripts, and sunset if no lift.
- Compare fablize's gate semantics against the reference “finish the job” doctrine; avoid duplicating naggy prompt text when a deterministic or post-hoc checker is cleaner.
- Use as a benchmark for Codex/Claude worker-lane control: small hook, explicit evidence, fail-open, measured impact.

## Alternatives / related repos

- [Yeachan-Heo/oh-my-claudecode](Yeachan-Heo--oh-my-claudecode.md) — broader Claude Code team-orchestration/runtime overlay; fablize is narrower and more measurement-focused.
- [obra/superpowers](obra--superpowers.md) — mature multi-harness procedural skill set; fablize is more hook/gate specific.
- [Chachamaru127/claude-code-harness](Chachamaru127--claude-code-harness.md) — another Claude Code harness with lifecycle/security emphasis.
- [NousResearch/hermes-agent-self-evolution](nousresearch--hermes-agent-self-evolution.md) — Hermes-native self-improvement loop where fablize-style measurement gates could be useful.

## SStack upgrade review — 2026-06-19

### Bottom line

- **Adopt the method, not the plugin.** `fivetaku/fablize` is still a strong pattern source for SStack/Hermes/Codex worker discipline, but direct runtime adoption remains wrong by default because it installs Claude Code hooks and setup scripts into the user's agent loop.
- **Highest-leverage steal:** a deterministic, ledger-backed completion gate: if a deep task changed executable files and no successful verification was observed, the agent cannot claim done. Prose doctrine alone is not enforcement; fablize shows a concrete automation pattern.
- **Best measurement idea:** out-of-band ON/OFF holdout plus post-hoc outcome signals. This could inform a future self-evolution measurement suite, not become an always-on hook yet.
- **Source review is not mutation authority.** Any durable procedure change needs a separately scoped, reviewed source update.

### What was checked

- Upstream metadata via `gh repo view fivetaku/fablize`: 479 stars, 72 forks, Python, latest release `v2.1.0`, pushed `2026-06-18T13:34:53Z`, license API `null`.
- Upstream HEAD: `6ebd6e409a44e77b3bd5514880ecbbf734490f2e` — `Merge pull request #3 from fivetaku/measurement-infra`.
- Tree sampled: `.claude-plugin/*`, `hooks/*`, `scripts/gate/*`, `scripts/shadow/*`, `scripts/goals.py`, `skills/fablize/SKILL.md`, `docs/MEASUREMENT_PROTOCOL.md`, tests.
- Local test verification from fresh clone at a disposable source-inspection workspace: direct script tests passed for gate, robustness, recovery, shadow, M3, and M4. `pytest` remains the wrong harness because tests are executable scripts.
- Comparison lens: evidence-first controller verification, a single executable work owner, and separately reviewed runtime activation. These are reference-architecture preferences, not upstream efficacy evidence.

### Capability comparison

- Keep the controller/verifier separate from bounded workers; a worker report is not proof.
- Missing verification stays unknown or failed.
- Prefer a small evidence-producing checker before a global runtime hook.
- A holdout and outcome signals test whether discipline improves results or merely adds context noise.
- Runtime hooks require separate security, authority and rollback review.

### Upstream findings worth preserving

1. **Observation-led Stop gate.** `scripts/gate/verify_state.py` blocks only when `mode == "deep"`, files changed, the task is not docs-only, and no successful verification was observed. It caps blocks at `MAX_STOP_BLOCKS = 2` and emits a warning instead of infinite nagging.
2. **Fail-open hook design.** `hooks/gate_stop.py` catches exceptions and exits `0`, preserving the user's work loop if the gate breaks.
3. **Out-of-band holdout.** `docs/MEASUREMENT_PROTOCOL.md` treats measurement as external to the model context, with a 20% OFF holdout and outcome signals such as reverts, reinstructions, rework commits, wall time, failed verifications, and final defects.
4. **Harness paradox as first-class risk.** The measurement doc explicitly asks whether the gate worsens outcomes through context noise. This is the right skepticism for SStack self-improvement.
5. **Story ledger with final verification gate.** `scripts/goals.py` persists multi-story work in `.fablize/`, requires evidence for completion, and refuses the final story without `--verify-cmd` + `--verify-evidence`.
6. **Promise-no-act detector.** `hooks/finish-the-work.sh` catches final answers that end with “I will/let me/now I'll…” work promises without a tool call, guarded by `stop_hook_active`.

### Reusable disposition

- Deep changed executable files without observed verification warrant a scoped completion checker, with docs-only exemption, fail-open hook behavior and a two-block cap.
- Preserve out-of-band ON/OFF measurement, outcome signals and sunset criteria.
- Do not make `.fablize/` a competing canonical tracker; reuse the final-story verification invariant at the established work owner.
- Promise-without-action detection is a post-hoc/lint candidate before a global hook; false positives matter.
- Global plugin adoption is not justified by this source review: hook authority and the unresolved license-file signal remain.

### Pinned revision history

- Previous reviewed ref: `6ebd6e409a44e77b3bd5514880ecbbf734490f2e`.
- Current checked ref: `d338460454c340736c16648df0920ca9eea6acea` — `docs(changelog): tidy setup wording`.
- GitHub showed a force-update between reviews. Pin source rather than relying on branch continuity.

### Current smoke evidence

Fresh clone: a disposable source-inspection workspace at `d338460454c340736c16648df0920ca9eea6acea`.

Direct-script tests run:

- `python3 tests/test_gate.py` — PASS; caught changed-code/no-test and failed-test/claimed-success fake-done cases while allowing honest verification, docs-only, quick/no-change, and promise-no-act handoff cases.
- `python3 tests/test_gate_robustness.py` — PASS; empty/bad JSON fail-open checks, `stop_hook_active` loop guard, two-block cap, deep-only behavior, and no-change deep analysis pass-through.
- `python3 tests/test_recovery.py` — PASS.
- `python3 tests/test_shadow_m3.py` — PASS.
- `python3 tests/test_shadow_m4.py` — PASS; stratified ON/OFF, harness-paradox delta, sunset expiry, and no deep→effort false wiring.
- `python3 tests/test_shadow.py` — PASS; holdout/off and out-of-band checks.

`tests/test_shadow_checks.py` existed in the prior reviewed shape but is absent at current HEAD; `tests/test_shadow.py` is the current equivalent. Generic pytest collection remains the wrong harness because these are executable scripts.

### Better next suggestions

1. **SStack low-risk automation:** build a tiny reusable checker script under the owning skill or `scripts/` that consumes task depth, changed-file, docs-only and observed-verification fields and emits allow/warn/block. Keep it repo-local/dry-run first; do not hook it globally.
2. **Pilot lane:** wire the checker into one high-value worker lane with repeated fake-done risk — best candidate is a repo-local closeout/pre-merge checker, not Hermes global chat. The checker should run after file-changing work and before final report/PR closeout.
3. **Measurement slice:** if we pilot the checker, predeclare a 20% OFF holdout or at least a before/after golden set. Track reverts, reinstructions, rework commits, failed verifications, and wall time. Sunset after a fixed sample if it does not reduce fake-done/rework.
4. **Promise-without-action lint:** consider a post-hoc transcript lint before adding any runtime Stop hook. It is useful, but more false-positive-prone in Discord because final answers often contain legitimate next-step offers.
5. **Do not adopt `.fablize/` as task management.** If multi-story evidence is needed, map the invariant to GitHub Issues/Project 2/CCPM closeout instead: final story/checkpoint requires command + evidence.
6. **Only sandbox-install the plugin** in a disposable Claude Code profile if the goal is to study Claude Code hook ergonomics. It is not needed for the distilled workflow improvement.
