---
title: anthropics/skills — skill-creator
type: repo-intel
aliases:
  - skill-creator
  - Anthropic skill-creator
  - GitHub repo: anthropics/skills skill-creator
source: https://github.com/anthropics/skills/tree/main/skills/skill-creator
url: https://github.com/anthropics/skills
category: agent-skills
topics: [github-repo, agent-skills, hermes-skills, skill-authoring, evals]
status: deep-analyzed
usefulness_score: 91
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-06-11
license: Apache-2.0
checked_ref: 57546260929473d4e0d1c1bb75297be2fdfa1949
---

# anthropics/skills — skill-creator

> Opinionated reference-stack evaluation, reviewed 2026-06-11. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `91/100` — Anthropic's own skill-creation workflow is directly relevant to Hermes/SStack skill authoring: draft → eval prompts → with-skill/baseline runs → human review viewer → quantitative assertions → iterate → optimize trigger description.
- **Recommendation:** `distill-pattern` — borrow the lifecycle and eval harness ideas; do not install it as a second skill runtime or adopt Claude-specific commands literally.
- **Usage observed 2026-06-11:** `pattern-in-use`. Pattern influence in the reference stack, not proof of upstream runtime installation.
- **Review candidate:** Patch Hermes/SStack skill-authoring guidance when next editing skills: require realistic eval prompts for objective workflows, compare against baseline/old skill, and surface results for human review before overfitting revisions.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Skill authoring is core to Hermes/GBrain/SStack; needs adaptation away from Claude-only subprocess assumptions. |
| Leverage | 24/25 | Better skill evals compound across every recurring workflow and reduce silent skill rot. |
| Reuse readiness | 17/20 | Clear SKILL.md plus scripts/schemas/viewer; scripts are usable reference material but tailored to Anthropic/Cowork/Claude flows. |
| Maturity/trust | 13/15 | Anthropic-maintained public repo, very active, Apache-2.0 in the skill directory; high issue count means fast-moving surface. |
| Differentiation | 13/15 | Strongest concrete lifecycle among skill-creation references: baseline runs, timing/tokens, assertion grading, blind comparison, trigger-description evals. |
| **Total** | **91/100** |  |

## Verdict

