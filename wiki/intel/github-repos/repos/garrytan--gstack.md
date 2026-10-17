---
title: garrytan/gstack
type: repo-intel
aliases:
  - gstack
  - GitHub repo: garrytan/gstack
source: https://github.com/garrytan/gstack
category: agent-skills
topics: [github-repo, deep-analysis, agent-skills, browser-automation, claude-code, gbrain]
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-31
license: NOASSERTION
---

# garrytan/gstack

> Reference-stack fit as reviewed 2026-05-31; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `88/100`
- **Recommendation:** `distill-pattern` — do not adopt wholesale into Hermes-first reference stack, but mine it aggressively for skill packaging, host-portable generated docs, browser-daemon security, and multi-agent workflow UX.
- **Usage observed 2026-05-31:** `reference-only`.
- **Why:** gstack is one of the strongest public examples of a skill-first AI engineering harness: opinionated slash-command workflows, generated host-specific skill docs, a persistent browser daemon, and GBrain-aware context hooks. The downside is that it is Claude Code / Garry workflow centered and would duplicate Hermes-native skills if imported uncritically.

## Live repo metadata checked

- **Repo:** `garrytan/gstack`
- **Description:** "Use Garry Tan's exact Claude Code setup: 23 opinionated tools that serve as CEO, Designer, Eng Manager, Release Manager, Doc Engineer, and QA"
- **Primary language:** TypeScript
- **Stars / forks at review:** ~105,170 stars / ~15,680 forks
- **Default branch:** `main`
- **Recent pushed at:** 2026-05-31T16:43:45Z
- **Open issues sampled via `gh issue list`:** 224
- **License metadata:** `NOASSERTION` from GitHub API at review time; verify before copying code/text.
- **Local analyzed commit:** `3bef43b` — `v1.55.0.0 fix wave: gbrain data-loss guards + browser crash-loop + 6 more (#1808)`

## What it is

gstack is a Bun/TypeScript monorepo for distributing role/workflow skills across Claude Code and other agent hosts, plus a real browser automation daemon. The high-value shape is not just "23 prompts"; it is a full skill distribution system:

- source skill templates and generated `SKILL.md` files across host directories (the upstream Claude host directory, the upstream Hermes host directory, `.opencode`, `.cursor`, `.openclaw`, `.agents`, etc.)
- typed host config and generation pipeline (`hosts/*.ts`, `scripts/host-config.ts`, `scripts/gen-skill-docs.ts`)
- persistent Playwright/Chromium browse daemon with scoped token pairing and tunnel/local split
- setup/config scripts with privacy stop-gates for telemetry, artifacts sync, GBrain hooks, and plan-tune hooks
- eval/test scripts for prompt/skill routing and host behavior

## Evidence checked

- `README.md`, `CLAUDE.md`, `ARCHITECTURE.md`, `USING_GBRAIN_WITH_GSTACK.md`
- `package.json`, `setup`, `bin/gstack-config`
- `hosts/hermes.ts`, `scripts/host-config.ts`, `scripts/gen-skill-docs.ts`
- `browse/src/server.ts`, `browse/src/browser-manager.ts`, `browse/src/url-validation.ts`, `browse/src/file-permissions.ts`, `browse/src/commands.ts`
- `.github/workflows/evals.yml`
- `pair-agent/SKILL.md(.tmpl)`, `setup-gbrain/SKILL.md.tmpl`

## Validation run

Commands run in the temporary upstream clone:

- `bun install --frozen-lockfile && bun test` — passed
- `bun test browse/test/batch.test.ts` — passed
- `bun run gen:skill-docs --host hermes --dry-run` — exited 0, reported generated Hermes skill docs as fresh
- `git status --short` — clean in analyzed clone

## Architecture findings

### 1. Host-portable skill generation is the biggest reusable pattern

`host-config.ts` defines a strongly typed host abstraction with install paths, frontmatter transformations, content rewrites, runtime symlinks, metadata generation, and host-specific behavior. This is directly relevant to the reference stack's "shared skills across Hermes / Claude Code / Codex / OpenCode" idea.

Evidence:

- `scripts/host-config.ts:17-112` defines the `HostConfig` schema.
- `scripts/host-config.ts:120-190` validates names, paths, CLI commands, linking strategy, and cross-config uniqueness.
- `package.json` exposes `gen:skill-docs`, `gen:skill-docs:user`, `skill:check`, and eval scripts.

**Distill into SStack/Hermes:** create a canonical skill source + generated host adapters model, but keep locally owned behavior in `sstack-*` skills instead of editing upstream bundled skills directly.

### 2. Browser daemon is serious infrastructure, not a toy helper

`browse/src/server.ts` documents a persistent Chromium daemon, random local port, state/log files under `.gstack`, auth token boundary, and idle shutdown. It has explicit dual-listener design for local vs tunnel traffic.

Evidence:

- `browse/src/server.ts:1-14` describes daemon architecture, state file, logs, random port, idle timeout.
- `browse/src/server.ts:121-141` validates injected auth tokens and falls back to random UUID if misconfigured.
- `browse/src/server.ts:156-163` states the dual-listener security property: local bootstrap endpoints are physically separated from ngrok/tunnel surface.
- `browse/src/server.ts:294-303` documents tunnel path allowlist and `/connect` as the only unauthenticated tunnel endpoint.
- `browse/src/server.ts:948-976` performs scoped-token scope/domain/rate checks before command dispatch.
- `browse/src/server.ts:1271-1288` wraps all command paths through the sanitizer choke point.

