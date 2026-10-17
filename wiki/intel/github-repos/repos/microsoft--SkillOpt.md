---
title: microsoft/SkillOpt
type: repo-intel
aliases:
  - SkillOpt
  - SkillOpt-Sleep
  - "GitHub repo: microsoft/SkillOpt"
source: https://github.com/microsoft/SkillOpt
category: hermes-self-improvement
topics: [github-repo, self-improvement, skill-optimization, agent-skills, self-evolving-agents, evals, gbrain]
status: deep-analyzed
usefulness_score: 84
recommendation: defer
usage: sandboxed
score_confidence: medium
last_reviewed: 2026-09-11
license: MIT
---

# microsoft/SkillOpt

> Reference-stack fit as reviewed 2026-09-11; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `84/100` — promising fit for review-gated skill improvement; this is a relevance judgment, not demonstrated benefit on SStack skills.
- **Recommendation:** `defer` under the dated reference-stack assessment; observed integration effort did not establish enough value for adoption.
- **Usage observed 2026-09-11:** `sandboxed`. Disposable standalone Python/Codex engine trial; no candidate adopted.
- **Confidence:** `medium` — native execution is demonstrated; reliable skill-delivery and useful improvements still need verification.
- **Reconsideration gate:** explicit trial authorization, a proven supported integration and a small trustworthy benchmark. Manual evidence-driven skill maintenance is distinct from optimizer adoption.

## Dated bounded-attempt evidence

The final bounded attempt on 2026-09-11 fixed actual skill delivery and explicit confidence-enum alignment; four static tests passed and five real Sol target evaluations completed. The optimizer then failed before inference because our disposable isolation wrapper added `--ephemeral` when SkillOpt’s backend already supplied it. Two analyst requests each exhausted three CLI parse retries. No candidate was generated, and the fresh final test set was not run.

**Attribution:** this is a local integration failure, not evidence that Microsoft SkillOpt’s optimization method is ineffective or that upstream maturity caused the failure. The dated defer judgment concerns demonstrated value versus integration effort. Earlier exact-string grading also penalized semantically equivalent answers; those scores are not robust measures of skill quality.

The bounded review did not repair the wrapper again. The recorded stderr identifies the duplicate-argument error; the result does not authorize activating an optimizer service or changing live skills. The historical score below remains a relevance assessment, not an adoption recommendation.

## Scorecard

| Factor | Points | Rationale |
|---|---:|---|
| Stack fit | 23/25 | Directly targets reviewable skill artifacts and supports native Codex execution. |
| Leverage | 22/25 | Could turn documented failures into measured improvements; Sleep separately covers session-derived tasks. |
| Reuse readiness | 16/20 | Native subscription execution works; arbitrary workflows require documented custom benchmark adapters. |
| Maturity/trust | 13/15 | Microsoft-owned MIT project with a published release; newer backend work and Sleep preview still require version discipline. |
| Differentiation | 10/15 | Overlaps GBrain conceptually but removes its database and provider constraints for native Codex experiments. |
| **Total** | **84/100** | Experiment-worthy, not adoption proof. |

## Distinguish the implementations

