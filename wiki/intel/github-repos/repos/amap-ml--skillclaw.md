---
title: AMAP-ML/SkillClaw
aliases: [SkillClaw]
type: repo-intel
source: https://github.com/AMAP-ML/SkillClaw
category: self-improving-agents
topics: [github-repo, hermes, skill-evolution, collective-learning]
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-06
license: MIT
---

# AMAP-ML/SkillClaw

> Opinionated reference-stack evaluation, reviewed 2026-10-06. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `78/100` — real Hermes adapter and substantial collective skill-evolution machinery, tempered by unsafe proxy defaults, ownership gaps and weak behavioral validation.
- **Recommendation:** `distill-pattern`; an isolated comparative trial is a review candidate, not adoption or execution authorization.
- **Confidence:** medium overall; high for inspected source behavior, unknown for operational compatibility and improvement efficacy.
- **Usage:** `reference-only`; no installation, proxy activation, shared-store configuration or live skill mutation.

## Scorecard

| Factor | Points | Evidence |
|---|---:|---|
| Stack fit | 22/25 | Procedural learning and real Hermes endpoint integration fit skill-based agents; another model proxy and ungoverned library writer introduce ownership friction. |
| Leverage | 22/25 | Cross-session evidence aggregation and candidate evolution could reduce manual maintenance; saved effort and task improvements remain unmeasured. |
| Reuse readiness | 13/20 | Python CLI, adapters, local storage, configuration backups and version activation exist; isolation and policy-safe integration still require work. |
| Maturity/trust | 9/15 | MIT, substantial source/tests and lint CI, but no GitHub releases, broad proxy exposure defaults and no demonstrated behavioral efficacy. |
| Differentiation | 12/15 | Packages capture, evolution, shared distribution and idle validation; shared libraries alone are not unique. |
| **Total** | **78/100** | Knowledge/pattern value, not a deployment readiness score. |

## Verdict

SkillClaw is a credible implementation to study rather than merely a self-improvement README. Unlike a documentation-only compatibility claim, its Hermes adapter actually rewrites model routing to a local OpenAI-compatible proxy. The collective layer aggregates recorded sessions and creates or edits skill assets through a separate evolver and shared registry. However, publication and synchronization are not equivalent to reviewed Git delivery, and its optional validation is not an independent end-to-end agent evaluation. Preserve the architecture and test it only in an isolated, explicitly authorized environment before considering replacement of an existing maintenance component.

## Reusable intelligence

### Integration and the two loops

The task-time proxy forwards model traffic, appends an available-skills catalog and records session experience. The post-task evolution service supports a `workflow` engine (default) and an `agent` engine. The workflow path summarizes sessions, aggregates evidence, chooses changes and generates candidates. The agent engine delegates editing to an OpenClaw-based workspace with self-validation instructions; Hermes client support does not mean a Hermes-native evolution engine.

`_configure_hermes` sets `model.provider=custom`, `model.base_url` to a loopback OpenAI-compatible `/v1` endpoint at the configured port, a served model name and proxy key in the default Hermes-home `config.yaml`, and clears provider-specific API mode. It makes configuration backups and offers inspection/restore functions. This is an endpoint/configuration adapter, not a native Hermes plugin, and source presence is not a locally verified integration. Adapter paths are computed from `Path.home()`; a named Hermes profile alone must not be assumed to isolate its writes. The Hermes configuration bridge selects the Hermes-local skill root; generic dataclass and CLI defaults differ.