**Distill into Hermes:** use it as a benchmark for browser-tool hardening: scoped tokens, command classes, tunnel surface minimization, audit logs, and explicit local-vs-remote boundaries.

### 3. Security posture is above average, but still has sharp edges

Good signs:

- metadata endpoint and dangerous URL defenses exist in `browse/src/url-validation.ts:1-19`, with DNS rebinding checks for A/AAAA records at `url-validation.ts:76-109`.
- file permissions are owner-only on POSIX and use Windows `icacls` best-effort hardening (`file-permissions.ts:1-37`, `67-82`, `97-112`).
- tunnel route allowlisting and scoped tokens are first-class.
- default config is privacy-conservative: telemetry off, auto-upgrade false, artifacts sync off, plan-tune hooks prompt (`bin/gstack-config:33-86`, `105-123`).

Risks / caveats:

- `url-validation.ts:106-108` fails open on unexpected DNS errors. Reasonable for usability, but not ideal for high-risk shared/CI environments.
- `file-permissions.ts:26-35` explicitly admits permission hardening is best-effort; failures do not stop execution.
- `pair-agent/SKILL.md(.tmpl)` grants read+write by default and admin on request; admin includes JS execution, cookie access, and storage access (`pair-agent/SKILL.md.tmpl:8`, `142`, `210-213`). This must stay explicit-consent only.
- Browser state persists cookies/localStorage/tabs; useful, but sensitive (`browse/SKILL.md.tmpl:28`, `188`, `219`).

### 4. GBrain integration is adapter/glue, not a replacement for the reference stack's GBrain layer

gstack has meaningful GBrain awareness: setup, sync, context-load messaging, endpoint hashes, trust policy, salience allowlists, artifact sync modes. But it is wrapped around the external `gbrain` CLI/MCP model, not a better canonical brain than the reference stack's Hermes + GBrain + second-brain stack.

Evidence:

- `bin/gstack-config:121-137` has artifact sync and brain trust/salience defaults.
- generated skill docs include GBrain availability hints and `/sync-gbrain` context loading.
- `setup-gbrain` docs discuss engine selection, token storage trade-offs, and setup modes.

**Verdict:** learn from its privacy stop-gates and per-worktree source pinning; do not make gstack's artifact sync another canonical memory path.

## Maintainability findings

Strengths:

- Big test surface and eval scripts in `package.json`.
- Generated docs dry-run works for Hermes target.
- The code comments are unusually rich and often explain threat model / invariants, not just mechanics.
- Host config centralizes what would otherwise become scattered install logic.

Weaknesses:

- Repo is huge for its conceptual scope: local line count sample found ~1,413 relevant text/code files and ~908k lines including generated skills/docs/templates. That means review burden is high.
- Generated skill files create duplication; source-of-truth discipline matters.
- `browse/src/server.ts` is large (~3,137 lines) and mixes auth, tunnel routing, server lifecycle, command dispatch, SSE/PTTY/session details, and shutdown behavior. It has good comments, but it is a complexity hotspot.
- Fast churn + huge popularity means upstream stability risk is nontrivial; avoid vendoring without pinning.

## Scorecard

| Dimension | Score | Notes |
|---|---:|---|
| Hermes reference-stack fit | 90 | Very relevant to shared skills, browser automation, GBrain-aware workflows, and agent harness design. |
| Direct adoption fit | 55 | Too Claude/Garry-specific; would duplicate Hermes/SStack skills. |
| Pattern value | 95 | Host-portable skills + browser security + privacy gates are excellent references. |
| Security posture | 82 | Strong design, but browser/cookie/admin/tunnel surfaces remain inherently sensitive. |
| Maintainability | 78 | Good tests/comments; large generated surface and large server file raise burden. |
| Reuse leverage | 92 | High if distilled into SStack/Hermes; mediocre if installed wholesale. |

## Reference-stack recommendation

Default move: **distill, do not install as a new daily runtime.**

Best extractions:

1. **Shared-skill build system pattern** — canonical skill sources + host adapters + generated target skill docs.
2. **Browser daemon hardening checklist** — local/tunnel split, scoped tokens, command classes, route allowlist, audit logs, token sanitization, state permission checks.
3. **Privacy stop-gates** — telemetry off, artifact sync off until explicit prompt, plan hooks prompt by default.
4. **Role/workflow skill UX** — review/ship/QA/security flows as reusable patterns, not literal prompts.
5. **GBrain integration boundaries** — per-worktree pinning and trust policy, while keeping the reference stack's second-brain as canonical.

## Review candidates and context

- Add a SStack design note for **cross-harness shared skills** using gstack's `HostConfig` model as the comparison baseline.
- Compare gstack browse daemon with Hermes browser tools / Playwright MCP before adopting any browser control changes.
- If copying text/code from gstack, verify license status first; GitHub API returned `NOASSERTION` at review time.
- Consider a small sandbox: generate Hermes docs from one locally owned source skill into Claude/Codex/Hermes targets, then diff ergonomics against current manual skill maintenance.
