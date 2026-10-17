---
title: Python Repo Quality Standards
type: standard
status: active
created: 2026-06-19
updated: 2026-10-13
tags: [python, repo-quality, repo-readiness, ruff, uv, pytest, ci, pre-commit, standards]
sources:
  - https://docs.astral.sh/ruff/
  - https://docs.astral.sh/ruff/configuration/
  - https://docs.astral.sh/uv/guides/projects/
  - https://docs.astral.sh/uv/concepts/projects/dependencies/
  - https://docs.astral.sh/uv/guides/integration/github/
  - https://docs.pytest.org/en/stable/
  - https://docs.pytest.org/en/stable/explanation/goodpractices.html
  - https://pre-commit.com/
  - https://docs.github.com/en/actions/tutorials/build-and-test-code/python
  - https://packaging.python.org/en/latest/guides/writing-pyproject-toml/
  - https://typing.python.org/en/latest/guides/modernizing.html
  - https://typing.python.org/en/latest/guides/libraries.html
  - https://microsoft.github.io/pyright/#/getting-started
  - https://mypy.readthedocs.io/en/stable/existing_code.html
  - https://docs.pydantic.dev/latest/concepts/models/
  - https://github.com/pypa/pip-audit
  - https://coverage.readthedocs.io/en/latest/subprocess.html
---

# Python Repo Quality Standards

> Private Python default: `pyproject.toml`, Ruff, one real test/validation command, and `uv` for new repositories following this reference profile unless an existing repo has a good reason not to move yet.

This extends [Repo Quality Standards](repo-quality-standards.md). It does not replace the five tech-agnostic essentials; it says what those essentials usually mean for Python.

## Python essentials

Every active private Python repo should have:

| Essential | Python default |
|---|---|
| **Declared setup** | `pyproject.toml` or a deliberate equivalent for Python version, project metadata, dependencies, and tool config. |
| **Ruff** | `ruff check .` and `ruff format --check .`, or documented scoped equivalents. |
| **One real test/validation command** | `pytest`, `unittest`, or a repo script that checks important behavior. |
| **Coverage command** | A documented `coverage`, `pytest --cov`, or equivalent command reports line/branch coverage for the repo's normal test suite. |
| **Declared dependency path** | `uv.lock`, `pyproject.toml`, requirements files, or equivalent. |
| **CI/local-wrapper parity** | The same checks work for agents without hidden local state. |

## Preferred new-repo commands

For new Python repositories following this reference profile, prefer:

```bash
uv sync
uv run ruff check .
uv run ruff format --check .
uv run pytest
uv run pytest --cov=<package-or-scripts> --cov-report=term-missing
```

For older/simple repos that do not yet have `pyproject.toml` or `uv`, do not block all work on migration. Add the readiness issue or smallest guardrail first, then migrate deliberately.

## Application and library dependency rule

Separate the reproducible development environment from the published dependency contract:

- applications and deployed services should commit a lockfile and use locked/frozen installs in CI and deployment;
- reusable libraries may also commit a lockfile so contributors and CI share a reproducible development/test environment;
- a published library's `project.dependencies` and optional dependencies remain the downstream contract, so use the narrowest compatible ranges justified by actual support rather than exporting the development lock as exact transitive requirements;
- exact pins in published library metadata require a concrete compatibility reason because they unnecessarily constrain downstream resolution.

In short: a library lockfile can reproduce *this repository's* checks, but it does not replace honest version constraints for consumers.

## Ruff adoption rule

Ruff is the default first Python quality tool because it is fast and covers lint plus formatting.

For existing repos, introduce it in this order:

1. Add check-only config.
2. Fix obvious lint issues.
3. Run a standalone mechanical format sweep.
4. Wire Ruff into pre-commit/CI after the commands are stable.

Never mix a formatter sweep with semantic refactors.

## Test runner rule

Use the repo's current test runner until a migration is explicitly chosen. Keeping `unittest` is fine when it is explicit and effective:

```bash
python3 -m unittest discover -s tests
```

Add pytest only when it buys something concrete: fixtures, parametrization, clearer failure output, or plugin support.

Good Python tests focus on pure functions, data transformations, report/CLI fixtures, subprocess boundaries, and safety regressions. Keep network/backtest/live-service work out of normal unit tests. Add a coverage command once tests exist; do not make an arbitrary 80% threshold the first gate for prototypes or script-heavy repos.

When tests launch Python CLIs or workers, configure and verify coverage in child processes; measuring the parent alone does not cover them. Use the installed Coverage.py version’s supported subprocess mechanism (such as `patch = ["subprocess"]`), collect parallel data and combine it before reporting where required, and verify that a representative child-only code path appears in the report. Keep source scope limited to maintained code.

## Type rule

Types are most valuable at module boundaries and refactor seams: parsed records, report rows, status/checker return objects, subprocess/API boundaries, and data passed across modules.

Do not make `mypy --strict` the first move on a messy repo. Start with typed seams and local clarity, then add a checker when the project is ready.

For agent-facing Python tooling, prioritize **typed and runtime-validated boundaries** over whole-repo type perfection:

- config and environment loading;
- CLI inputs/outputs, especially `--json` results agents parse;
- tool-call payloads and persisted records;
- LLM structured outputs and prompt/response contracts;
- subprocess/API return objects and report rows.

Use `pyright` or `mypy` as the static gate when useful, and use Pydantic or a deliberate equivalent for runtime validation where external systems, agents, or LLMs can send malformed data. Add small contract tests with representative payloads before tightening strictness.

## Python supply-chain rule

For Python repos with real dependencies, extend the tech-agnostic supply-chain baseline with Python-specific checks:

- install from locked metadata in CI when available, e.g. `uv sync --locked`;
- run `pip-audit` or an equivalent vulnerability check in CI, scheduled maintenance, or an explicit validation/maintenance command;
- configure dependency updates for Python packages and GitHub Actions, grouped to avoid alert fatigue;
- keep local secret files, generated logs, caches, notebooks, and runtime DB/state out of git.

Do not make vulnerability scanning part of the fastest local edit loop if it is slow or network-dependent. It can live in CI or maintenance automation while the core validation command stays cheap and deterministic.

## pre-commit / CI rule

Use pre-commit only for cheap deterministic checks: Ruff, whitespace/EOF, YAML/TOML syntax, large-file checks, and maybe secret detection when the repo plausibly touches credentials.

A basic Python CI should install from declared project metadata and run the same Ruff/test commands agents are expected to run locally. Check current upstream docs before writing exact workflow YAML.

## Mature validation target

For Python automation repositories adopting this profile, the target is Ruff + pytest + a documented coverage command + a single documented validation wrapper, with flat-repo packaging protection such as `py-modules = []` when editable install metadata is added. Preserve the existing-runner exception above until a migration is explicitly chosen.

For agent-heavy Python repos, the preferred mature-but-light gate is Ruff check, Ruff format-check, boundary type checking, focused tests, and a separate or CI-side dependency audit.

## Related

- [Repo Quality Standards](repo-quality-standards.md)
