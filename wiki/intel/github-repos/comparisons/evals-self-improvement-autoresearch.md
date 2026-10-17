---
title: Evals / Self-Improvement / Autoresearch Repo Comparison
created: 2026-06-03
updated: 2026-06-03
type: comparison
tags: [github-repos, repo-intelligence, evals, autoresearch, self-improvement, hermes]
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/ZJU-REAL--SkillZero.md
  - wiki/intel/github-repos/repos/ai-boost--awesome-harness-engineering.md
  - wiki/intel/github-repos/repos/alvinreal--awesome-autoresearch.md
  - wiki/intel/github-repos/repos/mutable-state-inc--autoresearch-at-home.md
  - wiki/intel/github-repos/repos/yologdev--yoyo-evolve.md
---

# Evals / Self-Improvement / Autoresearch Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Related focused comparisons

- [Evaluating the configured Hermes harness](hermes-harness-evaluation.md) — October 2026 source-checked framework comparison, Harbor configuration constraints, and the smallest proposed first regression; no evaluation framework adopted or benchmark run.

- [Dream and repair workflow tools](dream-repair-self-improvement.md) — October 2026 evidence, complementary tool candidates, and the proposed responsibility-first rebuild; no tool trial or workflow change adopted.

## Executive recommendation

- **Start with eval tasks, not training:** the next Hermes and portable skills substrate should define workload-specific tasks, artifacts, graders, budgets, and keep/revert discipline before any optimizer/self-modification loop.
- **Best pattern source:** [yologdev/yoyo-evolve](../repos/yologdev--yoyo-evolve.md) for self-improvement ledger/memory/skill evolution discipline.
- **Best coordination pattern:** [mutable-state-inc/autoresearch-at-home](../repos/mutable-state-inc--autoresearch-at-home.md) for claims, dedupe, expiry, shared result ledgers, and swarm coordination.
- **Best discovery maps:** [ai-boost/awesome-harness-engineering](../repos/ai-boost--awesome-harness-engineering.md) and [alvinreal/awesome-autoresearch](../repos/alvinreal--awesome-autoresearch.md).
- **Research after measurement:** [ZJU-REAL/SkillZero](../repos/ZJU-REAL--SkillZero.md) is interesting only after the shared-skill source has evals/traces.

## Decision matrix

| Repo | Layer | Score | Verdict | Reference-stack use |
|---|---|---:|---|---|
| yologdev/yoyo-evolve | self-evolving agent | 88 | distill-pattern | Dream-cycle/evolution ledger patterns |
| ai-boost/awesome-harness-engineering | harness resource map | 86 | reference-only | Discovery index for eval/permission/memory/orchestration repos |
| alvinreal/awesome-autoresearch | autoresearch resource map | 84 | reference-only | Queue-shaping for future autoresearch loops |
| mutable-state-inc/autoresearch-at-home | collaborative autoresearch | 82 | distill-pattern | Claim/lease/result-ledger semantics |
| ZJU-REAL/SkillZero | agent RL/skill learning | 78 | distill-pattern | Research reference after evals/traces exist |
| Agent-Field/agentfield | backend observability | 76 | distill-pattern | Identity/audit/observability vocabulary |
| HKUDS/AutoAgent | agent framework/eval | 72 | distill-pattern | Comparison baseline/evaluation folder sampling |
| TinyAGI/tinyagi | persistent multi-agent ops | 72 | distill-pattern | Heartbeat/team/channel semantics |
| affaan-m/ECC | harness OS | 70 | watch | Inspect eval/security hooks only; no install |
| NirDiamant/agents-towards-production | production tutorials | 68 | reference-only | Topic checklist; custom-license caution |

## Category map

1. **Evaluation contract:** define small tasks and graders first.
2. **Self-improvement ledger:** record experiments, changes, metrics, keep/revert decisions.
3. **Collaborative long-running work:** use claims, leases, expiry, dedupe, heartbeat, shared results.
4. **Skill learning/training:** defer until evals and trace redaction exist.
5. **Backend observability:** borrow identity/audit language without overbuilding Kubernetes-scale infra.

## Reference-stack recommendation

Next concrete move: create a small **Hermes eval suite** before adding more self-improvement machinery. Good first tasks:

- repo-intelligence note quality,
- GBrain retrieval accuracy,
- skill routing correctness,
- second-brain cleanup safety,
- coding edit/test/doc pass discipline,
- cron/dream-cycle report usefulness,
- long-running task resumability.

Then wire self-improvement runs to a ledger: proposal → bounded run → artifacts → eval result → keep/revert → commit.

## Open questions

- Where should the eval suite live: the shared-skill source, second-brain, or a Hermes plugin? Wikic remains a deterministic compiler/doctor rather than an eval-suite owner.
- Which evals can be deterministic enough to run nightly without model-judge noise?
- How should Hermes redact traces before using them for improvement/training?
- What is the smallest claim/lease/result-ledger schema that works for Discord-started long-running tasks?
