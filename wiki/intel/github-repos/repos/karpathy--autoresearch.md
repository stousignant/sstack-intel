---
title: karpathy/autoresearch
type: repo-intel
source: https://github.com/karpathy/autoresearch
category: autonomous-research
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-24
license: README says MIT; GitHub API reports no license file
---

# karpathy/autoresearch

> Reference-stack fit as reviewed 2026-05-24; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- Usefulness score: `78/100` — very strong pattern source for autonomous experiment loops, but direct adoption is mostly blocked by GPU/training focus and the reference stack's Hermes/GBrain priorities.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-24:** `reference-only`.
- Review candidate: extract the experiment-loop pattern into Hermes/GBrain self-improvement design, not into a new training-research project yet.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 17/25 | The agent-loop/program-as-skill pattern maps well to Hermes dream cycles, repo-intelligence, and self-improvement. The actual workload is single-GPU LLM pretraining, not the reference stack's bottleneck. |
| Leverage | 22/25 | Excellent leverage idea: bounded experiments, objective metric, keep/discard branch discipline, overnight autonomous work. |
| Reuse readiness | 14/20 | Tiny repo and clear instructions, but requires NVIDIA GPU, CUDA/PyTorch stack, data prep, and likely H100-like assumptions for the default baseline. |
| Maturity/trust | 10/15 | Karpathy-authored, simple, wildly popular, but minimal tests, no formal release, and no detected LICENSE file despite README saying MIT. |
| Differentiation | 15/15 | Sharp demonstration of “research org code” as Markdown plus autonomous coding agent loops. Highly relevant as a design pattern. |

## Verdict

`karpathy/autoresearch` is less a tool to run by default than a compact manifesto and reference implementation for autonomous empirical improvement. The gold is not the toy nanochat trainer; it is the discipline: define a fixed evaluation harness, constrain the agent's edit surface, require commits per experiment, score every run, keep improvements, revert regressions, and let a bounded loop continue without repeated approval after scope and safety are set. That discipline is directly reusable for Hermes/GBrain self-improvement, repo-intelligence evals, and nightly dream-cycle experiments.

Direct adoption is low priority unless a stable CUDA machine and a small-LLM-training workload are available. Otherwise, distill the pattern into local agent workflows where a fixed eval and bounded edit surface address a demonstrated need.

## Reference-stack relevance

- Models the kind of **self-improving Hermes loop** favored by the reference lens: objective metric, bounded experiment, autonomous iteration, morning report.
- Reinforces that high-leverage autonomy requires a good **harness** more than a smarter prompt: fixed metric, constrained scope, branch hygiene, revert policy.
- Suggests a concrete template for GBrain/Hermes improvements: define eval questions, run changes in a sandbox, score retrieval/tool behavior, keep only measurable wins.
- `program.md` is basically a lightweight skill/agent charter, aligning with the reference stack's interest in skills, SOUL/instructions, and self-improvement loops.

## What it is

A tiny repo that lets an AI coding agent modify a single-file GPT/nanochat-style training script (`train.py`) and repeatedly run 5-minute single-GPU training experiments. The human edits `program.md`; the agent edits `train.py`; `prepare.py` provides fixed data/tokenizer/evaluation utilities. The metric is validation bits per byte (`val_bpb`), lower is better.

## Evidence checked

- GitHub metadata via API on 2026-05-24: `karpathy/autoresearch`, 83,109 stars, 12,072 forks, Python, created 2026-03-06, pushed 2026-03-26, 183 open issues, GitHub API license `null`.
- Inspected disposable upstream clone: commit `228791f` from 2026-03-25.
- Files inspected: `README.md`, `program.md`, `pyproject.toml`, `prepare.py`, `train.py`.
- Syntax smoke check: `python -m py_compile prepare.py train.py` passed locally.
- Runtime smoke test not attempted: the review environment could not communicate with the NVIDIA driver via `nvidia-smi`, and the repo's training path requires CUDA.

## Strengths

