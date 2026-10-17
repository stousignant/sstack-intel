---
title: coleam00/skills
source: https://github.com/coleam00/skills
type: repo-intel
category: agent-skills
topics: [github-repo, agent-skills, instruction-evaluation]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-11
license: MIT
---

# coleam00/skills

## Decision

**82/100 · distill-pattern · medium confidence.** Preserve the instruction-evaluation and process-learning patterns; do not bulk-import the corpus or adopt its autonomous runner. This is source intelligence, not an installation or implementation commitment.

Dated evaluation lens: an existing local-first assistant and curated portable skills library, with independent verification and clear knowledge/execution ownership. The ordinary coding loop overlaps established capabilities; the meta-skills provide greater marginal value. Usage at this review: reference-only, with no installation, hooks, model experiments or activation.

## Scorecard

| Factor | Points | Rationale |
|---|---:|---|
| Stack fit | 23/25 | Skill lifecycle, instruction evaluation and knowledge freshness are highly relevant. |
| Leverage | 22/25 | Better evidence for pruning instructions and diagnosing repeated process failures. |
| Reuse readiness | 16/20 | Readable Markdown and supporting code; Claude paths, tool scopes and write assumptions need adaptation. |
| Maturity/trust | 10/15 | MIT, recent activity, substantial factory test scaffolding; safety gaps and no local runtime validation. |
| Differentiation | 11/15 | Rule-level ablation and state/event auditing are more distinctive than another coding-loop pack. |
| **Total** | **82/100** | Useful pattern reference rather than a new workflow owner. |

## Reusable intelligence

Cole Medin's repository packages the prime → plan → implement → validate → review → commit → PR loop, surrounding planning/worktree skills, meta-skills and copy-in hooks. The pinned tree contains **36 SKILL.md files**, whereas the README still says 35. It also contains executable Python/shell and deployment/merge templates: the README's plain-Markdown framing does not describe the whole trust surface.

### Instruction ablation

The strongest method is to use an agreed byte-identical real task, repeat both control and stripped arms, grade blind against individual testable rules, and distinguish **untested** from **no observed effect**. Separate new-file work from edits: nearby existing code can teach conventions even when explicit instructions are absent. Preserve hooks/permissions when testing prompt effects. These are evaluation-design patterns, not evidence that any particular rule is expendable. A small number of successful probes cannot justify deleting unexercised security or release constraints.

### Process evolution

Compare planned versus actual work, classify justified versus problematic divergence, then identify missing context, validation or automation. This is a process retrospective, not code review. The supplied workflow consumes a plan and execution report; a trustworthy adaptation should check the actual diff and tool evidence rather than accepting the implementer's retrospective as truth. Its alignment score is subjective.

### Knowledge freshness

Distinguish replaceable current **state** from append-only **events**; date verification rather than merely moving a line; inspect what the assistant actually receives, including truncation. Preserve unsupported versus contradicted findings. The scanner is a money-oriented heuristic, not a general factual contradiction detector: it intentionally leaves lifecycle/status contradictions to judgment. A zero result is not proof of freshness. Avoid parallel audit ledgers and competing write paths.

### Autonomous-factory architecture

Useful design lessons include product-specific validation, positive proof that checks ran, independent holdout assessment, explicit state transitions and building the trigger last. Retain these lessons without treating the template as authorization for unattended merging or deployment. A fresh model session and tool-name denial alone do not establish filesystem or credential isolation.

## Evidence checked

Pinned revision: `847be0848ae7b997ae4420bc0eac267177a066a2`; GitHub metadata reported last push `2026-10-07T16:41:20Z`. Evidence acquired from revision-pinned public raw URLs after resolving the GitHub tree; 120 selected text/source files downloaded, not a complete binary/source archive. Parent reviewed primary files and independently checked the material delegated risk anchors.

- [README](https://github.com/coleam00/skills/blob/847be0848ae7b997ae4420bc0eac267177a066a2/README.md) and root MIT license.
- Ablation SKILL.md, comparison rubric, map_layer.py and run_ablation.py.
- system-evolution-review/SKILL.md; second-brain-audit/SKILL.md and scripts/audit.py.
- build-dark-factory/SKILL.md, runner README, workflow/merge templates and auditor code.
- hooks/pre_tool_use_secrets.py and hooks/stop_tests_must_pass.py.
- **Static validation:** all 30 acquired Python files parsed with Python AST; zero syntax errors. Parsing does not execute code or prove behavior.
- **Not run:** upstream tests, hooks, factory doctor/auditor, ablation, providers, installers or benchmarks. Factory test scaffolding exists; no efficacy result was reproduced. No Repomix pack was generated.

## Risks and caveats

1. **Ablation is not mutation-free.** run_ablation.py:264–270 creates result output and can append to the original repo's `.gitignore`; :189–193 removes/prunes Git worktree metadata. Default subprocesses inherit host access and credentials, so detached worktrees are not a security sandbox.
2. **Auditing can execute target code.** build-dark-factory/scripts/_audit_runner.py:159–165 extracts and `exec()`s a TRANSITIONS expression from the inspected runner. Do not run it against untrusted repositories as a harmless static checker.
3. **Holdout boundary is weaker than claimed.** run-workflow.sh:225 denies Read/Glob/Grep for the holdout, but :414–415 permits `Bash(python -c:*)`. Static inference: Python can read files despite those tool-name restrictions absent stronger filesystem isolation. No exploit was executed.
4. **Hooks are bounded heuristics.** The secrets guard acknowledges bypass routes and fails open on unexpected errors. The stop hook permits completion on timeout/errors or an active stop-hook cycle; its test-edit guard compares retained files and misses deleted tests. They are not absolute enforcement guarantees.
5. **Portability and authority need review.** Slash commands, Claude-specific paths/tool scopes, report writes, automatic Git handling and deployment templates are not drop-in replacements for another harness's ownership rules. Preserve MIT notice on substantial copies.

## Strengths

- Explicit distinction between prompt guidance, on-demand instructions and executable enforcement.
- Practical per-rule evaluation rubric with noise, applicability and neighboring-code confounds.
- Current-state/event separation and lossless restructuring principles.
- Factory templates make several validation and state-machine concepts concrete rather than merely marketing them.

## Alternatives / related repos

- [Skills / prompt libraries comparison](../comparisons/skills-prompt-libraries.md).
- [mattpocock/skills](mattpocock--skills.md) — smaller composable engineering corpus.
- [Anthropic skill creator](anthropics--skills-skill-creator.md) — lifecycle and eval reference.
- [google-research/rrsi](google-research--rrsi.md) — hypothesis-led harness evaluation reference.

## Review candidates

1. **Rule-level blinded ablation:** rationale: stronger evidence than subjective prompt cleanup; review question: does it add value beyond existing before/after and holdout procedures? Promotion condition: an explicitly authorized representative task/model budget and safe runner, with multiple tasks before broad deletion.
2. **Plan/diff/process retrospective:** rationale: distinguish justified discovery from instruction failures; review question: can existing RCA owners capture this without another recurring report? Promotion condition: recurring evidenced divergence with a specific owner-supported remedy.
3. **State-versus-event audit:** rationale: diagnose stale always-loaded answers without rewriting history; review question: which existing source/write path is responsible? Promotion condition: a demonstrated retrieval error and scoped lossless fix with preserved provenance.

## Disposition

Private operating implications remain in the originating discussion; no private owner page was changed. No executable commitment was promoted. No skill was copied or installed.
