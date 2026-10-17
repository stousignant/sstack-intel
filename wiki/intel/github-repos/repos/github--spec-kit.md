---
title: github/spec-kit
type: repo-intel
aliases:
  - spec-kit
  - Spec Kit
  - GitHub repo: github/spec-kit
source: https://github.com/github/spec-kit
category: spec-driven-development
topics: [github-repo, repo-intelligence, spec-driven-development, prd, ai-coding, workflow]
status: deep-analyzed
usefulness_score: 86
recommendation: watch
usage: not-used
score_confidence: high
last_reviewed: 2026-09-05
license: MIT
---

# github/spec-kit

> Reference-stack fit as reviewed 2026-09-05; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `86/100` — excellent formal SDD pipeline and pattern source, but a poorer fit than a small planning bridge for workflows that already have GitHub task state and an established delivery owner.
- **Recommendation:** `watch`; distill requirements-checklist, cross-artifact analysis, and traceability methods rather than adopting the runtime globally.
- **Usage observed 2026-09-05:** `not-used`.
- **Review candidate:** reconsider only for a substantial greenfield, multi-contributor product that earns a uniform constitution/spec/plan/task chain.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 24/25 | Maps directly to Hermes plans, Codex/Claude coding workflows, and PAI/second-brain spec-first habits. |
| Leverage | 24/25 | Could reduce vague coding prompts and force predictable artifacts before implementation. |
| Reuse readiness | 19/20 | `uv tool install`, packaged CLI, docs, command templates, tests, security policy, GitHub backing. |
| Maturity/trust | 14/15 | MIT, huge adoption, active, official GitHub repo; still young/hype-heavy enough to sandbox first. |
| Differentiation | 11/15 | Strong executable-spec workflow; overlaps existing Hermes planning/TDD skills but packages it well. |

## Verdict

Spec Kit remains one of the strongest formal artifact pipelines, but it is not a default replacement for an established planning/delivery boundary. Its growing constitution/spec/plan/tasks/implement/converge/workflow surface overlaps SStack policy, GitHub task state, coding-lane execution, and Hermes orchestration. The preferred reference-stack direction is a small Matt-style planning bridge, GitHub work truth, and an established delivery owner.

### 2026-09-05 refresh

- Current metadata: 133,616 stars, 12,026 forks, MIT, latest release `v1.0.4` published 2026-09-02.
- A disposable Hermes initialization created 20 project files (99,200 bytes) and installed ten `speckit-*` skills globally under the per-user Hermes skills directory; the smoke artifacts were removed afterward.
- The official Hermes integration deliberately uses the global skill directory, conflicting with SStack's project/profile isolation and projection ownership.
- `taskstoissues` requires GitHub MCP tools rather than a deterministic GitHub CLI workflow, so an adapter would still be required.
- Spec Kit's resumable workflows, branching, gates, loops, and fan-out/fan-in now overlap Archon's workflow-state layer rather than remaining only a spec generator.
- Retain as a pattern source for `clarify`, requirements checklists, `analyze`, and artifact traceability. Do not make a Spec Kit overlay the default path without a new decision.

## Workload fit

- This assessment favors reuse over custom builds and values stronger specification, test, and evaluation discipline; Spec Kit packages those practices.
- Hermes/Codex coding work could benefit from a standard pre-implementation artifact contract.
- PAI/Hermes onboarding could adapt the “constitution → spec → plan → tasks” chain for higher-stakes agent work.

## What it is

Spec Kit is GitHub's open-source toolkit for Spec-Driven Development. The README frames SDD as making specifications executable: product scenarios and predictable outcomes drive implementation instead of “vibe coding every piece from scratch.” The CLI is `specify`, backed by Python/Typer and command templates for agent slash commands.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 106,738 stars, 9,441 forks, MIT, Python primary language, pushed 2026-05-28.
- README: install via `uv tool install specify-cli --from git+https://github.com/github/spec-kit.git@vX.Y.Z`; workflow: init, constitution, specify, plan, tasks, implement.
- `pyproject.toml`: package `specify-cli`, Python >=3.11, Typer/Click/Rich/YAML/pathspec dependencies, bundled templates/workflows/extensions/presets, pytest config.
- `SECURITY.md`: coordinated disclosure through GitHub open-source security channel.
- `spec-driven.md`: source-of-truth inversion: specifications and implementation plans generate code.
- Command templates inspected: `specify.md`, `plan.md`, `tasks.md`, `implement.md`, including extension hook checks and handoff metadata.

## Strengths

- Concrete, repeatable artifact chain: constitution, spec, technical plan, tasks, implementation.
- Multi-agent integration rather than one IDE lock-in.
- Bundled templates/scripts make it operational and air-gappable.
- Extension hooks point to a useful local customization story.

## Risks / caveats

- Can become process theater if the spec artifacts are too verbose or not checked against tests/evals.
- Generated specs/plans should be reviewed, not blindly treated as truth.
- Existing Hermes skills already cover parts of this; adoption should unify, not duplicate, planning rituals.
- Huge star count means hype pressure; use a tiny pilot before changing default workflows.

## Integration ideas

- Run a tiny sandbox project and compare Spec Kit artifacts against Hermes `writing-plans`, `test-driven-development`, and `atomic-criteria-verification` outputs.
- Distill a Hermes-friendly “constitution/spec/plan/tasks/proof” contract for autonomous coding runs.
- Use extension hooks as inspiration for preflight gates in Hermes project workflows.

## Alternatives / related repos

- [eyaltoledano/claude-task-master](eyaltoledano--claude-task-master.md) — task/dependency execution layer from PRDs.
- [bmad-code-org/BMAD-METHOD](bmad-code-org--BMAD-METHOD.md) — heavier agile/agent methodology.
- [openai/symphony](openai--symphony.md) — proof-of-work bundle reference.
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — active runtime where any adopted pattern should land.

## Review candidates and context

- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
