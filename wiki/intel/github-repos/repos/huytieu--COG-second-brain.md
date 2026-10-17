---
type: concept
title: huytieu/COG-second-brain
source: https://github.com/huytieu/COG-second-brain
aliases:
  - COG-second-brain
  - "GitHub repo: huytieu/COG-second-brain"
category: self-improving-agent-harness
topics: [github-repo, second-brain, agent-harness, verification, skills]
status: deep-analyzed
usefulness_score: 75
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-08-12
license: MIT
---

# huytieu/COG-second-brain

> Reference-stack fit as reviewed 2026-08-12; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `75/100` — unusually strong verification and skill-distribution ideas, but its advertised closed-loop harness is incomplete at release `v3.10.0` because required templates and installer files are absent.
- **Recommendation:** `distill-pattern`
- **Usage observed 2026-08-12:** `reference-only`.
- **Confidence:** `high`
- **Review candidate:** Mine only the V-model evidence-ledger, review-cockpit, and cross-model-verifier semantics; do not clone COG as a second vault or install its full skillpack.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22/25 | Its Markdown/Git/Obsidian model and verification-first agent workflows map closely to the reference stack, but COG would duplicate the canonical vault, Hermes skills, GBrain, and SStack. |
| Leverage | 22/25 | The AC-to-evidence traceability, independent verifier, risk lanes, retro, harvest, and living review document can improve trust and review efficiency. |
| Reuse readiness | 11/20 | MIT and multi-harness packaging help, but the runnable closed-loop path references six absent framework files and fails during checkpoint initialization. |
| Maturity/trust | 7/15 | Active releases and 848 stars are positive; one dominant maintainer, no SECURITY.md, no conventional CI/test suite, and a validator that misses broken runtime references materially reduce trust. |
| Differentiation | 13/15 | The V-model evidence ledger plus “worker never grades its own homework” and one-document review cockpit are crisp, transferable patterns. |
| **Total** | **75/100** | High-value pattern library; not a credible active-runtime or vault replacement today. |

## Verdict

COG is interesting because it packages several ideas the reference lens values into a coherent operating model: falsifiable acceptance criteria, task-to-criterion traceability, independent read-only verifiers, artifact-level post-condition checks, risk-scaled ceremony, retrospectives, and human-approved learning promotion. The right move is still **not adoption**. The reference architecture already has the stronger ownership boundaries—Hermes as cockpit, SStack as reviewed infra, GBrain as index/query layer, GitHub as execution state, and the second-brain as canonical knowledge. Installing COG would create a parallel vault and duplicate skills. More importantly, the current release's flagship closed-loop workflow is not runnable from a clean clone because its own scripts and skills reference templates and an installer that are not shipped.

## Reference-stack relevance

- **Independent evidence contract:** COG formalizes “the worker never grades its own homework” as read-only verifier agents receiving artifact paths and emitting evidence rows tied to `AC-n` IDs.
- **One review surface:** `review-cockpit` proposes a living Markdown control document linking all deliverables, statuses, approvals, and decision logs—useful for multi-item Hermes/Discord work where review bandwidth is the bottleneck.
- **Cross-model gate placement:** it uses a different model family at spec, integration, acceptance, and ship boundaries for high-stakes work, rather than spraying multi-model review everywhere.
- **Human-gated learning:** `harvest` stages corrections, facts, process lessons, and skill gaps, but requires approval before durable knowledge or skill changes—aligned with SStack's reviewed-evolution north star.

## What it is

COG (“Cognition + Obsidian + Git”) is an MIT-licensed starter vault and agent skillpack. It ships 33 skills and 10 agent definitions, with first-class Claude Code and Antigravity surfaces, an Agent Plugins 1.0 mirror, and smaller Kiro/Gemini/Cursor/Codex surfaces. Its scope spans personal capture, briefings, PM workflows, people CRM, research, content/design, and a V-model verification harness.

## Evidence checked

