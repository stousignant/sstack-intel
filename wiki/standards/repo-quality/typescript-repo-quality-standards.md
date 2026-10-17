---
title: TypeScript Repo Quality Standards
type: standard
status: active
created: 2026-09-03
updated: 2026-09-03
tags: [typescript, javascript, repo-quality, repo-readiness, bun, vite, vitest, ci, standards]
sources:
  - https://www.typescriptlang.org/tsconfig/
  - https://bun.sh/docs
  - https://bun.sh/docs/test
  - https://vitest.dev/guide/
  - https://vite.dev/guide/
  - https://typescript-eslint.io/
  - https://biomejs.dev/
  - https://docs.github.com/en/actions/tutorials/build-and-test-code/nodejs
---

# TypeScript Repo Quality Standards

> Private TypeScript default: `package.json` with a single `validate` script, strict `tsconfig`, one real test command, and Bun for new repositories following this reference profile unless the repo has a reason not to move.

This extends [Repo Quality Standards](repo-quality-standards.md). It does not replace the five tech-agnostic essentials; it says what those essentials usually mean for TypeScript and JavaScript.

## TypeScript essentials

| Essential | TypeScript default |
|---|---|
| **Declared setup** | `package.json` plus a committed lockfile (`bun.lock`, `pnpm-lock.yaml`, `package-lock.json`, `yarn.lock`). Node or Bun version declared, not assumed. |
| **Strict typecheck** | `tsc --noEmit` passes with `strict: true`. A TypeScript repo that only builds is not typechecked. |
| **Lint/format** | Biome, or ESLint via `typescript-eslint` plus a formatter. One of them, configured, run in CI. |
| **One real test command** | `bun test`, `vitest run`, or the repo's runner. Capture file and test counts, not just "tests pass." |
| **Coverage command** | A documented `bun test --coverage` or `vitest run --coverage` reports coverage for the normal suite. |
| **One validation command** | A `validate` script that mirrors CI exactly: typecheck, lint, test, build. |
| **CI/local parity** | CI uses a clean frozen install and runs the same script names, with no hidden local state. |
| **Purpose** | README says what the package is for, what it is not for, and any safety boundaries. |
| **Hygiene guardrails** | `.gitignore` covers `node_modules/`, `dist/`, `coverage/`, logs, and `.env`; no generated bundles or lockfile-adjacent junk committed. |

## Preferred new-repo commands

Bun-first for new repositories following this reference profile:

```bash
bun install
bun run typecheck        # tsc --noEmit
bun run lint
bun test
bun test --coverage
bun run build
```

The single most valuable addition to a JS/TS repo is a `validate` script. Use `bun run test` rather than `bun test` so it delegates to whatever runner the repo declares:

```json
{ "scripts": { "validate": "tsc --noEmit && biome check . && bun run test && bun run build" } }
```

For existing npm/pnpm repos, do not block work on a Bun migration. Use `npm ci` / `pnpm install --frozen-lockfile` and the repo's existing script names, then migrate deliberately.

## Audit probes

Runtime-agnostic:

```bash
git status --short --branch
npm pkg get scripts    # reads package.json directly; works with any runner or no lockfile
gh run list --limit 5 --json status,conclusion,name,createdAt,headBranch,event,url,workflowName
```

Bun repos:

```bash
bun install --frozen-lockfile
bun run typecheck && bun run test && bun run build
bun audit
bun outdated
```

npm/pnpm repos:

```bash
npm ci                 # or: pnpm install --frozen-lockfile
npm run typecheck && npm test && npm run build
npm audit --audit-level=moderate
npm audit fix --dry-run
npm outdated --json || true
```

Do not mix the two. `npm audit` on a repo with only `bun.lock` fails with `ENOLOCK`, and `npm outdated` returns an empty object with no error, which is worse than failing loudly.

## Frontend and Vite specifics

For Vite/browser repos, apply the essentials above plus:

- Vite build warnings are usually not failures, but note them when they signal future bundle pressure.
- Verify deployment claims instead of trusting the README. If a repo advertises GitHub Pages, check it:

```bash
gh api repos/<owner>/<repo>/pages --jq '{status:.status, html_url:.html_url, source:.source, build_type:.build_type}'
curl -I -L --max-time 20 https://<owner>.github.io/<repo>/
```

A 404 while the README says "Play Now" means purpose and docs score present, but deployment truth is a high-leverage follow-up.

## Smallest next guardrail

For private JS/TS repos, the first move is usually one of:

1. Add one `validate` script that mirrors CI.
2. Turn on `strict` in `tsconfig` and fix the resulting errors, or record why not.
3. Refresh the lockfile after an audit fix, then rerun validation.
4. Correct stale deployment docs or enable the advertised workflow path.
5. Add pre-commit only once the validation path is stable.

Do not turn this into public OSS ceremony. Badges, docs sites, containers, provenance, and governance stay out unless the repo's real risk demands them. Public release additionally requires a separate disclosure, history, licensing and repository-surface review; this readiness standard is not publication clearance.
