# Repo Quality Standards

Technical engineering standards for making repositories understandable, safe to change, and easy for humans and coding agents to verify.

This collection is the canonical input for repo-readiness audits. It covers tooling, configuration, tests, packaging and CI—not agent-operating doctrine. The baseline targets private repositories; publication adds separate disclosure and open-source requirements.

- [Repo Quality Standards](repo-quality-standards.md) — tech-agnostic private-repo readiness scorecard.
- [Python Repo Quality Standards](python-repo-quality-standards.md) — Python-specific extension covering `pyproject.toml`, Ruff, uv, tests, pre-commit, CI, and typing seams.
- [TypeScript Repo Quality Standards](typescript-repo-quality-standards.md) — TypeScript/JavaScript extension covering strict `tsconfig`, Bun, lint/format, the `validate` script, CI parity, and Vite specifics.

## Boundary

This folder is normative audit doctrine, not raw source material and not project-specific task state. Repo-specific exceptions belong in the repo's docs or project page; reusable lessons should be distilled back into the smallest applicable standard.
