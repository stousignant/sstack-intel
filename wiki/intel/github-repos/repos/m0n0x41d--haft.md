---
title: m0n0x41d/haft
type: repo-intel
source: https://github.com/m0n0x41d/haft
category: decision-harness
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# m0n0x41d/haft

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `84/100` — Best decision-governance pattern in this mini-batch: evidence decay, parity enforcement, WorkCommission, and measurement loops are highly reusable. Direct install is heavier/riskier than pattern extraction until Hermes has a concrete decision-harness gap.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Write a tiny Hermes decision-record/evidence-decay design note before any install attempt.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22 | Maps to the reference stack’s sparring-partner protocol: compare options, expose assumptions, keep/revert based on evidence. |
| Leverage | 22 | Could prevent premature coding by forcing frame/compare/decide/measure before execution. |
| Reuse readiness | 14 | Go binary/MCP install and multiple host-agent integrations; install script exists but should not be piped into shell in main environment. |
| Maturity/trust | 13 | Active releases, MIT, Go modules, pre-commit/lint/test structure; alpha TUI/desktop surfaces should be ignored. |
| Differentiation | 13 | Evidence decay and parity enforcement are more distinctive than ordinary spec/task managers. |

## Verdict

Best decision-governance pattern in this mini-batch: evidence decay, parity enforcement, WorkCommission, and measurement loops are highly reusable. Direct install is heavier/riskier than pattern extraction until Hermes has a concrete decision-harness gap.

## Reference-stack relevance

- This sits in the same lane as repository readiness, spec-first coding, execution-state visibility, and long-running agent task hygiene.
- The value is mostly **artifact contracts**: readiness reports, instruction files, evals, specs, decision records, phase state, and verification evidence.
- Default stance: sandbox/read-only first; do not add another global command framework unless it beats existing Hermes skills and Spec Kit on a tiny task.

## What it is

Engineering-decision governor for agentic coding: MCP plugin + CLI harness around specifying, comparing, deciding, bounded commissions, evidence, and stale-assumption review.

## Evidence checked

- README frames Haft as “Specify → Think → Run → Govern,” not a coding agent.
- Production surfaces: MCP plugin for Claude Code/Codex and CLI harness; TUI/Desktop are alpha and not recommended for production.
- README names `haft spec check`, seven MCP tools, `/h-reason`, WorkCommission harness, evidence workflow, trust-score/evidence decay.
- Go module, SQLite, tree-sitter, Anthropic/OpenAI SDK dependencies; releases up to v7.1.0 as of 2026-05-13.
- Local evidence directory: temporary upstream inspection material.

## Strengths

- Evidence expiry/decay is exactly the missing piece in many AI-generated decision records.
- Parity enforcement aligns with the reference stack’s preference to compare existing tools before custom builds.
- WorkCommission pattern can sharpen autonomous coding handoffs.

## Risks / caveats

- Install path uses a shell script; do not run in main environment without inspection.
- Broad integrations and alpha desktop/TUI add surface area.
- Could become a parallel project-governance layer if adopted wholesale.

## Integration ideas

- Distill “evidence freshness” into durable design rationale and evidence checks for project decisions; keep executable state in the existing work tracker.
- Use WorkCommission semantics in Hermes delegation: objective, constraints, evidence, measurement, expiry.
- If sandboxing, inspect installer first and use a disposable repo/profile.

## Alternatives / related repos

- [github/spec-kit](github--spec-kit.md)
- [bmad-code-org/BMAD-METHOD](bmad-code-org--BMAD-METHOD.md)
- [eyaltoledano/claude-task-master](eyaltoledano--claude-task-master.md)
- [AI Development Workflow Frameworks](../comparisons/ai-development-workflow-frameworks.md)

## Review candidates and context

- Source-local: Write a tiny Hermes decision-record/evidence-decay design note before any install attempt.
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
