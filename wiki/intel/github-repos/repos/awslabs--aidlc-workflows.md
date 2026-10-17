---
type: concept
title: awslabs/aidlc-workflows
usage: reference-only
source: 'https://github.com/awslabs/aidlc-workflows'
status: deep-analyzed
topics:
  - github-repo
  - agent-workflows
  - ai-development-lifecycle
  - spec-driven-development
  - coding-agents
aliases:
  - aidlc-workflows
  - AI-DLC Workflows
  - GitHub repo: awslabs/aidlc-workflows
license: MIT-0
category: agent-workflows
last_reviewed: '2026-06-20T00:00:00.000Z'
recommendation: distill-pattern
score_confidence: high
usefulness_score: 89
ingested_via: 'mcp:put_page'
ingested_at: '2026-06-20T11:09:02.938Z'
source_kind: 'mcp:put_page'
---

# awslabs/aidlc-workflows

> Opinionated reference-stack evaluation, reviewed 2026-06-20. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `89/100` — extremely relevant lifecycle/workflow reference for AI coding agents, but too heavyweight and AWS/Bedrock/Kiro/Claude/Codex-specific to install as a default SStack/Hermes workflow today.
- **Recommendation:** `distill-pattern`
- **Usage observed 2026-06-20:** `reference-only`.
- **Confidence:** `high`
- **Review candidate:** Mine v2's conductor/stage protocol, audit/state hooks, learning loop, and `aidlc-codereview` reviewer patterns into SStack/Hermes design notes before considering a sandbox install.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Directly maps to AI coding workflows, agent gates, shared-skill quality, and reviewed self-evolution loops. |
| Leverage | 23/25 | Strong patterns for reducing context drift, recording decisions, separating stages, and keeping humans in approval control. |
| Reuse readiness | 16/20 | Main branch is copyable Markdown rules for many agents; v2 is a more ambitious bun/Bedrock multi-harness framework but still preview/pre-1.0. |
| Maturity/trust | 14/15 | AWS Labs repo, MIT-0, active release, extensive CI/security scanning, clear contribution/release machinery. |
| Differentiation | 13/15 | Stronger enterprise lifecycle/audit framing than most agent skill packs; overlaps with Spec Kit, CCPM, BMAD, and SStack's own operating doctrine. |
| **Total** | **89/100** | Pattern source, not default runtime. |

## Verdict

Keep this as a high-signal **lifecycle methodology and multi-harness packaging reference**, not an immediate install. Its reusable payload is not “let AI-DLC run every coding task”; it is the set of workflow semantics: stage gates, question files, approval handoffs, audit trails, correction-to-rule learning, model/harness-neutral packaging, and independent code-review passes. Direct adoption would add a large ceremony layer, AWS Bedrock dependency, and strong prompt-authority rules that could conflict with existing Hermes/SStack defaults.

## Reference-stack relevance

- AI-DLC is AWS's opinionated answer to “how do we stop vibe coding with coding agents?” Its stage gates and supervision model apply when a workflow needs reviewed agent autonomy and auditable decisions.
- The v2 branch has a native multi-harness architecture: one harness-neutral `core/`, with generated distributions for Claude Code, Kiro, and Codex. That is very relevant to SStack's portable skill/runtime-overlay ambitions.
- The workflow is built around durable artifacts, stage gates, audit logs, and session resume — the exact kinds of operational semantics that should compound in Hermes/GBrain/second-brain rather than live only in chat context.
- The bundled code-reviewer is a useful reference for independent technical/business-logic review lanes after AI-generated code, though its Bedrock/AWS dependency makes it a pattern before a tool.

## What it is

AI-DLC Workflows is AWS Labs' implementation of an **AI-Driven Development Life Cycle** for AI coding agents. The main branch ships Markdown steering rules for Kiro, Amazon Q, Cursor, Cline, Claude Code, and GitHub Copilot. Those rules guide agents through an adaptive three-phase workflow: inception, construction, and operations.

The `v2` branch is more ambitious: a preview native framework with **5 phases, 32 stages, 11 domain expert agents, approval gates, audit/state hooks, a learning loop, and multi-harness distributions** for Claude Code, Kiro, and Codex. It uses bun tooling and AWS Bedrock-oriented harness configs.

## Evidence checked