- **GitHub metadata:** 848 stars, 103 forks, MIT, created 2025-10-15, pushed 2026-08-07, latest release `v3.10.0` published 2026-08-07; 3 open issues and 5 open PRs when checked. [Source: GitHub API, 2026-08-12]
- **Maintenance:** GitHub returned 61 commits in the first 100-commit page and five listed contributors, dominated by `huytieu`; releases `v3.6.0` through `v3.10.0` were published between June and August 2026. [Source: GitHub commits/contributors/releases APIs, 2026-08-12]
- **Packaging validator:** `./scripts/validate-agent-surface.sh` passed with 0 warnings; it verifies JSON manifests, mirrored skills, documented commands, versions, and packaged surface counts. [Source: clean disposable clone, 2026-08-12]
- **Shell parse:** `bash -n` passed for `cog-update.sh`, `scripts/validate-agent-surface.sh`, `checkpoint.sh`, and `lane-classify.sh`. [Source: local smoke test, 2026-08-12]
- **Classifier smoke:** production deploy classified `full`; typo classified `tiny`. [Source: local smoke test, 2026-08-12]
- **Critical harness smoke failure:** `checkpoint.sh init <disposable-project>` exited 1 because `04-projects/harness/templates/evidence-ledger.md` does not exist. Also absent: `SPEC-template.md`, `session-review.md`, `retro.md`, `report.html`, and `install-harness.sh` in the upstream Claude library, despite references in `closed-loop`, `retro`, `review-cockpit`, and `WORKFLOW.md`. [Source: clean `v3.10.0` clone and local test, 2026-08-12]
- **Security/CI:** no root `SECURITY.md` was found; GitHub Actions API exposed only a dynamic Copilot code-review workflow, while no conventional test workflow is shipped in `.github/workflows/`. [Source: GitHub API and repository tree, 2026-08-12]
- **Key files inspected:** `README.md`, `WORKFLOW.md`, the upstream Claude `SKILL.md` files for closed-loop, harvest, retro, review-cockpit and memory-hygiene, the upstream Claude `task-verifier.md` agent, the upstream Claude `checkpoint.sh` and `lane-classify.sh` library scripts, `cog-update.sh`, and `scripts/validate-agent-surface.sh`.
- **Repomix:** not generated; a direct clean clone plus targeted file and runtime inspection provided stronger evidence.

## Strengths

- **Traceability is explicit:** every non-trivial criterion gets an ID, task mapping, independent verification row, and acceptance evidence before ship.
- **Verification observes artifacts:** the verifier contract rejects worker self-report and asks for files, re-fetched issues, URLs, commands, or screenshots.
- **Ceremony scales with risk:** tiny/normal/full/bug/backfill lanes avoid forcing a huge process onto trivial work.
- **Review cockpit is human-centered:** one editable document is a better approval UX than scattered files and chat fragments.
- **Distribution discipline is real:** the packaged Agent Plugins mirror and manifests are synchronized, and the shipped packaging validator actually passed.
- **Upgrade script has useful safeguards:** dry-run/check modes, per-file interaction, backups, fixed framework allowlist, and post-update packaging validation.

## Risks / caveats

- **Flagship workflow is broken in a clean release:** the documentation describes a complete closed loop, but required templates and installer artifacts are absent. This is not a minor documentation gap; checkpoint initialization fails immediately.
- **Validator checks packaging, not operability:** its clean pass gives false confidence about the harness because it does not verify referenced files or run a minimal workflow smoke test.
- **No substantive automated test/CI surface:** shell syntax and packaging consistency are not enough for a repo claiming self-healing and verification-first behavior.
- **Single-maintainer concentration:** contributor evidence shows the project is primarily maintained by one person; community growth is recent.
- **Security posture is underdeveloped:** no root security policy was found despite skills that can publish, execute mutations, access work systems, and update framework files.
- **Broad prompt supply chain:** direct install imports 33 large skills and agent instructions; these should be reviewed selectively, not trusted because the repo is MIT or popular.
- **Update safety is incomplete:** dirty worktrees are warned about rather than blocked; `--force` overwrites an extensive allowlist (with backups), and the current allowlist can drift from newly introduced framework dependencies.
- **README hype exceeds proof:** “zero maintenance,” “95%+ source accuracy,” “self-healing,” and “actually self-evolves” are source claims without a visible reproducible evaluation suite.

## Integration ideas

- Add an **AC ↔ task ↔ evidence** traceability table only for high-stakes or multi-item SStack/Hermes work; keep normal chat lighter.
- Distill a **review cockpit** template for sessions with multiple user approvals, but route executable state to GitHub rather than creating another persistent tracker.
- Reuse the **cross-model gate placement** rule: spend the different model at spec quality and final acceptance/ship, where divergent reasoning has the most leverage.
- Extend repo/skill validators with a deterministic **referenced-path + minimal smoke-test gate**; COG itself demonstrates why manifest parity alone is insufficient.
- Keep harvest semantics aligned with current SStack policy: propose corrections/process lessons/skill patches, validate, review, then commit—never silent self-mutation.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — the reference stack's active cockpit and tool runtime.
- [garrytan/gbrain](garrytan--gbrain.md) — active knowledge index/query layer; COG should not replace it with another vault-centric retrieval model.
- [fivetaku/fablize](fivetaku--fablize.md) — narrower, more measurable completion-gate pattern suited to selective distillation into an existing owner.
- [cobusgreyling/loop-engineering](cobusgreyling--loop-engineering.md) — stronger operational loop/readiness pattern source with runnable tooling.
- [NousResearch/hermes-agent-self-evolution](nousresearch--hermes-agent-self-evolution.md) — Hermes-native candidate-generation/eval lane for actual self-improvement.

## Review candidates and context

No new executable issue recommended. The most reusable COG ideas substantially overlap existing SStack acceptance-criteria, self-improvement, cross-model review, and loop-engineering doctrine. Revisit only if upstream ships the missing harness assets plus an end-to-end CI smoke test, or if a concrete need arises for a focused review-cockpit experiment.
