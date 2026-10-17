---
title: kayba-ai/agentic-context-engine
type: repo-intel
aliases: [Agentic Context Engine, Kayba ACE, ACE Skillbook]
source: https://github.com/kayba-ai/agentic-context-engine
category: agent-self-improvement
topics: [github-repo, repo-intelligence, context-engineering, skill-evolution, trace-learning]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-02
license: Apache-2.0
---

# kayba-ai/agentic-context-engine

> Reference-stack fit as reviewed 2026-10-02; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `84/100` — strong structured learning-record and reflection patterns, with automatic mutation, incomplete benchmark reproduction and privacy/isolation boundaries that limit direct adoption.
- **Recommendation:** `distill-pattern`, not an install or runtime-learning approval.
- **Usage:** `reference-only`; no installation, active integration or benchmark reproduction claimed.
- **Confidence:** medium. Pinned implementation inspected; code syntax parsed, but tests, provider behavior, model outputs and claimed performance were not exercised.

## Scorecard

| Factor | Points | Evidence and judgment |
|---|---:|---|
| General fit | 24/25 | Trace-derived strategies and structured context records transfer to agent learning without model-weight training. |
| Leverage | 23/25 | Reusing outcome-linked lessons could reduce repeat failures; the potential is architectural, not a measured local gain. |
| Reuse readiness | 15/20 | Concrete Python API, pipeline stages, examples and integration adapters; runtime skillbook records are not versioned filesystem skills. |
| Maturity/trust | 10/15 | Apache-2.0, recent beta release and offline CI configuration; incomplete benchmark harness, permissive execution/file boundaries and docs drift. |
| Differentiation | 12/15 | Provenance, outcome observations, scoped atomic entries and retrieval offer more substance than generic reflection advice. |
| **Total** | **84/100** | High pattern value with a separate production-adoption gate. |

## Verdict

