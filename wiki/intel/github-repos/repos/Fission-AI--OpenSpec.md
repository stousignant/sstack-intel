---
title: Fission-AI/OpenSpec
type: repo-intel
aliases:
  - OpenSpec
  - GitHub repo: Fission-AI/OpenSpec
source: https://github.com/Fission-AI/OpenSpec
category: spec-driven-development
topics: [github-repo, repo-intelligence, spec-driven-development, brownfield, ai-coding, workflow]
status: deep-analyzed
usefulness_score: 84
recommendation: watch
usage: not-used
score_confidence: high
last_reviewed: 2026-09-05
license: MIT
---

# Fission-AI/OpenSpec

> Reference-stack evaluation as reviewed 2026-09-05. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — strongest formal-framework challenger for specification-heavy brownfield work, especially when change-delta specifications address repeated behavioral-specification drift.
- **Recommendation:** `watch`; pilot only when a real repository repeatedly suffers from behavioral-specification drift.
- **Usage observed 2026-09-05:** `not-used`.
- **Review candidate:** keep executable work and implementation ownership fixed; compare OpenSpec's living delta specs against the SStack/Matt snapshot-spec plus ADR/domain-doc promotion model only when the living-spec trigger appears.

## Verdict

OpenSpec is a stronger formal framework than Spec Kit for this assessment's brownfield workflow: it uses a lighter default lifecycle, validates artifacts, supports project-local Hermes skills, and archives change deltas into current behavioral specifications. Its archive model is also an adoption cost: `openspec/specs/` would become another canonical truth surface beside project docs, ADRs, tests, SStack, and GitHub Issues. Adopt it only if it resolves a demonstrated specification-drift problem.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-09-05: 67,392 stars, 4,637 forks, MIT, active, latest release `v1.12.0` published 2026-09-03.
- Official README, overview, workflows, customization, and existing-project guides on current `main`.
- CLI smoke using `npx --yes @fission-ai/openspec@1.12.0` in a disposable repository.
- Hermes initialization produced six project-local skills plus `openspec/config.yaml` and the change/spec directories: 9 files, 70,095 bytes.
- The CLI exposes validation, status, instructions, archive, schema, store, context, and workset surfaces. Custom schemas are currently marked experimental.

## Useful mechanisms

- Brownfield-first `ADDED` / `MODIFIED` / `REMOVED` delta specifications.
- Default `explore → propose → apply → sync → archive` lifecycle.
- Project-local artifact rules and operation guidance.
- Custom artifact dependency graphs and templates.
- Deterministic schema and artifact validation.
- Archive operation that merges accepted behavior into current specs.

## Risks / caveats

- Living specifications can duplicate project documentation, ADRs, tests, and GitHub issue context.
- `tasks.md` competes with GitHub Issues as executable task truth.
- `apply` can compete with the existing implementation/proof owner.
- Hermes requires adding each project's Hermes skill directory to `skills.external_dirs`.
- Anonymous usage telemetry is enabled by default; `OPENSPEC_TELEMETRY=0` or configuration disables it.
- Custom schemas are experimental and fast upstream release velocity increases local-overlay maintenance cost.

## Integration boundary

If adopted, OpenSpec would own only behavioral change specifications and archive semantics. GitHub would remain executable work truth; the established coding lane would retain implementation and proof ownership; SStack would retain cross-harness policy.

## Alternatives

- [mattpocock/skills](mattpocock--skills.md) — preferred pattern source for a lean SStack-native planning bridge.
- [github/spec-kit](github--spec-kit.md) — stronger formal artifact chain, but a poorer fit for the brownfield/runtime constraints described here.