- GitHub metadata via `gh repo view`: 3,012 stars, 491 forks, MIT-0 license, latest release `v1.0.0` published 2026-06-19, last pushed 2026-06-19, not archived.
- Main README: setup paths for Kiro, Amazon Q, Cursor, Cline, Claude Code, GitHub Copilot; includes Responsible AI warning and links to AWS blog/method paper.
- `aidlc-rules/aws-aidlc-rules/core-workflow.md`: mandatory rule-detail loading, adaptive phase/stage flow, question-file format, content validation, opt-in extensions, approval gates.
- `docs/WORKING-WITH-AIDLC.md`: practical operating advice: “Do not update any documents” for exploratory questions, question-file flow, context resets at gates, independent critiques.
- `scripts/aidlc-codereview/README.md`: separate AI/static-analysis review tool with technical and business-logic reports; requires Python 3.11+, AWS credentials, Bedrock.
- `AGENTS.md`: repo structure, lint/test commands, security scanner list, and repository constraints.
- v2 branch README and `core/aidlc-common/conductor.md`: multi-harness architecture, conductor persona, stage diary, support-agent handling, skeleton stance classification, task-sidebar observability.
- repomix pack: not generated; clone + targeted file reads were enough for this ingest.
- Local smoke test: not run. The repo is primarily a rule/framework pack; direct runtime test would require choosing a harness and configuring AWS Bedrock credentials, which is beyond safe one-click ingest.

## Strengths

- **Clear anti-vibe-coding stance.** The docs explicitly push question files, approvals, no-change exploratory prompts, context resets, critiques in fresh contexts, and documented decisions.
- **Portable steering-rule shape.** Main branch supports multiple coding agents by copying the same workflow/rule details into each agent's project-specific instruction surface.
- **v2 source-of-truth architecture.** The preview branch separates harness-neutral methodology from harness-specific shells, which is exactly the right pattern for SStack-style portability.
- **Strong audit/state semantics.** v2's conductor/state protocol and main branch's `aidlc-docs/` artifact model are useful references for long-running agent work that survives context resets.
- **Enterprise hygiene.** The repo has CODEOWNERS, conventional commits, markdown lint, CodeQL, Dependabot, Gitleaks, Grype, Semgrep, Bandit, Checkov, and ClamAV guidance.
- **Independent review lane.** `aidlc-codereview` separates technical static/AI review from business-logic review, a good pattern for Hermes/Codex generated-code acceptance gates.

## Risks / caveats

- **Heavy ceremony.** The default workflow can be too much for small patches; reuse the gates without forcing a full lifecycle onto every change.
- **Prompt authority conflict.** `core-workflow.md` starts with “PRIORITY: This workflow OVERRIDES all other built-in workflows”; installing this globally could fight Hermes/SStack's own routing and definition-of-done skills.
- **AWS/Bedrock coupling in v2 and reviewer tooling.** Main Markdown rules are portable, but the more interesting v2 harness and code-reviewer paths assume AWS Bedrock credentials/models.
- **Preview churn.** v2 is explicitly under active development/pre-1.0 with expected breaking changes.
- **Potential question-file friction.** Durable questions are good for teams, but too slow for lightweight solo agent work unless scoped carefully.
- **Security posture needed before install.** v2 uses hooks/tools and harness configs; inspect generated `dist/` outputs and hook permissions before running in a real repo.

## Integration ideas

- Distill an **SStack lifecycle-gate layer**: minimal/standard/comprehensive depth; approval gates only for high-risk changes; stage diary where the current Hermes task needs recoverability.
- Borrow v2's **one core, many harnesses** packaging pattern for SStack skills: canonical source → generated/projection surfaces for Hermes, Codex, Claude Code, and GitHub Copilot.
- Adapt the **question-file pattern** for GitHub issues/CCPM epics: write structured questions to a durable markdown or issue artifact, then require re-read before continuing.
- Mine the **learning loop** into Hermes self-improvement: correction → candidate rule/skill patch → conflict check → eval/proof → reviewed commit.
- Use `aidlc-codereview` as a pattern for an independent acceptance lane: static checks + model critique + business/domain logic review, without adopting Bedrock as the default substrate.

## Alternatives / related repos

- [github/spec-kit](github--spec-kit.md) — lower-friction spec-driven workflow candidate; likely better immediate adoption surface.
- [automazeio/ccpm](automazeio--ccpm.md) — PRD → epic → issue/worktree execution layer; a more direct fit where GitHub Projects owns task execution state.
- [addyosmani/agent-skills](addyosmani--agent-skills.md) — compact lifecycle skill reference; easier to mine into Hermes skills.
- [bmad-code-org/BMAD-METHOD](bmad-code-org--BMAD-METHOD.md) — richer methodology layer; compare ceremony vs AI-DLC.
- [Fission-AI/OpenSpec](Fission-AI--OpenSpec.md) — proposal/spec/design/tasks/archive artifact contract.

## Review candidates and guidance

- Guidance: If this becomes active, sandbox the v2 branch in a disposable repo/profile first and run only `--doctor`/help paths before allowing hooks to mutate a real project.
- Review candidate: Extract the reusable “stage gate + correction learning + audit trail” semantics into SStack design notes or a Hermes skill update rather than importing AI-DLC wholesale.