Sources: [adapter](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/claw_adapter.py#L472-L603), [configuration bridge](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/config_store.py), [workflow engine](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/evolve_server/engines/workflow.py), [agent workspace](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/evolve_server/engines/agent_workspace.py).

### Publication, synchronization and rollback are separate contracts

For the ordinary object-storage workflow, `publish_mode=direct` is the evolver default. `validated` optionally stages jobs for client validation; it is not necessarily human review. The separate Nacos registry defaults to `nacos_publish_mode=review`, with draft/review/direct lifecycle choices. These backend-specific defaults must not be conflated.

Sharing is off by default. When enabled, polling defaults to `poll` at 30-second intervals; session close also schedules a pull. The ordinary object-store `pull_skills` defaults to full mirror mode, deleting local skill directories missing from a nonempty remote manifest. It has backup/rollback safety for failed pulls and treats empty manifests as a no-op. Subset pulls force incremental mode, preserving unrelated extras. These mitigations do not make successful destructive synchronization appropriate for a separately owned skill library.

Version activation can select an earlier shared skill revision, while Hermes configuration restoration recovers routing. Neither should be described as universal rollback of the whole deployment, private trace storage, concurrent local edits or other configuration changes. No `external_dirs` provenance/owner exclusion was found in the inspected source. Filesystem/path safety tests are not a skill-source authority policy.

Sources: [evolver defaults](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/evolve_server/core/config.py#L98-L125), [pull semantics](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/skill_hub.py#L555-L840), [proxy close/poll behavior](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/api_server.py#L1989-L2128), [Nacos hub](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/nacos_skill_hub.py).

### Optional validation is narrower than behavioral proof

The optional workflow verifier is an LLM review of candidate text and summarized motivating evidence. It is disabled by default (`use_skill_verifier=False`), with candidate/current-skill clipping limits. It does not execute the agent's task.

The optional client replay validator generates baseline and candidate responses and scores them with a PRM. It accepts a candidate when its mean score clears the configured threshold and is at least the baseline mean; equality can pass. It evaluates at most three cases. Those cases come from the same `sessions` supplied to candidate evolution, preferring turns without tool calls/results. `_run_replay_branch` passes system/user text to an LLM chat call; it does not reproduce Hermes tool execution or the original environment. This is useful candidate screening, not a held-out, tool-grounded regression gate.

The agent engine's self-validation requirements are instructions plus evidence files. Inspected tests check that the instructions contain validation wording; that does not independently prove runtime enforcement, workspace confinement or successful learning. Benchmark/paper efficacy claims were not reproduced in this ingest.

Sources: [optional verifier](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/evolve_server/pipeline/skill_verifier.py), [replay case construction](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/evolve_server/engines/workflow.py#L490-L555), [client validator](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/validation_worker.py#L119-L237), [instruction tests](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/tests/test_agent_evolver_self_validation.py).

### Privacy, network exposure and model cost

Proxy defaults are `0.0.0.0` and an empty API key. The authentication checker returns without checking credentials when no expected key is configured. Set loopback binding and explicit authentication for any authorized experiment; the integration's loopback client URL does not constrain the server's listening interfaces.

Local recording defaults on. With sharing enabled and session storage configured, closing a session uploads the full captured turn records even when the periodic upload interval is zero. Records can contain user/assistant text, available reasoning content, tool calls and raw tool results. A local object-store backend is available, so collective machinery need not require cloud storage; subsequent LLM/PRM/evolution calls still require separate provider/privacy and cost approval. Disabling record files alone must not be assumed to disable in-memory session collection or shared uploads. Logs can also contain response text.

Sources: [proxy/sharing defaults](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/config.py#L50-L136), [auth](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/api_server.py#L1822-L1829), [turn capture](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/api_server.py#L2442-L2520), [session upload](https://github.com/AMAP-ML/SkillClaw/blob/3938f7537645c961d94498a0a79fc0a977019595/skillclaw/api_server.py#L3050-L3110).

## Evidence checked

- Reviewed revision: `3938f7537645c961d94498a0a79fc0a977019595`, current `main` checked 2026-10-06; commit/push timestamp `2026-08-17T08:48:07Z`.
- GitHub API snapshot: 2,669 stars, 265 forks, MIT; no GitHub releases returned. `pyproject.toml` declares package version `0.4.0`; this is not a GitHub release.
- Read README, manifest, configuration/bridge, Hermes adapter, proxy capture/auth/close/pull logic, object-store and Nacos lifecycle, workflow/validation/verifier paths, agent workspace/instruction tests and lint workflow. Direct source clone supersedes external summaries for this analysis.
- Inspected tests cover recording, path safety, bundle support, cloud reload, session uploads and self-validation wording. Tests were read, not executed.
- **Static check:** standard-library `ast.parse` succeeded for 77 Python files across `skillclaw`, `evolve_server` and `tests`. Parsing does not prove imports, packaging, tests or runtime behavior.
- Pinned source was inspected in a disposable clone; no source code imported or executed and no raw clone retained as authored knowledge.
- Repomix: not generated; binary absent and a no-install npm probe found no cached package. Used pinned direct source and targeted reads rather than downloading another execution dependency.
- No installation, upstream test run, model call, benchmark reproduction, proxy startup, registry write, private-session replay or runtime activation. This ingest grants none of those operations.

## Strengths

- Real Hermes endpoint adapter with configuration backup/inspection/restore.
- Captured experience is separable from skill assets; workflow and agent engines support different evolution approaches.
- Local storage and optional review/validation paths permit contained experiments in principle.
- Bundled skill assets, version history, reload and client validation are concrete implementation surfaces rather than only marketing.

## Risks / caveats

- Unsafe proxy exposure/auth defaults; transcript and log privacy require explicit containment.
- Shared skills can overwrite/delete local assets; no verified external-owner provenance boundary.
- Optional validators use motivating evidence and text-only judging, not independent tool-grounded effectiveness checks.
- Catalog injection can duplicate native skill discovery and add conflicting instructions; source code asks the model to read at most one relevant skill.
- The broader evolution path adds a proxy, registry/storage, scheduling and judge/model costs; an agent engine introduces OpenClaw as a dependency.
- Star count is interest, not a security or efficacy signal. CI inspected is lint/format only, not a unit-test or behavioral-evaluation guarantee.

## Integration ideas

- Treat the collective system as a candidate proposer over copied skills, not the owner of canonical skill files.
- Keep trace capture local/minimized and separate from publication; distinguish explicit user corrections, repeated failures and successful workarounds before aggregating evidence.
- Route accepted candidates through existing source review/versioning, retaining candidate hashes and originating evidence.
- Evaluate changed skills on independent tasks with real tools; keep candidate generation and acceptance evidence disjoint.

## Alternatives / related repos

- [MetaClaw](aiming-lab--MetaClaw.md) — related proxy/experience-to-skills lineage, plus a separate model-training path; SkillClaw has a concrete Hermes adapter at this revision.
- [Curator Evolver](pingchesu--hermes-curator-evolver.md) — Hermes-native hooks, proposal evidence and hash/backup guarded application; narrower mutation and source-owner boundaries.
- [Hermes Self-Improvement](ryonakae--hermes-self-improvement.md) — evidence clustering, review roles and outcome accounting; preserve its own eval/recovery caveats.
- [Nous self-evolution](nousresearch--hermes-agent-self-evolution.md) — offline optimization research, not this collective distribution architecture.

## Operating boundary

Source-maintenance authority stays with the established owner; a candidate proposer or shared registry does not acquire it. No runtime adoption is inferred by this note.

## Review candidates

- **Rank 1 — isolated comparative trial.** Rationale: determine whether packaged evidence aggregation/evolution beats an existing manual or governed repair lane. Question: does a candidate improve independent tasks while reducing operator effort? Promotion condition: explicitly approved sandbox/provider/budget; one copied skill/workflow, sanitized generation evidence, fixed held-out tasks and baseline/incumbent/SkillClaw arms. Use a disposable HOME/container without host credential or canonical-source mounts; no shared uploads or live synchronization. Local sandbox storage may be enabled only if required by the selected offline path. Stop if candidate-only evolution requires intrusive live integration or exceeds the agreed cost.
- **Rank 2 — guarded publication adaptation.** Rationale: preserve candidates without appointing a second source owner. Question: can existing Git review and activation replace default direct publication/mirror pulls? Promotion condition: concrete value demonstrated by the trial, with exact owner/provenance checks and rollback proof.
- **Rank 3 — trace minimization.** Rationale: raw tool results may contain credentials/private work. Question: can minimal sanitized evidence preserve proposal quality? Promotion condition: useful candidate output without transmitting unnecessary session contents.

## Commitment disposition

Not promoted to an implementation issue or Project item. Ingestion is research/documentation only; the trial remains an unadopted candidate. Source provenance: [AMAP-ML/SkillClaw](https://github.com/AMAP-ML/SkillClaw/tree/3938f7537645c961d94498a0a79fc0a977019595).
