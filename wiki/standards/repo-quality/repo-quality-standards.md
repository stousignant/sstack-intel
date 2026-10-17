---
title: Repo Quality Standards
type: standard
status: active
created: 2026-06-19
updated: 2026-10-13
tags: [software-development, repo-quality, repo-readiness, ci, pre-commit, testing, standards]
sources:
  - https://pre-commit.com/
  - https://git-scm.com/docs/gitignore
  - https://docs.github.com/en/actions
  - https://docs.github.com/en/actions/security-for-github-actions/security-guides/security-hardening-for-github-actions
  - https://docs.github.com/en/code-security/getting-started/github-security-features
  - https://docs.github.com/en/code-security/getting-started/dependabot-quickstart-guide
  - https://docs.github.com/en/code-security/dependabot/working-with-dependabot/dependabot-options-reference
  - https://docs.github.com/en/code-security/secret-scanning/introduction/about-secret-scanning
  - https://agents.md/
  - https://github.com/ossf/scorecard
  - https://www.bestpractices.dev/en
  - https://playwright.dev/docs/locators
  - https://playwright.dev/docs/actionability
  - https://testing-library.com/docs/queries/about/
  - https://docs.pytest.org/en/stable/how-to/tmp_path.html
---

# Repo Quality Standards

> Private-repo standard: make the repo understandable, safe to change, and easy for humans/agents to verify. Skip public/open-source ceremony unless the repo actually needs it.

This is the tech-agnostic source of truth for [repo readiness scorecards](index.md). These technical engineering standards target private repositories, not agent-operating policy or universal open-source requirements. Language-specific defaults live in the [Python](python-repo-quality-standards.md) and [TypeScript](typescript-repo-quality-standards.md) standards.

## Private repo readiness scorecard

Every active private repo is scored on five essentials:

| Essential | What good looks like |
|---|---|
| **Purpose** | README or equivalent says what the repo is for, what it is not for, and any safety boundaries. |
| **One validation command** | A documented command or short script proves a normal change is safe; code repos with tests also document a code coverage command. |
| **Declared setup** | Runtime and dependencies are declared in repo files, not tribal shell state. |
| **Basic automation** | CI or a local wrapper runs the important checks from a clean-ish checkout. |
| **Hygiene guardrails** | Secrets, logs, caches, local DBs, build outputs, generated binaries, and runtime state are ignored or controlled; pre-commit catches cheap mistakes when useful. |

Use ✅ present, ⚠️ partial, ❌ missing. Score one point per present essential:

- **0–1/5:** not agent-ready; basic orientation/validation missing.
- **2–3/5:** partial; useful work is possible, but changes are higher-friction or riskier than necessary.
- **4/5:** good enough; one focused guardrail would make it solid.
- **5/5:** solid; avoid polishing unless a concrete repo risk demands it.

No weighted scoring. No fake precision. Evidence beats vibes.

## Smallest next guardrail

After scoring, recommend only the smallest next guardrail that materially improves safety to change. Good first moves are boring and reversible:

- clarify purpose/safety boundaries in the README;
- add or document one validation command, including a coverage command for code repos with tests;
- declare setup/dependencies in the repo;
- add a tiny CI workflow or local wrapper that runs the existing checks;
- fix `.gitignore`/secret/runtime artifact hygiene;
- add pre-commit only for cheap deterministic mistakes.

Do not turn repo quality into enterprise cosplay.

## Reference notes

Use these only to interpret the five essentials; they are not extra default requirements.

### Documentation

The first screen of docs should answer:

1. What is this repo for?
2. What is safe or unsafe to change?
3. How do I validate a change locally?
4. What does CI or local automation enforce?
5. Where does executable work live?

Keep executable work in the repository’s chosen issue/PR tracker; knowledge pages preserve durable engineering guidance and rationale, not parallel live task state.

### Commit boundary

Use pre-commit for fast deterministic checks: whitespace/EOF, YAML/TOML syntax, cheap lint/format checks, secret detection when relevant, and tiny project validators.

Do **not** put expensive integration tests, backtests, live-service calls, or broad network work in pre-commit. Those belong in CI, an explicit validation command, or a release gate.

When useful, place slower deterministic tests in an optional pre-push hook rather than on every commit. Declare the hook stage and document its installation; hook configuration alone does not install it. CI remains the shared backstop.

