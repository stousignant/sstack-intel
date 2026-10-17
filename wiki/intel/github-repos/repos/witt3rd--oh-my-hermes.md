---
title: witt3rd/oh-my-hermes
type: repo-intel
aliases:
  - witt3rd oh-my-hermes
  - OMH
  - Oh My Hermes OMH
  - GitHub repo: witt3rd/oh-my-hermes
source: https://github.com/witt3rd/oh-my-hermes
category: hermes-extension
status: deep-analyzed
usefulness_score: 90
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-08
license: MIT
tags: [github-repo, hermes, skills, multi-agent, orchestration, plugin]
---

# witt3rd/oh-my-hermes

> Reference-stack evaluation as reviewed 2026-06-08; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `90/100` — the strongest third-party Hermes-native skill/plugin pack checked so far: multi-agent planning/execution skills, optional plugin hooks, state/evidence tools, tests, docs, and MIT license.
- **Recommendation:** `adopt-now` — sandbox/install selected skills first, especially `omh-ralplan`, `omh-ralph`, `omh-deep-research`, and the `omh_delegate` pattern; do not globally enable the plugin in the active profile until the current test failure and hook/tool behavior are reviewed.
- **Usage observed 2026-06-08:** `not-used`.
- **Review candidate:** Run a controlled sandbox against a copied repo or small fixture, then decide whether to port/adapt the best patterns into SStack or install via Hermes skill tap.

## Scorecard

| Factor | Points | Evidence |
|---|---:|---|
| Stack fit | 24/25 | Built natively for Hermes primitives: skills, `delegate_task`, plugin hooks, project-local `.omh/` state, evidence gathering, and role prompts. |
| Leverage | 24/25 | Directly addresses reliable multi-agent planning, requirements discovery, implementation, verification, and research workflows. |
| Reuse readiness | 17/20 | Clear install docs, MIT license, Python plugin with `pyyaml`, 10 skills, roles, tools, templates, and docs; one failing test prevents fully clean trust. |
| Maturity/trust | 12/15 | 61 stars / 9 forks, last push 2026-05-13, committed tests and docs; test suite is mostly healthy but currently fails one role-catalog assertion. |
| Differentiation | 13/15 | More Hermes-native and operationally serious than generic skillpacks: role-injection hooks, atomic state, evidence allowlists, hardened delegation, and circuit breakers. |
| **Total** | **90/100** | Sandbox immediately; likely pattern/adoption candidate. |

## Verdict

This is not the same shape as [Salomondiei08/oh-my-hermes](Salomondiei08--oh-my-hermes.md). Salomondiei08's repo is mainly a founder/app-builder packaging layer; witt3rd's OMH is a serious Hermes-native multi-agent orchestration toolkit. It merits a sandbox. The best assets are the RALPlan/Ralph workflow split, role-specific subagent discipline, project-local `.omh/` state convention, `omh_delegate` subagent-output persistence pattern, and `omh_gather_evidence` allowlisted verification tool. Direct installation into an active Hermes profile remains premature because plugin hooks alter subagent/system-prompt behavior and the test suite has one failing role-catalog regression; selected skills/patterns are suitable for a controlled test now.

## Reference-stack relevance

- It addresses a recurring reliability problem in multi-agent work: preserving progress through context limits, tool hiccups, and vague requirements.
- It is built for Hermes rather than Claude Code/OpenClaw, so the patterns can transfer cleanly into SStack and a Hermes cockpit.
- Its `.omh/` convention is a useful cousin to SStack/CCPM/GitHub Projects: project-local artifacts for specs, plans, state, evidence, breadcrumbs, and interrupted runs.
- The `omh_delegate` pattern directly mitigates a Hermes delegation hazard: parent only receives the subagent's final summary, so the subagent should persist the important artifact itself.
- The evidence tool's allowlist/timeout/truncation design is a concrete safety pattern for verification agents.

## Reuse / inspiration potential

- **Direct reuse:** Yes, but staged. Start with skills in a sandbox; treat the plugin as privileged code requiring review before active-profile enablement.
- **Pattern to borrow:** RALPlan consensus planning, Ralph verified execution, one-task-per-invocation persistence, role injection, subagent-persisted outputs, `.omh/` state schema, evidence allowlists, and 3-strike circuit breakers.
- **Stack area improved:** Hermes/SStack agentic coding workflows, verification discipline, multi-agent orchestration, project-local state, research synthesis.
- **Autonomy leverage:** Could reduce flaky long-running agent work by separating planner/architect/critic/executor/verifier roles and forcing evidence-backed completion.
- **Freedom leverage:** Better autonomous implementation loops can reduce supervision and strengthen self-improving agent infrastructure.

## What it is

`witt3rd/oh-my-hermes` is a Hermes-native multi-agent orchestration skillpack plus optional plugin. The standalone skills include deep research, consensus planning (`omh-ralplan`), requirements interviewing, verified execution (`omh-ralph`), task execution, backlog triage, and autopilot composition. The optional plugin adds role-injection hooks, state management, evidence gathering, and a hardened delegation helper.

## Evidence checked