Preserve ACE as a concrete design reference for evidence-linked runtime memory and candidate generation. Its strongest transferable asset is the learning record and trace → evaluation → reflection separation. Its standard updater is deliberately automatic: mutation occurs before its audit output returns. A review-gated adaptation must make the learner propose a candidate instead, then separately validate and apply the accepted change. This repository does not establish that its automatic loop safely improves a canonical skill library. [Sources: [Skillbook](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/core/skillbook.py#L292-L341), [UpdateStep](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/steps/update.py#L11-L23).]

## Reusable intelligence

### A Skillbook is runtime memory, not a filesystem skill library

A `Skill` has a stable ID, `context` or `harness` section, issue/applicability text, keywords, optional actionable insight, active state, timestamps, usage and helpful/harmful/neutral counters, embeddings and trace-linked occurrences. Context entries require an insight; harness entries can omit it. These are records injected into prompts, not automatically authored `SKILL.md` packages. Counters represent observations, not calibrated efficacy or causal attribution. Source records may preserve trace identity, sample question, error identification and learning text. [Sources: [schema](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/core/skillbook.py#L292-L341), [InsightSource](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/core/insight_source.py#L107-L150).]

CRUD includes ADD/UPDATE/TAG/REMOVE; removal deactivates a record, while purge deletes it. Retrieval helpers combine BM25, dense ranking and keyword overlap. JSON save/load and optional embedding sidecars provide explicit persistence; an in-memory update does not itself prove a durable save. No encryption layer was found in this inspected persistence path. [Sources: [CRUD](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/core/skillbook.py#L473-L549), [persistence](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/core/skillbook.py#L686-L734), [retrieval](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/implementations/skill_rendering.py#L70-L182).]

### Separation exists, but approval does not

The ordinary learning path is AgentStep → EvaluateStep → ReflectStep → UpdateStep. Environment feedback is optional; absent an environment, reflection can still proceed from the output and available sample fields. ReflectStep does not mutate the book. SkillManager then receives the live book and calls mutation tools directly. UpdateStep returns a post-hoc operation record, not a proposal awaiting application. Standard learning-tail composition contains no external proposal queue, human approval, holdout acceptance or rollback gate. [Sources: [runner](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/runners/ace.py#L40-L94), [evaluation](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/steps/evaluate.py#L9-L46), [mutation tools](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/implementations/sm_tools.py#L171-L256), [learning tail](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/steps/__init__.py#L50-L87).]

### Scope and atomicity heuristics worth studying

The SkillManager prompt prefers one trigger/action per entry, updating near-duplicates rather than adding copies, concrete applicability, evidence-only tagging and narrow rules before general ones. Its cross-trace broadening heuristic asks for at least three confirming surface instances across two domains, a runtime-filled slot, API-independent action and verifiable trigger. It retains contributing narrow entries during that pass and explicitly rejects harmful-count-only deletion. These are model instructions—not deterministic enforcement or proof of generalization. The exact numeric thresholds are an upstream heuristic, not a proposed universal policy. [Source: [prompt](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/implementations/prompts.py#L392-L494).]

### Deduplication is less automatic than its naming suggests

At this revision, DeduplicateStep obtains a similarity report and logs it. It does not apply consolidation operations. Separate MERGE/DELETE/KEEP/UPDATE application helpers exist, but the inspected standard step does not call them. Search-before-add and near-duplicate updating remain SkillManager prompt behaviors. Default embedding dedup configuration uses LiteLLM with `text-embedding-3-small`; local sentence-transformers is optional. Thus deduplication can transmit strategy text externally unless routing is deliberately constrained. [Sources: [standard step](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/steps/deduplicate.py#L14-L52), [standalone operations](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/deduplication/operations.py#L78-L162), [defaults](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/protocols/deduplication.py#L12-L23).]

## Evaluation evidence and limits

The README reports Claude Haiku 4.5 learning 15 strategies on a Tau2 training split without reward signals, then improving held-out consistency. The committed chart reports pass^1 41.2% → 52.5% and pass^4 20.0% → 40.0%. These are project-reported results, not independently reproduced here; doubled pass^4 is not a claim of doubled accuracy across all tasks. The graphic lacks run IDs, per-task results and uncertainty estimates. The configs offer some model/split context but do not independently prove the reported run setup. [Sources: [README](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/README.md#L140-L148), [chart](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/benchmarks/tasks/tau_bench/Tau2Benchmark%20Result%20Haiku4.5.png), [config](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/benchmarks/tasks/tau_bench/default.yaml#L1-L21).]

Documented runner files `scripts/run_benchmark.py` and `scripts/run_tau_benchmark.py` are absent at the pinned revision. The `ace-eval` gitlink references `19e09d23738b6aadffc37e8c7e1f53bed453b977`; the research fetch of its repository returned “Repository not found.” Private/deleted/inaccessible remains unknown. The live `test_sm_tau_retail.py` harness learns from and replays the same three task indices: useful plumbing evidence, not a held-out generalization test. Do not present it as reproducing the README chart. [Sources: [benchmark README](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/benchmarks/README.md#L7-L20), [submodule](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/.gitmodules), [live harness](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/test_sm_tau_retail.py#L320-L383).]

Tests cover store operations, pipeline/step plumbing, providers, recursive reflection and MCP. CI declares Python 3.12 on Linux, Windows and macOS, excluding API-requiring tests. Existence/configuration is not a verified passing run. [Sources: [core tests](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/tests/test_ace_core.py), [CI](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/.github/workflows/test.yml#L10-L47).]

### Relation to the ACE paper

The linked paper describes Generator → Reflector → Curator, with itemized deltas merged by non-LLM logic. The current repository instead has a tool-calling SkillManager mutate the live book. Its Tau2 graphic is distinct from the paper's AppWorld/finance results. Neither architecture supplies human approval by default. The paper discusses degradation from noisy or harmful feedback, which motivates a separate acceptance boundary; it does not prove such a boundary exists here. [Source: [ACE paper v3](https://arxiv.org/html/2510.04618v3), §§3, A.4 and limitations.]

## Risks / caveats

- **Learning contamination:** traces and model reflection are untrusted inputs. Without external acceptance, plausible but wrong lessons can influence future prompts. This is a risk inference, not an exploit finding.
- **Privacy:** provenance may retain sample questions and error text. Configured LLM/embedding providers receive analysis inputs. Optional Kayba trace uploads and tracing are separate hosted paths, not requirements of the local store. Logfire's configured scrubbing callback explicitly preserves reasoning, answers, message content, payment IDs and tool arguments/responses. Review egress before providing private traces. [Sources: [Logfire](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/observability/__init__.py#L27-L70), [cloud upload](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/cli/cloud.py#L285-L307).]
- **Execution isolation:** recursive TraceSandbox uses restricted Python execution in the current process, not OS/container isolation. SIGALRM timeout enforcement is limited to Unix main-thread paths. It is not a demonstrated security boundary for hostile generated code. [Source: [sandbox](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/core/sandbox.py#L612-L688).]
- **MCP filesystem boundary:** inspected server defaults to stdio with `safe_mode=False`, save/load allowed and no skillbook root. Path confinement requires explicit root configuration. [Sources: [config](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/integrations/mcp/config.py#L5-L21), [handlers](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/integrations/mcp/handlers.py#L287-L339).]
- **Docs drift:** roles documentation says Reflector tags skills; the current Reflector documents pure analysis and mutation/tagging belongs to SkillManager. Prefer current wiring over role prose. [Sources: [roles docs](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/docs/concepts/roles.md#L41-L70), [Reflector](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/ace/implementations/reflector.py#L25-L37).]
- **License/maturity:** main package is Apache-2.0, Python >=3.12, beta version 0.13.0; the tracing SDK declares MIT. The changelog records the main license change. No root SECURITY.md was found; this is not a full dependency/security audit. [Sources: [manifest](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/pyproject.toml#L5-L16), [SDK manifest](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/sdk/python/pyproject.toml#L5-L20), [changelog](https://github.com/kayba-ai/agentic-context-engine/blob/3a319831785ede6ba4a3a4002756233095c59e17/CHANGELOG.md#L10-L22).]

## Strengths

- Structured, serializable learning records with source occurrences instead of an opaque growing summary.
- Reflector/updater separation creates a useful seam for a proposal-only adapter.
- Atomicity, narrow applicability, search-before-add and evidence-only tagging heuristics are concretely specified.
- Provider/integration adapters and tests offer implementation reference beyond README claims.

## Pattern-distillation proposal

This is a proposed adaptation, **not an ACE feature or an implementation commitment**:

1. Preserve stable lesson ID, applicability, one actionable insight and source evidence; distinguish external outcome evidence from model self-assessment.
2. Let reflection produce a candidate operation/diff against a copy, with no canonical-write access.
3. Evaluate the candidate against baseline, triggering cases and held-out regression cases; broadening/removal requires evidence and consumer checks, not raw counters.
4. Apply accepted changes through the existing versioned review/delivery owner; retain exact evidence and a forward-only rollback path.

## Evidence checked

- **Pinned revision:** `3a319831785ede6ba4a3a4002756233095c59e17`; parent independently verified upstream main still resolved to it. [Commit](https://github.com/kayba-ai/agentic-context-engine/commit/3a319831785ede6ba4a3a4002756233095c59e17).
- **Metadata snapshot:** 2,585 stars, 311 forks, last push September 24, 2026; Apache-2.0. Attention is not independent adoption evidence. [Repository API](https://api.github.com/repos/kayba-ai/agentic-context-engine).
- **Inspection:** README, design/concept docs, manifests, Skillbook/provenance/retrieval, evaluation/reflection/update/dedup wiring, prompts, providers, recursive sandbox, observability/cloud/MCP boundaries, tests, CI and benchmark artifacts. Research checked 44 source files; parent directly rechecked the updater, dedup step, generalization prompt, Logfire callback, missing runner paths and gitlink.
- **Static probe:** parent parsed all 80 Python modules under `ace/` with `ast.parse`: PASS. This does not import or execute ACE and is not a smoke test.
- **Not run:** installation, pytest, live inference, embedding calls, benchmark reproduction or security exploit testing.
- **DeepWiki/repomix:** not used; pinned clone and selective source inspection sufficed. Disposable research artifacts remain outside the vault.

## Alternatives / related repos

- [RRSI](google-research--rrsi.md) — complementary acceptance/regularization of full harness edits; ACE focuses on accumulated runtime context records.
- [SkillOpt](microsoft--SkillOpt.md) — narrower optimization/evaluation of skills; compare targets and acceptance rather than assuming interchangeable systems.
- [Anthropic skill-creator](anthropics--skills-skill-creator.md) — skill-file authoring and eval lifecycle rather than a runtime-memory learner.
- [Hermes Agent self-evolution](nousresearch--hermes-agent-self-evolution.md) — runtime-native evolution reference, distinct from ACE's external Skillbook substrate.

## Evaluation boundary

- Source analysis and review candidates only; no runtime integration is implied.

## Review candidates

1. **Proposal-only reflection seam:** can structured candidate operations improve lesson quality without canonical-write access? Promote only after a small copied-fixture trial shows useful output and preserved authority.
2. **Evidence-linked lesson records:** can provenance/applicability improve review and retrieval without duplicating a truth store? Promote only when a concrete existing owner and retrieval failure are identified.
3. **Acceptance and anti-contamination evaluation:** can a fixed baseline/holdout set reject harmful broadening and repeated failure overfitting? Promote only after task definitions and evaluation cost are bounded.

## Commitment disposition

Not promoted to executable work. Ingestion records evidence and non-binding candidates only; no installation, integration, learner activation or new task tracking authorized.