### CI boundary

Good CI proves that a clean clone can install from declared project metadata and run the repo's core checks. CI is a shared backstop, not a substitute for local validation.

### Test strategy

Prefer tests that protect behavior contracts: pure unit tests for parsing/aggregation/decision logic, fixture-driven tests for reports/CLI output, a few smoke tests, and characterization tests before major refactors. Keep external calls out of normal unit tests.

Keep each test layer accountable for a distinct contract instead of repeating the same assertion everywhere:

- unit tests cover deterministic domain behavior and important edge cases without requiring Docker, a running server, or live network services;
- integration tests cover boundaries between components, storage, subprocesses, or APIs;
- filesystem/configuration tooling uses isolated temporary roots and fixture state for install, migration, worker-state, and cleanup tests rather than touching the developer’s real home, credentials, or runtime;
- end-to-end tests cover a small number of critical user journeys rather than re-testing every branch already protected below;
- fake or mock external-I/O boundaries when isolation is useful, but do not mock the domain behavior the test is supposed to prove;
- browser tests prefer user-facing locators such as role, label, and visible text over DOM structure, CSS position, or `nth()` selectors;
- wait for observable state with framework auto-waiting or retrying assertions instead of fixed sleeps.

A test should have one clear reason to fail, but may use multiple assertions to prove that one behavior. Cover the normal path and meaningful failure states; do not multiply tests merely to satisfy a coverage number.

For code repos with tests, document a code coverage command as part of the baseline validation surface. Coverage is a diagnostic, not the score: avoid failing readiness solely because total coverage is below a magic number. Use 80%+ only as an aspirational target for mature application/library code; prioritize critical paths, bug regressions, and agent-facing seams.

### Agent-friendly defaults

Agent-touched repos benefit from explicit issue boundaries, small PRs with validation evidence, clear generated-artifact policy, deterministic scripts over prompt memory, and forward-only fixes after pushed commits.

### Agent handoff contract

For repos that humans expect coding agents to change, add a short root `AGENTS.md` or equivalent. It should be operational, not a second README:

- setup and dependency command;
- exact validation command;
- repo map for source, tests, docs, scripts, generated files, and runtime state;
- safe/unsafe commands and secret rules;
- repo-specific conventions agents should not rediscover;
- boundaries such as generated files, live-service calls, or data that must not be touched.

Keep this concise. A useful `AGENTS.md` reduces agent drift; a long stale wiki page creates another thing agents must distrust.

### Supply-chain and secret-safety guardrails

Private repos with real dependencies should have a minimal supply-chain and secret-safety baseline:

- clean installs use declared dependency metadata and lockfiles when the ecosystem supports them;
- CI permissions are least-privilege by default, especially for GitHub Actions;
- dependency update automation exists but is grouped/low-noise enough that humans actually review it;
- vulnerability or dependency-audit checks exist in CI, scheduled automation, or an explicit maintenance command;
- secret scanning or cheap secret-detection hooks cover repos that touch credentials, API keys, local `.env` files, or generated logs.

This is not a mandate for SBOMs, signing, provenance, or heavyweight compliance. Add those only when the repo's risk profile justifies them.

## Add only when useful

- **Dependency alerts/freshness** when the repo has real dependencies.
- **Branch protection/required checks** when more than one agent/person can push or the repo is high-risk.
- **`AGENTS.md` / `MISSION.md`** when agents need operating boundaries; prefer `AGENTS.md` for repo navigation and validation, `MISSION.md` for recurring autonomous loop contracts.
- **A tiny architecture note** when the repo is hard to understand from filenames alone.

## Usually skip for private repos

Do not add these by default:

- public contribution docs;
- badges/status theater;
- docs sites;
- SBOM/signing/provenance;
- heavyweight e2e suites;
- containers/devcontainers/Nix;
- strict open-source governance checklists;
- external quality platforms such as SonarQube, Codacy, or Code Climate.

External scorecards and quality platforms can inform judgment, but they are not the private-repo baseline.

## Stack-specific standards

- [Python Repo Quality Standards](python-repo-quality-standards.md)
- [TypeScript Repo Quality Standards](typescript-repo-quality-standards.md)
