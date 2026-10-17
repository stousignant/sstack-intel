---
title: google-research/rrsi
type: repo-intel
aliases: [RRSI, Regularized Recursive Self-Improvement of Agent Harnesses]
source: https://github.com/google-research/rrsi
category: agent-self-improvement
topics: [github-repo, repo-intelligence, harness-evolution, evaluation, regularization]
status: deep-analyzed
usefulness_score: 87
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-02
license: Apache-2.0
---

# google-research/rrsi

> Reference-stack fit as reviewed 2026-10-02; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `87/100` — unusually relevant research on keeping harness self-improvement generalizable, cost-aware and auditable rather than growing unmeasured complexity.
- **Recommendation:** `distill-pattern`; study the selection and evidence contracts, not a runtime replacement.
- **Usage:** `reference-only`; no installation, benchmark run, runtime activation or implementation of its patterns is claimed.
- **Confidence:** medium. Pinned source and paper inspected; research results remain author-reported and were not reproduced.

## Scorecard

| Factor | Points | Evidence and judgment |
|---|---:|---|
| General fit | 24/25 | Frozen-model harness evolution includes prompts, skills, memory, tools and control flow; reusable beyond one provider. |
| Leverage | 24/25 | Explicit hypotheses, cost gates, leakage review and removal pressure address common failure modes of self-improving agents; local outcome gains unmeasured. |
| Reuse readiness | 15/20 | Small Python selection/history modules and documented domain adapters; full runs require model access and benchmark environments. |
| Maturity/trust | 11/15 | Apache-2.0, source-mapped method and offline tests; fresh research implementation, incomplete token telemetry treatment, unsupported-product boundary and unbounded dependency version ranges. |
| Differentiation | 13/15 | Regularizes the trajectory of open-ended harness edits rather than restricting optimization to one prompt or training model weights. |
| **Total** | **87/100** | High pattern value, not an adopt-now maturity score. |

## Verdict

Preserve as a research and design reference for evaluation-gated harness evolution. Its strongest asset is the rule for deciding whether a change earns its complexity and inference cost, coupled to a recorded hypothesis and explicit anti-overfitting checks. Adapt those contracts into an existing owner only after a bounded baseline/holdout evaluation; do not add a parallel runtime or authorize production self-modification based on the paper. The repository is not an officially supported Google product. [Sources: pinned README, selection and critic modules below.]

## Reusable intelligence

RRSI evolves the scaffolding around a frozen model, not model weights. The repository supplies coding, document-work and engineering-design domain adapters. Proposals may change prompts, configuration, context management, tools, skills, memory and subagents. Candidate harnesses live in Git worktrees; accepted candidates advance an incumbent branch, preserving a concrete code revision. [Sources: [README](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/README.md), [gitops.py](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/rrsi/gitops.py).]

### Proposal regularization and evidence history

An annealed edit budget limits independent mechanisms bundled into one candidate. The proposer receives edit history and explicit component/hypothesis tags. Stalled search redirects reserved proposal slots toward components not yet measured. The history stores per-edit records, including score/cost deltas and outcomes. However, all edits in a bundle inherit the same candidate-level measurement; that is not causal component attribution. `replace_round` can rewrite a round's records, so this implementation is not an immutable audit ledger. [Sources: [history.py](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/rrsi/history.py), [propose.py](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/rrsi/propose.py).]

### Leakage screen before expensive evaluation

The critic combines deterministic deny patterns with an LLM diff review. It targets suite-specific constants/answers, grader gaming, undeclared bundled mechanisms, task-specific runtime memory leakage, disabled safeguards and unbounded work. Runtime correctness is explicitly deferred to compile/constructor/smoke checks. This is an anti-overfitting screen, not a complete security audit or proof that arbitrary generated code is safe. [Source: [critic.py](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/rrsi/critic.py).]

### Noise-aware and cost-aware acceptance

The admissibility floor is `S' >= S* - delta`, where `S*` is the best observed score. This is **not strict monotonic improvement**. Gains greater than the noise band must satisfy a relative policy-token budget `delta_C <= beta0 + beta1 * delta_S`. Inside the band, a weighted score/cost/structural-novelty expression must be positive, and the same best-score floor still applies. A flat or slightly lower score versus the current incumbent can therefore be admissible. Domain guards can reject otherwise admissible candidates; the winner is the highest-scoring admissible candidate. Structural novelty concerns component categories, not arbitrary diff size. [Source: [selection.py](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/rrsi/selection.py).]

Missing rewards are represented as zero by the domain scoring adapters, preventing failed trials from simply disappearing from the score denominator. Cost has a weaker contract: `aggregate` averages only observed positive token counts, and `relative_cost_change` returns zero when either side has no usable estimate. **Missing token telemetry is not a verified cost saving; it can bypass cost pressure.** A port should make telemetry coverage an acceptance requirement or explicitly mark cost evidence unknown. [Source: [evaluate.py](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/rrsi/evaluate.py).]

### Pruning is a proposal directive, not automatic deletion

`History.prune_set` flags previously measured components whose best recent score delta is non-positive. An empty recent measurement window has yield `-inf` and also qualifies: stale positive evidence can age out. The output identifies accepted machinery for the proposer to remove; it does not itself delete code. Combined with shared bundle measurements, this argues for targeted ablation and consumer checks before porting pruning into a skill library. [Source: [history.py](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/rrsi/history.py).]

## Reported research results and limits

