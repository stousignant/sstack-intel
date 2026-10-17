---
title: ayghri/i-have-adhd
type: repo-intel
source: https://github.com/ayghri/i-have-adhd
category: agent-communication
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-09-29
created: 2026-09-29
updated: 2026-09-29
license: MIT
tags: [agent-skills, communication, accessibility, productivity, evals]
---

# ayghri/i-have-adhd

> Opinionated reference-stack evaluation, reviewed 2026-09-29. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- **78/100 — distill-pattern; reference-only; high evidence confidence.** A small, inspectable output-style skill with useful communication and evaluation patterns; prefer selective reuse over importing a global behavior overlay.
- Evidence confidence concerns implementation and checks, not medical effectiveness or guaranteed model-quality improvement.
- Navigation: [GitHub repo intelligence](../index.md).

## Scorecard
| Factor | Points | Evidence-based rationale |
|---|---:|---|
| Stack fit | 21/25 | Portable Markdown communication rules; no native Hermes adapter verified. |
| Leverage | 20/25 | Reduces answer-finding and task-start friction; much overlaps ordinary concise assistant behavior. |
| Reuse readiness | 17/20 | Small MIT skill, explicit exceptions, local hooks, broad installation documentation. |
| Maturity / trust | 10/15 | 70 local tests pass; no published release; unpinned install routes and limited efficacy evidence. |
| Differentiation | 10/15 | Better-than-average state-reporting rules and candid paired evals; not novel runtime infrastructure. |

## Verdict
Preserve as a communication-pattern and eval-design reference, not as another runtime dependency. The useful payload is answer-first presentation, bounded steps, visible completion, and keeping concise output subordinate to safety and completeness. Do not import diagnostic assumptions, unconditional time estimates, or pressure to name an unproven error cause. Ingestion does not activate the skill or authorize installation.

## Reusable intelligence
The canonical [skill](https://github.com/ayghri/i-have-adhd/blob/839872f9d1cd634fed642b4589ce7226199cc15f/skills/i-have-adhd/SKILL.md) has ten rules: lead with action, number multi-step work, finish open work with one next action, suppress tangents, restate task state, give concrete estimates, make completion visible, report errors plainly, keep visible lists small, and omit filler. It explicitly exempts detailed explanations, safety, ambiguity, task contracts, and higher-priority harness instructions. Its list cap is presentation guidance, not an analysis/completeness limit.

Explicit invocation and session persistence are separate from opt-in always-on hooks. The inspected [Node hook](https://github.com/ayghri/i-have-adhd/blob/839872f9d1cd634fed642b4589ce7226199cc15f/hooks/always-on.mjs) checks a local opt-in flag, reads the bundled skill, strips frontmatter, and emits prompt text; it has no network calls or persistent writes. Failure does not block session start. Shell and PowerShell variants and OpenCode/Pi adapters are included; every advertised runtime was not live-tested.

The [recorded eval report](https://github.com/ayghri/i-have-adhd/blob/839872f9d1cd634fed642b4589ce7226199cc15f/evals/RESULTS.md) covers 14 cases and three trials per condition. It reports weighted scores 4.045 baseline versus 4.473 candidate and blockers 7 versus 3, but **fails its own zero-blocker release gate**. A no-tools agent-owned-edit case is acknowledged as unpassable; another regression confidently names an unsupported cause. These are upstream-reported response-quality results, not rerun here and not clinical evidence. Same-family judging and three trials limit generalization.

## Evidence checked
- Snapshot: `839872f9d1cd634fed642b4589ce7226199cc15f`, remote main checked; last push September 19, 2026. GitHub API observed September 29: **52,158 stars**, **3,004 forks**, MIT; no published releases returned. Popularity is adoption interest, not effectiveness evidence.
- Discovery snapshot observed 50,574 stars and 2,916 forks; the later API observation is higher, but the earlier observation time was not independently established, so no growth rate is claimed.
- Inspected README, canonical skill and Cursor mirror, install guide, manifests, hooks, tests, eval harness/results, contribution rules and GitHub workflow. Direct selective source inspection was sufficient; no DeepWiki or repomix pack was needed.
- Review used a disposable source checkout and temporary evidence report, not installed runtime artifacts.
- Parent rerun: `PYTHONDONTWRITEBYTECODE=1 python3 -m unittest discover -s tests` — **70 tests passed**. Fixture tests emit expected simulated judge-failure messages; suite result is OK. No installation/provider-backed eval was run.
- Parent rerun: `python3 scripts/run_evals.py validate` and `python3 scripts/run_scenario_eval.py validate evals/scenarios/persistence-topic-switch-stop` — passed. Checkout stayed clean.
- Commit signature was not authenticated locally because its signing key was unavailable; pinned identity is not a verified signature.

## Strengths
- Small, readable core rather than a new service or store.
- Rules preserve safety, completeness, explanations, and harness priority.
- Concrete state-reporting and low-friction next-action patterns.
- Candid failed-gate reporting and paired eval plumbing support critical reuse.

## Risks / caveats
- The skill contains broad uncited statements about ADHD and assumes a reader diagnosis in its body. Treat this as source rhetoric, not established medical fact or user identity; README says no diagnosis is needed.
- Cause-and-fix formatting can manufacture certainty. Preserve unknown causes explicitly. Time estimates must be grounded, not invented to satisfy a style rule.
- [Installation routes](https://github.com/ayghri/i-have-adhd/blob/839872f9d1cd634fed642b4589ce7226199cc15f/INSTALL.md) commonly reference moving branches or external installers; pin and review before any trial.
- [Maintainer automation](https://github.com/ayghri/i-have-adhd/blob/839872f9d1cd634fed642b4589ce7226199cc15f/.github/workflows/claude.yml) triggers on comments containing `@claude`, passes an OAuth secret, grants `id-token: write`, and uses mutable action tags. No commenter allowlist is visible in this workflow; action-internal controls were not evaluated. This is an upstream maintenance risk, not proof the local style hook exfiltrates data.
- Unit tests prove hook/harness behavior, not durable model compliance or compatibility across all advertised hosts.

## Alternatives / related repos
- Existing host communication preferences are the lowest-dependency alternative when the desired rules already fit.
- [Anthropic skill-creator](anthropics--skills-skill-creator.md) for broader skill evaluation/lifecycle mechanics.
- [Addy Osmani agent skills](addyosmani--agent-skills.md) for task/workflow structure rather than a presentation overlay.

## Operating boundary
Personalized recommendations remain in the ingest chat; no private health inference, adoption-state update, or active runtime change was made.

## Review candidates
1. **Optional communication distillation:** review answer-first/state-first wording against existing preferences. Promote only if a repeated observed gap warrants a scoped change; avoid another skill merely to repeat established style.
2. **Uncertainty-preserving style eval:** compare partial-success and unknown-cause responses with/without a small candidate prompt. Promote only with explicit bounded trial scope; never equate brevity with correctness.

## Commitment disposition
Not promoted. No GitHub task, installation, or behavior activation follows automatically from ingestion.
