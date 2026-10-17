---
title: revfactory/harness
type: repo-intel
aliases:
  - harness
  - "GitHub repo: revfactory/harness"
source: https://github.com/revfactory/harness
category: agent-orchestration
topics: [github-repo, agent-orchestration, harness-engineering, claude-code, skill-testing]
status: deep-analyzed
usefulness_score: 69
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-08-30
license: Apache-2.0
---

# revfactory/harness

> Reference-stack evaluation as reviewed 2026-08-30; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `69/100` — strong portable methodology, but the shipped control plane is Claude Code-specific and project maturity is much weaker than its presentation suggests.
- **Recommendation:** `distill-pattern`
- **Usage observed 2026-08-30:** `not-used`.
- **Confidence:** `high`
- **Review candidate:** Preserve the skill-evaluation schema and orchestration patterns; do not install. Revisit only after a real release with CI and a stable, relevant runtime surface.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 15/25 | Harness engineering philosophy fits SStack, but execution depends on Claude Code Agent Teams rather than Hermes delegation. |
| Leverage | 21/25 | Skill A/B evaluation, trigger near-miss tests, handoff artifacts, and team-pattern selection can improve recurring workflows. |
| Reuse readiness | 17/20 | Apache-licensed Markdown references are easy to adapt without importing the plugin. |
| Maturity/trust | 4/15 | No tests, CI, tags, or releases; documentation describes automation that is absent; high single-maintainer concentration. |
| Differentiation | 12/15 | Most philosophy is already captured, but its concrete skill-eval contract and rerun-aware orchestrator template add useful detail. |
| **Total** | **69/100** | **Distill the method; reject runtime adoption.** |

## Verdict

`revfactory/harness` is a Claude Code meta-skill that generates domain-specific agent definitions, skills, and an orchestrator from a domain description. Its valuable payload is a compact methodology for choosing a team topology, testing skill outcomes, validating trigger boundaries, and preserving file-based handoffs across reruns. Distill those patterns into existing workflow doctrine; do not install a Claude-specific overlay that writes `.claude/agents/`, `.claude/skills/`, and `CLAUDE.md`.

## Workload fit

- Its **with-skill vs without-skill** protocol turns skill quality from prompt aesthetics into comparative evidence.
- Its **should-trigger vs near-miss should-not-trigger** set is a practical regression test for Hermes skill routing.
- Its `_workspace/{phase}_{agent}_{artifact}` handoffs and initial/partial/full-rerun branching fit durable, multi-session agent work.
- Its six team shapes provide a usable vocabulary: pipeline, fan-out/fan-in, expert pool, producer-reviewer, supervisor, and hierarchical delegation.
- It reinforces SStack's existing direction: thin root pointers, progressively disclosed skills, deterministic validation, and independent QA.

## What it is

A documentation-only Claude Code plugin containing one Korean-language meta-skill and six reference guides. Given a project/domain description, it instructs Claude Code to scaffold specialized agents, skills, an orchestrator, workspace handoffs, validation steps, and a minimal `CLAUDE.md` pointer. Its default team execution uses Anthropic Agent Teams primitives such as `TeamCreate`, `SendMessage`, and `TaskCreate`.

## Evidence checked

- GitHub metadata on 2026-08-30: `8,855` stars, `1,252` forks, Apache-2.0, created 2026-03-26, current API `pushedAt` 2026-07-24. Source: https://github.com/revfactory/harness
- Independently cloned current `main` at `cceac68ea1d0ad198ef4b7b906cd238375836387` into a disposable source checkout.
- Inspected `README.md`, `CHANGELOG.md`, `.claude-plugin/plugin.json`, `docs/experimental-dependency.md`, `skills/harness/SKILL.md`, all six skill references, repository tree, and `_workspace/` dogfooding artifacts.
- Repository shape: 35 tracked files; 21 Markdown files; no implementation code, package manifest, test suite, or `.github/workflows/` directory.
- GitHub release metadata: no tagged release surfaced through `gh repo view`; the delegated full-history review also found zero git tags and zero GitHub releases.
- A separate source review reported completion; findings remain bounded by the direct inspection and execution limits below.
- Smoke test: no runtime test was appropriate because the repo is a Markdown skillpack requiring Claude Code's experimental Agent Teams surface. Bounded verification used clone, metadata, and direct file inspection only.

## Strengths

- Clear six-pattern topology and team-vs-subagent decision framework.
- Strong progressive-disclosure and reuse-before-create skill-writing guidance.
- Concrete evaluation artifacts: assertion-based grading, timing capture, comparative baselines, and trigger-boundary tests.
- Good boundary-coherence QA idea: inspect both sides of an integration and test incrementally rather than only at the end.
- Plain Markdown and Apache-2.0 make selective adaptation cheap.
- `_workspace/` files provide real evidence that the author dogfooded multi-agent production on this repository.

## Risks / caveats

- **Wrong runtime:** official support is Claude Code only and team execution depends on its Agent Teams surface. Using it with Hermes would overlap the existing orchestration layer.
- **Prompt/config supply-chain surface:** direct use generates project agents/skills and edits `CLAUDE.md`; those mutations require review and should not be imported wholesale.
- **Documentation-reality gap:** `docs/experimental-dependency.md` claims nightly compatibility CI and an SLA-monitoring GitHub Action, but the repository has no workflows. It also references pending/missing documents.
- **No executable validation:** zero code and zero tests mean the project's validation claims are procedures, not continuously enforced guarantees.
- **Release hygiene:** version badges and a SemVer changelog exist without tags or GitHub releases.
- **Bus factor:** delegated history review found roughly 89% of commits from one maintainer.
- **Benchmark caveat:** the reported `+60%` average-quality result is author-measured on 15 tasks with third-party replication pending; treat it as a source claim, not independent proof.

## Integration ideas

- Treat the six team topologies and comparative skill-evaluation contract as source material for the reference architecture’s team/skill composition layer, not as justification for a separate harness generator.
- Add comparative **with-skill / without-skill** fixtures and near-miss routing tests to SStack's existing skill validation workflow.
- Use the six team topologies as a selection rubric, but preserve Hermes' cheaper default: delegate independent work; use collaboration only when workers genuinely need shared negotiation.
- Standardize substantial delegated workflows around a declared execution mode, artifact naming, normal/error test scenarios, and explicit rerun behavior.
- Reuse the integration-coherence QA check in acceptance verification: compare both sides of each contract rather than checking file existence alone.

## Alternatives / related repos

- [coleam00/Archon](coleam00--Archon.md) — stronger runtime-level deterministic workflow engine and sandbox candidate.
- [steipete/agent-scripts](steipete--agent-scripts.md) — stronger shared-skill/source-of-truth pattern reference.
- [automazeio/ccpm](automazeio--ccpm.md) — stronger durable issue/worktree execution contract.
- [deepseek-ai/deepseek-harness](deepseek-ai--deepseek-harness.md) — much stronger composable runtime architecture and verification discipline.
- [harness engineering](../../../concepts/ai-engineering/harness-engineering.md) — reference-stack synthesis.

## Review guidance

- Preserve the skill-evaluation and orchestration deltas in existing SStack/Hermes doctrine when those skills are next revised; do not create a parallel harness generator.
- Re-evaluate only if upstream ships real CI, tagged releases, and a runtime-independent or Hermes-relevant artifact contract.