Treat `skill-creator` as a **skill lifecycle reference**, not a drop-in dependency. Its useful payload is the evaluation loop: make skill changes observable with realistic test prompts, old-vs-new or with-vs-without comparisons, human review of outputs, quantitative assertions where objective, and trigger-description tests with hard negatives. [Source: Anthropic skill-creator `SKILL.md`, https://github.com/anthropics/skills/tree/main/skills/skill-creator, 2026-06-11]

The big warning: several operational instructions are Claude/Cowork-specific (`claude -p`, `present_files`, browser assumptions, subagent mechanics). In Hermes, map these to Hermes `delegate_task`, `skill_manage`, static review files, `skill_view`, and existing SkillOpt/GBrain workflows rather than copying the wrapper. [Source: Anthropic skill-creator `SKILL.md`, https://github.com/anthropics/skills/tree/main/skills/skill-creator, 2026-06-11]

## Reference-stack relevance

- Skill quality compounds across recurring workflows. This gives a concrete process for turning “we should remember this workflow” into a tested, iterated artifact instead of another long prompt file.
- It reinforces the [Thin Harness, Fat Skills](../../../concepts/ai-engineering/thin-harness-fat-skills.md) direction: keep the harness thin, push durable procedure into skills, and evaluate whether the skill actually changes behavior.
- It gives Hermes a practical anti-overfitting rule: improve from test feedback by explaining the why and generalizing, not by adding brittle `ALWAYS/NEVER` clauses for one failing example.

## What it is

A public Anthropic skill folder for creating, testing, improving, packaging, and trigger-optimizing agent skills. The folder contains:

- `SKILL.md`: full workflow and authoring guide.
- `agents/`: grader, blind comparator, and post-hoc analyzer instructions.
- `references/schemas.md`: JSON schemas for evals, grading, benchmark, comparison, analysis, timing, and history.
- `scripts/`: eval runner, aggregation/reporting, description improver, packaging, quick validation.
- `eval-viewer/` and `assets/`: HTML review UI for human evaluation.

[Source: GitHub tree for `anthropics/skills/skills/skill-creator`, 2026-06-11]

## Core patterns to distill

### 1. Intent capture before writing

The skill starts by extracting intent from the current conversation before asking more questions: what the skill enables, trigger contexts, expected output format, and whether test cases make sense. Objective workflows should default toward test cases; subjective work can lean on qualitative review. [Source: Anthropic skill-creator `SKILL.md` lines 47-60, 2026-06-11]

### 2. Descriptions are routing surfaces

Anthropic treats the frontmatter `description` as the primary trigger mechanism, not decorative metadata. Descriptions should include what the skill does plus the contexts/phrases where it should be used, with enough “pushiness” to avoid undertriggering. [Source: Anthropic skill-creator `SKILL.md` lines 64-68, 2026-06-11]

### 3. Progressive disclosure is explicit

The skill's recommended anatomy matches Hermes practice: small `SKILL.md`, optional `scripts/`, `references/`, and `assets/`, with large domain-specific docs loaded only when needed. Keep the main body under roughly 500 lines where possible; large references should have a table of contents. [Source: Anthropic skill-creator `SKILL.md` lines 73-109, 2026-06-11]

### 4. Skill quality means lack of surprise

The source explicitly says a skill's contents should not surprise the user given the skill description and should not contain malware, exploit code, unauthorized access, or data exfiltration behavior. This aligns with SStack prompt-injection and instruction-hygiene rules. [Source: Anthropic skill-creator `SKILL.md` lines 111-114, 2026-06-11]

### 5. Eval loop: with-skill vs baseline, same turn

For each test case, launch both with-skill and baseline/old-skill runs together so they finish under comparable conditions. For new skills, baseline is no skill; for skill revisions, baseline is the old snapshot. Store outputs, metadata, assertions, timing, and grading under iteration-specific workspaces. [Source: Anthropic skill-creator `SKILL.md` lines 163-231, 2026-06-11]

### 6. Human review before self-correction

The viewer exists because final outputs and benchmark numbers are not enough. The human sees prompts, outputs, previous outputs, formal grades, and a feedback box; revisions should focus on concrete user complaints, with empty feedback treated as “fine.” [Source: Anthropic skill-creator `SKILL.md` lines 236-282, 2026-06-11]

### 7. Improve by generalizing, not overfitting

The strongest authoring advice: read transcripts, remove instructions that create wasted work, explain the why, and bundle repeated scripts when every test run independently reinvents the same helper. Avoid brittle all-caps constraints unless the reasoning genuinely requires them. [Source: Anthropic skill-creator `SKILL.md` lines 292-306, 2026-06-11]

### 8. Trigger-description evals need hard negatives

Description optimization uses realistic should-trigger and should-not-trigger queries, including typos, casual phrasing, adjacent domains, and near misses. Simple generic queries are bad tests because they do not exercise the routing problem. [Source: Anthropic skill-creator `SKILL.md` lines 333-404, 2026-06-11]

## Hermes/SStack adaptation notes

- Use `skill_manage` / SStack files for actual skill writes; keep SStack provenance metadata when distilling external ideas.
- Use Hermes `delegate_task` for independent eval/baseline runs when available; otherwise run a smaller inline sanity check and label the reduced rigor.
- Generate a static HTML or markdown review artifact in disposable scratch or a repo-local report path instead of relying on a GUI browser.
- Replace Claude-only `claude -p` description optimization with Hermes SkillOpt where available, or keep it as a future adaptation target.
- Keep upstream scripts as reference; only vendor selected scripts after reviewing command execution, model/API assumptions, and schema compatibility.

## Evidence checked

- **GitHub metadata:** `anthropics/skills`, default branch `main`, pushed `2026-06-09T20:35:19Z`, topic `agent-skills`, stars/forks `149507 / 17637`, archived `false`, GitHub repo license field `null` but `skills/skill-creator/LICENSE.txt` is Apache-2.0. [Source: GitHub API via `gh`, 2026-06-11]
- **Checked ref:** `57546260929473d4e0d1c1bb75297be2fdfa1949`, commit date `2026-06-09T20:35:16Z`. [Source: GitHub API via `gh`, 2026-06-11]
- **Files inspected:** `SKILL.md`, `LICENSE.txt`, `references/schemas.md`, `agents/analyzer.md`, `agents/comparator.md`, `agents/grader.md`, `scripts/quick_validate.py`, `scripts/run_loop.py`, `scripts/run_eval.py`, `scripts/generate_report.py`.
- **Local test:** No runtime execution; this ingest was a read/distill pass, not an adoption test.

## Verified / plausible / source claims

- **Verified:** The skill folder contains the authoring workflow, eval schemas, grader/comparator/analyzer agents, scripts, and review UI described above. [Source: GitHub tree and fetched files, 2026-06-11]
- **Verified:** The `skill-creator` folder includes an Apache-2.0 license file. [Source: `skills/skill-creator/LICENSE.txt`, 2026-06-11]
- **Plausible:** The eval loop should improve Hermes skill quality if adapted to Hermes tooling rather than copied literally.
- **Source claim:** Anthropic's text says skill triggering depends mainly on description metadata and that complex/substantive queries trigger skills more reliably than simple one-step asks. [Source: Anthropic skill-creator `SKILL.md` lines 396-400, 2026-06-11]

## Strengths

- Concrete lifecycle, not just style advice.
- Good separation between authoring, evals, human feedback, grading, analysis, and packaging.
- Strong anti-overfitting guidance for skill revisions.
- Practical trigger-description optimization method with hard negatives.
- Scripts/schemas make the evaluation idea reproducible rather than purely conversational.

## Risks / caveats

- Claude/Cowork-specific assumptions need translation before use in Hermes.
- The full workflow is heavier than needed for small preference or style skills; use it when skill behavior is high-leverage or objectively testable.
- Repo is fast-moving and large; cite checked ref/date when borrowing patterns.
- The GitHub repo-wide license field is null despite folder-level Apache-2.0; preserve the folder license and avoid assuming all repo contents share one license without checking.

## Integration ideas

- Patch `sstack-hermes-skill-authoring` or related guidance with a “minimum eval loop”:
  1. 2-3 realistic prompts.
  2. Baseline/old-skill comparison when behavior matters.
  3. Human-readable review artifact.
  4. Objective assertions only where they are actually objective.
  5. Transcript review for wasted work and repeated helper scripts.
- Add a lightweight Hermes review report template that mirrors Anthropic's viewer fields but works in Discord/headless environments.
- Use this as a benchmark against [mgechev/skills-best-practices](mgechev--skills-best-practices.md), [addyosmani/agent-skills](addyosmani--agent-skills.md), [microsoft/skills](microsoft--skills.md), and [cisco-ai-defense/skill-scanner](cisco-ai-defense--skill-scanner.md).

## Alternatives / related repos

- [mgechev/skills-best-practices](mgechev--skills-best-practices.md) — concise skill-writing rubric.
- [addyosmani/agent-skills](addyosmani--agent-skills.md) — skill lifecycle and examples.
- [microsoft/skills](microsoft--skills.md) — vendor catalog/distribution patterns.
- [google/skills](google--skills.md) — vendor catalog/reference patterns.
- [cisco-ai-defense/skill-scanner](cisco-ai-defense--skill-scanner.md) — security scanner angle.
- [Agent Skills Ecosystem Comparison](../comparisons/agent-skills-ecosystem.md)
- [Coding Agent Skill Systems](../../../concepts/ai-engineering/coding-agent-skill-systems.md)

## Review candidates and guidance

- Review candidate: Distill the baseline comparison + human-review artifact into the SStack/Hermes skill-authoring workflow when creating or revising a non-trivial skill.
- Review candidate: Consider a small Hermes-native static review template instead of adopting Anthropic's viewer wholesale.
- Review candidate: Re-check upstream before copying scripts or schemas into SStack; use checked ref `57546260929473d4e0d1c1bb75297be2fdfa1949` as the baseline.
