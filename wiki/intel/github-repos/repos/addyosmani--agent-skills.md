---
title: addyosmani/agent-skills
type: repo-intel
aliases:
  - agent-skills
  - GitHub repo: addyosmani/agent-skills
source: https://github.com/addyosmani/agent-skills
category: agent-skills
topics: [github-repo, agent-skills, hermes-skills, skillpacks]
status: deep-analyzed
usefulness_score: 86
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-26
license: MIT
---

# addyosmani/agent-skills

> Opinionated reference-stack evaluation, reviewed 2026-05-26. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `86/100` — Best lifecycle/workflow reference for engineering skills: spec → plan → build → verify → review → ship maps directly to Hermes skill quality and future project-state workflows.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-26:** `reference-only`.
- **Review candidate:** Distill the useful skill-design patterns into Hermes skill authoring/review conventions; do not bulk-import the catalog.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22 | Lifecycle skill design maps cleanly to Hermes project execution habits. |
| Leverage | 23 | Spec/plan/build/verify/review/ship loops could sharpen Hermes work and reduce sloppy execution. |
| Reuse readiness | 17 | Readable repo with commands, agents, hooks, docs; easy to distill, but direct install is Claude/Cursor-shaped. |
| Maturity/trust | 13 | MIT and very active, but no GitHub security policy detected. |
| Differentiation | 11 | Excellent lifecycle framing and command taxonomy. |

## Verdict

Treat `addyosmani/agent-skills` as the best **software-delivery lifecycle skill reference** in this batch. The command taxonomy and workflow structure are more reusable than the repo as a direct dependency. Distill its spec/plan/build/verify/review/ship discipline into Hermes skills and project-state reporting.

## Workload fit

- Reliable agent workflows benefit from skills that are selectively loaded, auditable, safe, and validated against the intended task.
- This repo belongs to the **agent-skill ecosystem** category: useful less as another app to run, more as evidence for how skill libraries should be designed, validated, distributed, and secured.
- The immediate stack target is Hermes skill quality, not a new parallel skill runtime.

## What it is

A broad production-engineering skill library for coding agents, organized around lifecycle commands and reusable personas/checklists for designing, planning, building, verifying, reviewing, and shipping software.

## Live metadata checked

| Field | Value |
|---|---|
| GitHub URL | https://github.com/addyosmani/agent-skills |
| Description | Production-grade engineering skills for AI coding agents. |
| Stars / forks | 45890 / 5087 |
| Primary language | Shell |
| Last push | 2026-05-24T21:03:14Z |
| Archived? | False |
| License | MIT |
| Security policy | not detected |

## Evidence checked

- GitHub metadata via `gh repo view addyosmani/agent-skills` on 2026-05-26.
- README fetched via GitHub API into [upstream README](https://github.com/addyosmani/agent-skills).
- Top-level repository contents fetched via GitHub API into the captured upstream root listing.
- Existing migrated repo note in the curated repo-intelligence folder.
- README headings/features inspected for install, test, security, and workflow claims.

## Strengths

- Very strong lifecycle framing for engineering work.
- Covers skills, agents, hooks, references, and command UX.
- High community traction and active maintenance.
- MIT license enables pattern reuse.

## Risks / caveats

- Direct install flow is shaped around Claude/Cursor/Gemini/opencode, not Hermes specifically.
- No GitHub security policy detected.
- Popularity alone does not establish task fit or quality for any individual skill.

## Integration ideas

- Distill lifecycle commands into Hermes project skills and daily project-state reports.
- Use its personas/checklists as review inspiration for Hermes coding workflows.
- Compare with current `plan`, `test-driven-development`, and `requesting-code-review` skills.

## Alternatives / related repos

- [microsoft/skills](microsoft--skills.md)
- [google/skills](google--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)
- [cisco-ai-defense/skill-scanner](cisco-ai-defense--skill-scanner.md)
- [mgechev/skills-best-practices](mgechev--skills-best-practices.md)
- [Agent Skills Ecosystem Comparison](../comparisons/agent-skills-ecosystem.md)

## Review candidates and context

- Distill useful conventions into Hermes skill authoring/review guidance when working on skills.
- No standalone install action unless a concrete project needs this repo's domain-specific content.
