---
title: gsd-build/get-shit-done
type: repo-intel
source: https://github.com/gsd-build/get-shit-done
category: agent-workflow-framework
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-05-30
license: MIT
---

# gsd-build/get-shit-done

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `78/100` — The starred repo is now an archived redirect; the active successor is `open-gsd/gsd-core`. Keep as a pattern source for context-rot handling, discuss/plan/execute/verify phases, and security/test hygiene, but do not install the legacy package.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** No legacy install. Mine successor docs for context-rot/verify semantics if Hermes long-running coding tasks need sharper phase state.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20 | GSD’s phase/context-rot framing maps to Hermes coding workflows and session-handoff hygiene. |
| Leverage | 20 | Could improve long-running agent tasks by separating discuss/plan/execute/verify and preserving phase state. |
| Reuse readiness | 13 | Legacy repo redirected; successor package exists but is release-candidate and ownership transition adds caution. |
| Maturity/trust | 12 | MIT, active successor with security policy/tests; migration/continuity warning lowers confidence. |
| Differentiation | 13 | Strong context-rot and verification-agent vocabulary, but overlaps with Spec Kit/OpenSpec/BMad/Hermes skills. |

## Verdict

The starred repo is now an archived redirect; the active successor is `open-gsd/gsd-core`. Keep as a pattern source for context-rot handling, discuss/plan/execute/verify phases, and security/test hygiene, but do not install the legacy package.

## Reference-stack relevance

- This sits in the same lane as repository readiness, spec-first coding, execution-state visibility, and long-running agent task hygiene.
- The value is mostly **artifact contracts**: readiness reports, instruction files, evals, specs, decision records, phase state, and verification evidence.
- Default stance: sandbox/read-only first; do not add another global command framework unless it beats existing Hermes skills and Spec Kit on a tiny task.

## What it is

Legacy Claude Code/context-engineering workflow repo. README now says development moved to Open GSD / `open-gsd/gsd-core`, whose README describes a cross-runtime meta-prompting/spec-driven workflow for Claude Code, OpenCode, Gemini CLI, Kilo, Codex, Copilot, Cursor, Windsurf, and more.

## Evidence checked

- Legacy README is only a redirect: “GSD Has Moved” to `open-gsd/get-shit-done-redux`; GitHub resolves successor to `open-gsd/gsd-core`.
- Successor README says package names are `@opengsd/gsd-core` and `@opengsd/gsd-sdk`; it explicitly warns to migrate away from legacy packages.
- Successor root has `commands/`, `agents/`, `hooks/`, `docs/`, `tests/`, `SECURITY.md`, `AGENTS.md`, `.secretscanignore`, `.base64scanignore`.
- Package check: `@opengsd/gsd-core` 1.2.0-rc.1, MIT, bin `gsd-core`, modified 2026-05-30.
- Local evidence directory: temporary upstream inspection material.

## Strengths

- Names the real failure mode: context rot over multi-session AI work.
- Phase model includes discussion, planning, execution, verification, and repeat/ship; good for Hermes long-task handoffs.
- Successor has security/test hygiene signals worth mining.

## Risks / caveats

- Do not install legacy package; project moved/renamed with continuity warning.
- High ceremony and multi-agent command framework could duplicate Hermes skills/Kanban.
- Successor is RC; treat as moving target.

## Integration ideas

- Distill phase-state and verification-agent patterns into Hermes `session-handoff-progress`, Kanban, and coding workflows.
- Use successor docs as a reference only; if testing, sandbox `npx @opengsd/gsd-core@latest` in a disposable scratch directory after inspecting installer behavior.
- Compare against OpenSpec/Spec Kit before adopting any GSD commands.

## Alternatives / related repos

- [github/spec-kit](github--spec-kit.md)
- [bmad-code-org/BMAD-METHOD](bmad-code-org--BMAD-METHOD.md)
- [eyaltoledano/claude-task-master](eyaltoledano--claude-task-master.md)
- [AI Development Workflow Frameworks](../comparisons/ai-development-workflow-frameworks.md)

## Review candidates and context

- Source-local: No legacy install. Mine successor docs for context-rot/verify semantics if Hermes long-running coding tasks need sharper phase state.
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