- **Excellent harness shape.** The repo deliberately keeps the editable surface tiny: `prepare.py` fixed, `train.py` editable, `program.md` as human-owned research-org code.
- **Objective metric.** `evaluate_bpb` computes bits per byte over a pinned validation shard, avoiding tokenizer-vocab comparability traps.
- **Time-boxed empirical loop.** Every experiment gets a fixed 5-minute wall-clock training budget, which makes local iteration possible and forces “good under this platform/time budget” optimization.
- **Agent-friendly branch discipline.** `program.md` instructs the agent to commit an experiment, run it, log TSV results, keep improved commits, and `git reset` regressions.
- **Simplicity criterion is explicit.** It tells the agent not to keep ugly complexity for tiny gains unless the improvement justifies it.
- **Good demonstration of Markdown-as-control-plane.** `program.md` is essentially a skill file for an autonomous researcher.

## Risks / caveats

- **Hardware mismatch.** Defaults are tested on H100 and require a single NVIDIA GPU. The review environment could not verify a working NVIDIA driver. Mac/AMD/Windows support is delegated to forks.
- **Not a general research platform.** It is intentionally a small toy/benchmark setup, not a broad AutoML or agent-lab framework.
- **No formal test suite.** Syntax checks pass, but correctness depends on actual CUDA training runs.
- **License ambiguity.** README says MIT, but the GitHub API reports no license and no `LICENSE` file was present in the inspected tree. Treat reuse as “probably intended MIT, but verify before copying substantial code.”
- **Metric can overfit the local harness.** The design optimizes for val_bpb under a 5-minute budget on one platform; the repo itself notes runs are not comparable across different compute.
- **Agent loop can burn compute.** The `NEVER STOP` instruction is appropriate for the toy setting but dangerous if copied blindly into broader Hermes automation without cost, safety, and scope limits.

## Integration ideas

- **Hermes dream-cycle eval harness:** define a small eval suite for nightly self-improvement, e.g. retrieval questions, tool-use discipline checks, skill-routing checks, second-brain note quality checks. Keep changes only if evals improve.
- **Repo-intelligence experiments:** treat repo-analysis templates/skills as `program.md`; run controlled variants over a fixed batch of repos; score against human-review criteria.
- **GBrain retrieval tuning:** create a TSV-like results log for query quality before/after sync/index/config changes.
- **Subagent/Kanban loops:** borrow the branch-per-experiment + append-only result log pattern for multi-agent workflows, but avoid “run forever” unless the cost and stop conditions are explicit.
- **Personal AI OS:** “fixed harness + objective metric + morning report” is a useful design pattern for self-improving routines, instead of vague reflection loops.

## Reusable patterns to keep

1. **Program file as skill:** the real product is the agent's operating manual, not only the code.
2. **Constrained edit surface:** give agents one or two files they may edit; keep the evaluator immutable.
3. **Objective score + revert policy:** commit every attempt, keep wins, discard regressions.
4. **Fixed budget:** compare attempts under a fixed time/compute/token/cost budget.
5. **Human-free loop after setup:** once scope and safety are set, the agent should not keep asking “continue?”
6. **Results ledger outside commits:** `results.tsv` remains untracked so experiment history survives without polluting the branch.

## Alternatives / related repos

- [garrytan/gbrain](garrytan--gbrain.md) — more directly relevant to the reference stack's memory/search layer; autoresearch's harness pattern could be applied to GBrain retrieval evals.
- [hesamsheikh/awesome-openclaw-usecases](hesamsheikh--awesome-openclaw-usecases.md) — complementary pattern source for proactive assistant workflows; autoresearch is more rigorous about measurable experiment loops.
- [SamurAIGPT/llm-wiki-agent](SamurAIGPT--llm-wiki-agent.md) and [atomicstrata/llm-wiki-compiler](atomicstrata--llm-wiki-compiler.md) — candidates for applying autoresearch-style bounded evals to generated knowledge workflows.

## Review candidates and context

- Distill the `program.md` autonomous experiment-loop pattern into Hermes dream-cycle / self-improvement design.
- Consider a small, no-GPU analogue: run agents against a fixed second-brain/retrieval eval suite instead of LLM pretraining.
- Do not attempt direct install/run until a CUDA machine with a working NVIDIA driver is available and model-training compute is explicitly authorized on model-training experiments.