- **GitHub metadata:** `witt3rd/oh-my-hermes`, created 2026-04-07, default branch `master`, 61 stars, 9 forks, not archived, not a fork, MIT license, last pushed 2026-05-13.
- **Local clone:** a disposable source checkout, HEAD `2636f58 2026-05-13T07:50:46-07:00 plugin.yaml: conform to Hermes plugin guide manifest schema (#18)`.
- **Repo shape:** 120 tracked files: docs, `.omh/` plans/research artifacts, `plugins/omh`, 10 skill directories, role prompts, templates, tests, `pyproject.toml`, and `uv.lock`.
- **Docs inspected:** `README.md`, `docs/concepts.md`, `docs/plugin.md`, `docs/omh-delegate.md`, `plugins/omh/config.yaml`, `plugins/omh/plugin.yaml`, `LICENSE`.
- **Code inspected:** `plugins/omh/tools/evidence_tool.py`, `plugins/omh/omh_state.py`.
- **Syntax check:** `python3 -m compileall -q plugins/omh` passed.
- **Test run:** `uv run pytest -q plugins/omh/tests` produced `200 passed, 1 failed` in 1.89s. The failure was `test_get_role_catalog_returns_all_roles`, where the role catalog now includes extra `triage-maintainer` and `triage-skeptic` roles not reflected in the test's expected set.

## Verified / plausible / source claims

- **Verified:** Skills are standalone Markdown skill directories under `plugins/omh/skills/`.
- **Verified:** The optional plugin declares tools `omh_state` and `omh_gather_evidence`, and hooks `pre_llm_call`, `on_session_end`, and `pre_tool_call` in `plugin.yaml`.
- **Verified:** `omh_gather_evidence` uses token-prefix allowlists, rejects shell metacharacters, runs with `shell=False`, bounds timeout to 300s, and truncates output.
- **Verified:** `omh_state` writes project-local `.omh/state` files atomically and seeds `.omh/README.md`/`.gitignore` without overwriting user edits.
- **Verified:** `omh_delegate` explicitly documents the Hermes `delegate_task` final-summary-only contract and uses a subagent-persisted-output pattern.
- **Plausible:** RALPlan/Ralph/autopilot should improve long-running planning/execution reliability, but this review did not run a full end-to-end workflow in a real project.
- **Source claim:** Skills can be installed with `hermes skills tap add witt3rd/oh-my-hermes` and `hermes skills install ...`; plugin install requires copying `plugins/omh/` to `~/.hermes/plugins/omh/` plus `pyyaml`.

## Strengths

- **Hermes-native, not just prompt cosplay:** It uses Hermes skills, delegate semantics, plugin hooks, tools, and project-local state instead of assuming Claude Code primitives.
- **Good role architecture:** Planner, architect, critic, executor, verifier, analyst, security reviewer, test engineer, code reviewer, debugger, and research roles are explicit and reusable.
- **State discipline:** `.omh/` keeps plans, specs, research artifacts, state, evidence, and breadcrumbs local to the project.
- **Verification discipline:** Ralph separates executor from verifier and uses build/test evidence, 3-strike circuit breakers, cancel signals, and final architect review.
- **Subagent-output hardening:** `omh_delegate` addresses the real failure mode where the parent loses useful subagent work because only final summaries cross the boundary.
- **Safety-aware evidence tool:** Allowlist prefixes, no shell, metacharacter rejection, cwd confinement, timeout caps, and truncation are the right default shape.
- **MIT license and docs/tests:** Much cleaner direct-reuse posture than many third-party skillpacks.

## Risks / caveats

- **Plugin hooks are privileged:** `pre_llm_call` and `pre_tool_call` can modify subagent prompt behavior; review before enabling globally.
- **One failing test:** The suite is mostly healthy, but the role catalog test is stale relative to triage roles. That is probably minor, but it proves the repo is not green at HEAD.
- **Possible overlap with SStack/CCPM:** Direct adoption may duplicate existing SStack skills, CCPM flow, GitHub Projects, and Hermes delegation habits unless bounded carefully.
- **Evidence allowlist still runs commands:** The design is sane, but enabling a tool that runs build/test commands expands the agent's operational surface.
- **No end-to-end dogfood in this review:** The full RALPlan → Ralph workflow was not exercised locally, only docs/code/tests were inspected.
- **Install docs assume skill tap support:** Confirm current Hermes `skills tap` behavior before relying on README install commands.

## Integration ideas

- Sandbox `omh-ralplan` on one small SStack/Hermes improvement idea and compare output quality against current planning skills.
- Sandbox `omh-ralph` on a low-risk copied repo task to test executor/verifier discipline and state artifacts.
- Port the `omh_delegate` subagent-persisted-output pattern into SStack's agentic coding workflow skill if it improves reliability.
- Use `omh_gather_evidence` as a model for future Hermes verification tools: allowlisted commands, no shell, bounded output, structured evidence.
- Consider `.omh/` as a project-local state/artifact convention for experimental multi-agent runs, but avoid making it another canonical task tracker unless it beats GitHub Projects or CCPM.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — runtime and substrate OMH targets.
- [Salomondiei08/oh-my-hermes](Salomondiei08--oh-my-hermes.md) — same repo name, different purpose: app-builder/CTO packaging, less mature as a Hermes-native orchestration substrate.
- [automazeio/ccpm](automazeio--ccpm.md) — stronger PRD→epic→GitHub issue workflow substrate; compare against OMH for planning/execution state.
- [openai/symphony](openai--symphony.md) — compact proof-of-work/run lifecycle spec that can inform OMH-style task contracts.
- [Yeachan-Heo/oh-my-claudecode](Yeachan-Heo--oh-my-claudecode.md) — stated inspiration, but Claude Code-oriented rather than Hermes-native.

## Review guidance

- Sandbox selected skills before active-profile install.
- Review/fix upstream stale role-catalog test before trusting the plugin as green.
- Distill `omh_delegate` and evidence-tool safety patterns into SStack/Hermes skills if the sandbox works.
