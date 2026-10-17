---
title: microsoft/agentrc
type: repo-intel
source: https://github.com/microsoft/agentrc
category: agent-context-engineering
status: deep-analyzed
usefulness_score: 88
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# microsoft/agentrc

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `88/100` — Best immediate repo-readiness/context-engineering candidate: it measures AI-readiness, generates instruction/eval/dev-config artifacts, and evaluates drift. Sandbox on a copied repo before letting it PR or write canonical instructions.
- **Recommendation:** `adopt-now`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Run `npx github:microsoft/agentrc readiness --json` and `instructions --output AGENTS.md` in a copied repo; review diffs before canonical use.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23 | Directly maps to Hermes/GBrain repo hygiene, AGENTS/CLAUDE.md style project context, and eval-first coding workflows. |
| Leverage | 23 | Could turn manual repo onboarding into a measurable Measure → Generate → Maintain loop. |
| Reuse readiness | 17 | NPM/GitHub CLI path, VS Code extension, CI/batch modes; uses Copilot SDK and GitHub auth for some flows. |
| Maturity/trust | 13 | Microsoft-backed, active, MIT, tests/build scripts/security policy; explicitly experimental. |
| Differentiation | 12 | Stronger than generic templates because it claims repo-specific context plus eval/drift checks. |

## Verdict

Best immediate repo-readiness/context-engineering candidate: it measures AI-readiness, generates instruction/eval/dev-config artifacts, and evaluates drift. Sandbox on a copied repo before letting it PR or write canonical instructions.

## Workload fit

- This sits in the same lane as repository readiness, spec-first coding, execution-state visibility, and long-running agent task hygiene.
- The value is mostly **artifact contracts**: readiness reports, instruction files, evals, specs, decision records, phase state, and verification evidence.
- Default stance: sandbox/read-only first; do not add another global command framework unless it beats existing Hermes skills and Spec Kit on a tiny task.

## What it is

Experimental Microsoft context-engineering tool for getting repos ready for AI coding agents. It scores readiness, generates instructions/evals/dev configs, and runs drift/eval checks.

## Evidence checked

- README documents Measure / Generate / Maintain commands: `readiness`, `instructions`, `eval`, plus init/batch/PR modes.
- Root files include `agentrc.eval.json`, `examples/`, `docs/`, `plugin/`, `vscode-extension/`, `webapp/`, CI config, `SECURITY.md`.
- Package metadata: `@microsoft/agentrc`, MIT, bin `agentrc`, tests via Vitest, active push 2026-05-30.
- README flags the project as experimental and some generation uses the Copilot SDK.
- Local evidence directory: temporary upstream inspection material.

## Strengths

- Turns agent context into a measurable artifact, not just a hand-written prompt file.
- CI/batch/readiness mode is exactly the shape needed before trusting generated repo instructions.
- Can output `AGENTS.md`, making it relevant beyond Copilot/VS Code.

## Risks / caveats

- Experimental; expect breaking changes.
- Generation/eval paths may require Copilot/GitHub credentials and should not be run against sensitive repos first.
- Could create noisy generated instructions if adopted without review.

## Integration ideas

- Run on a copied non-sensitive repo; compare generated `AGENTS.md`/evals against existing project instructions.
- Distill the 9-pillar readiness model into Hermes repo onboarding and GBrain health checks.
- If useful, keep it as a tactical sandbox/CI aide, not a global instruction authority.

## Alternatives / related repos

- [github/spec-kit](github--spec-kit.md)
- [bmad-code-org/BMAD-METHOD](bmad-code-org--BMAD-METHOD.md)
- [eyaltoledano/claude-task-master](eyaltoledano--claude-task-master.md)
- [AI Development Workflow Frameworks](../comparisons/ai-development-workflow-frameworks.md)

## Review candidates and context

- Source-local: Run `npx github:microsoft/agentrc readiness --json` and `instructions --output AGENTS.md` in a copied repo; review diffs before canonical use.
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