**Microsoft/SkillOpt** is the standalone Python implementation of [the SkillOpt paper](https://arxiv.org/abs/2605.23904). **GBrain `skillopt`** is an independent TypeScript implementation inspired by that work, not a wrapper around the Python package. **GEPA** is a separate optimizer, not the underlying SkillOpt dependency.

The earlier recommendation to reject the Python package solely because GBrain contained related machinery is superseded. GBrain's tool registry, database locking, and provider limitations do not establish limitations of Microsoft's standalone product. Neither conceptual overlap nor installed code establishes operational usage or measured benefit.

## Supported workflows

- **Research engine:** fixed benchmark → scored rollouts → bounded skill edits → validation gate → `best_skill.md`. Custom tasks use `SplitDataLoader`, a rollout/scorer, `EnvAdapter`, and configuration. See the [first experiment](https://github.com/microsoft/SkillOpt/blob/79124b37e9a6371e13b753f8bcd7adb1e493ade1/docs/guide/first-experiment.md) and [custom benchmark guide](https://github.com/microsoft/SkillOpt/blob/79124b37e9a6371e13b753f8bcd7adb1e493ade1/docs/guide/new-benchmark.md).
- **SkillOpt-Sleep, preview:** harvest local sessions → review derived tasks → replay → propose → explicitly adopt. This companion implementation is distinct from the research engine. See [Sleep documentation](https://github.com/microsoft/SkillOpt/blob/79124b37e9a6371e13b753f8bcd7adb1e493ade1/docs/sleep/README.md).
- **Version boundary:** published release `0.2.0` exists, but newer Codex support/fixes were inspected on `main`. Experiments pin immutable commit `79124b37e9a6371e13b753f8bcd7adb1e493ade1`, not a floating branch.
- **Harness boundary:** Codex execution is not Hermes execution. There is no shipped Hermes backend in the inspected source; final Hermes adoption requires independent evaluation through Hermes.

## Local experimental evidence

The 2026-09-10 experiment used the pinned standalone source, a disposable venv, public frozen repository evidence, a sanitized skill derivative, and exact `gpt-5.6-sol` through authenticated Codex CLI. The native smoke returned `SKILLOPT-NATIVE-SMOKE-OK`. No paid API route or model fallback was used.

A minimal custom benchmark exercised the engine's candidate generation and rejection gate. Filesystem tool execution encountered `bwrap: loopback: Failed RTM_NEWADDR: Operation not permitted`. A second run embedded repository evidence and prohibited tools rather than disabling the sandbox.

**Verification caveat:** that fallback wrote candidate instructions to a skill file but did not explicitly include the skill body in its actual prompt. Since tools were prohibited, candidate loading is not established. Its reported equal scores must not be interpreted as evidence that optimization was ineffective. The constructed `conversation.json` is an adapter record, not proof of what Codex received. Candidate-delivery verification is required before efficacy conclusions.

A corrected diagnostic pair explicitly embedded each complete sanitized skill in the actual Codex prompt; parent verification confirmed both skill bodies and the recorded input hashes. Both outputs returned `reference-only` and the requested entry-point facts. The scorer reported hard `0`, soft `11/12` for each because `confidence` was `verified`, not `high|medium|low`. **That failure is a benchmark-contract defect, not demonstrated agent failure:** the prompt never specified those confidence enums, while the supplied skill instructed `verified|plausible|unknown`. Do not use the hard-zero score to judge capability. The corrected pair reused an already inspected item, so it is diagnostic rather than a fresh untouched test. It did not rerun optimization with corrected instruction delivery.

This was a tiny Codex reasoning/output-contract smoke on a short rewritten public derivative, not an optimization of the full SStack skill, its references, or Hermes tool behavior. No candidate was adopted. The canonical skill remained unchanged. Before another optimization run, make the task contract and grader agree, verify baseline/candidate delivery, and reserve genuinely fresh final tasks. The corrected diagnostic records preserve the explicitly embedded prompts and input hashes.

Dated experiment evidence comprised a report, raw run logs, adapter source, candidate diff and dependency pins. The execution findings and scoring qualifications are preserved above; temporary artifacts are not canonical operating state.

## Historical evidence

The August 30 review recorded a successful disposable `pip install skillopt`, Sleep CLI help, and a local read-only harvesting smoke producing three tasks from five sessions without provider calls. It also recorded Microsoft ownership, MIT licensing, release `v0.2.0`, and upstream benchmark claims. Those claims were not independently reproduced. Historical GBrain integration findings establish provenance, not that an optimization service was active or successful.

## Safety and evaluation boundaries

- Keep canonical skills, production GBrain state, private repositories, and final test data outside optimizer reach. Stage candidates for review; never auto-adopt.
- Confirm actual target inputs and skill hashes. Writing a skill file or reconstructing a transcript does not prove the model consumed it.
- Reserve final test tasks outside iterative optimization gates; reruns after inspecting failures are diagnostic, not fresh untouched tests.
- Public embedded-evidence tests assess reasoning/output contracts only. They do not prove tool use, retrieval, filesystem safety, or real repo ingestion.
- Sleep harvesting is local, but real replay/mining sends transcript-derived excerpts to the selected provider. Review/redact task files and authorize the provider/data boundary first. A real-backend `dry-run` can still make inference calls.
- Do not run unattended Sleep scheduling or its WebUI as part of this bounded experiment.

## Related sources and work

- [Hermes Self-Evolution](nousresearch--hermes-agent-self-evolution.md) — runtime-native alternative; requires shipped fixes, target-size support, and real artifact/evaluation evidence before any adoption claim.
- [Anthropic skill creator](anthropics--skills-skill-creator.md) — authoring rather than optimization.
- Session-evidence harvesting and optimizer execution are separate scopes; this native optimizer smoke does not prove a complete harvest/replay workflow.