The paper was first submitted September 21, 2026; v2 is dated September 23, 2026. It reports out-of-distribution gains up to 4.7 percentage points and a workspace comparison with about 30% fewer policy tokens than unregularized evolution. The 14.1-point Terminal-Bench headline is the separate Gemini 3.5 Flash experiment; the main Claude Opus 4.8 coding gain is 6.0 points. These are author-reported comparisons, not a local replication. **Policy tokens per trial are not the total search bill**: proposals, analysis, critic review, repeated evaluation and discarded candidates add cost. [Source: [paper v2](https://arxiv.org/html/2609.24972v2).]

The experiments use frozen backbones and finite evolve sets. Transfer and results depend on the task distribution and hyperparameters; broader architectures, tools and long-run behavior require validation. Leakage screening is helpful but does not eliminate adaptive overfitting. Do not equate the result with autonomous model-weight improvement, open-ended intelligence growth, or guaranteed improvement on unrelated personal workflows. [Source: [paper](https://arxiv.org/abs/2609.24972).]

## Evidence checked

- **Pinned revision:** `be50316e1db05914068a973f322770ef08ed7ba1`; parent independently confirmed it remained `main` on October 2, 2026. [Commit](https://github.com/google-research/rrsi/commit/be50316e1db05914068a973f322770ef08ed7ba1).
- **Metadata snapshot:** 1,198 stars, 111 forks; repository created September 16, 2026; last push September 23, 2026; Apache-2.0. Snapshot from [GitHub repository API](https://api.github.com/repos/google-research/rrsi). Attention is not evidence of independent adoption or benchmark reproduction.
- **Docs/source:** README, pyproject, selection, critic, history, evaluate, propose, gitops, domain documentation/configurations and core tests. Parent directly rechecked selection/critic during initial triage and evaluate/history/manifest during ingestion.
- **Paper:** abstract and v2 HTML; result magnitudes and metric boundaries cross-checked against repository documentation.
- **Local execution:** no upstream code, test suite, benchmark or model API was run. This is a source-analysis ingest, not a smoke-tested adoption.
- **Offline test feasibility:** `tests/test_core.py` declares a no-API/no-benchmark core suite, covering selection/calibration/history/components. Python >=3.10 and pytest >=7 are declared. Feasible for a later explicitly bounded trial, not verified here. [Sources: [tests](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/tests/test_core.py), [manifest](https://github.com/google-research/rrsi/blob/be50316e1db05914068a973f322770ef08ed7ba1/pyproject.toml).]
- **DeepWiki/repomix:** not used. Targeted source inspection was sufficient; fetched source copies are disposable scratch evidence, not vault artifacts.

## Strengths

- Concrete implementation links for the mathematical method, reducing the gap between paper and code.
- Pre-evaluation leakage checks and bounded repair attempts avoid paying for obviously invalid candidates.
- Explicit score/cost/novelty decisions and re-adjudication support make selection inspectable.
- Exploration and pruning counter the tendency to accumulate increasingly elaborate scaffolding without measuring its contribution.

## Risks / caveats

- **Compute:** two candidates per round, repeated trials and full evolve-set evaluation; domain configurations use 20 or 40 rounds and 2 or 4 trials per task. Full runs need Vertex/model access and domain benchmark environments. No spend estimate or run is authorized by this ingest.
- **Isolation:** worktrees and path-jailed proposer access are not a uniform process sandbox. Coding documents Docker; engineering documents bwrap/no-network isolation. Verify the actual domain boundary before running generated harness code.
- **Telemetry:** unknown token cost is treated as zero relative change; reject unsupported claims of cost efficiency in any adaptation.
- **Attribution:** bundle-level deltas do not prove an individual component helped or hurt; stale evidence can produce pruning pressure.
- **Dependencies:** manifest dependencies have lower bounds without upper bounds; do not install into an active runtime without pinned dependency/security review.
- **Support:** fresh research code, not an officially supported Google product; README excludes it from Google's OSS vulnerability rewards program. Apache-2.0 at the repository level does not establish rights/access for external benchmark data.

## Alternatives / related repos

- [Anthropic skill-creator](anthropics--skills-skill-creator.md) — narrower skill authoring/evaluation lifecycle reference; RRSI is about broader harness evolution.
- [SkillOpt](microsoft--SkillOpt.md) — related automated skill optimization evidence; compare optimization targets and acceptance contracts rather than treating tools as interchangeable.
- [Hermes Agent self-evolution](nousresearch--hermes-agent-self-evolution.md) — adjacent runtime-native evolution reference; RRSI contributes regularization and transfer-evaluation semantics rather than a shipped Hermes integration.
- [Prime Agent](primeintellect-ai--prime-agent.md) — adjacent continual-refinement runtime and control-plane reference; distinct from this research loop.

## Evaluation boundary

- Research evaluation only; no runtime adoption or skill change follows from this note.

## Review candidates

Non-binding; none are implementation commitments:

1. **Hypothesis-to-evidence contract.** Rationale: distinguish proposed improvement from demonstrated value. Review question: can each candidate carry a declared mechanism, baseline, unfamiliar-task check and acceptance reason? Promotion condition: a bounded existing-owner experiment with explicit evaluation criteria.
2. **Cost/noise admission policy.** Rationale: prevent false wins and expensive complexity. Review question: what minimum telemetry coverage and score uncertainty make the rule defensible? Promotion condition: complete comparable baseline/candidate cost and quality evidence.
3. **Consumer-aware pruning.** Rationale: retain useful removal pressure without equating missing recent measurements with uselessness. Review question: can targeted ablation and live-consumer checks establish removal safety? Promotion condition: bounded reversible removals with independent outcome evidence.

## Commitment disposition

Not promoted. This ingest preserves research and ranked review questions only; no GitHub issue, implementation obligation, runtime adoption or star mutation is created.

## Navigation

- [GitHub Repo Intelligence](../index.md) — canonical cross-repository rollup.
