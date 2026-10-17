---
title: mgechev/skills-best-practices
type: repo-intel
aliases:
  - skills-best-practices
  - GitHub repo: mgechev/skills-best-practices
source: https://github.com/mgechev/skills-best-practices
category: agent-skills
topics: [github-repo, agent-skills, hermes-skills, skillpacks]
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-05-26
license: no-license-detected
---

# mgechev/skills-best-practices

> Reference-stack fit as reviewed 2026-05-26; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `80/100` — Concise skill-authoring quality rubric: discoverability, progressive disclosure, deterministic scripts, and validation prompts. Strong teaching/reference value; no license was detected during the dated review, so permission to reuse its text/code was not established.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-26:** `reference-only`.
- **Review candidate:** Distill the useful skill-design patterns into Hermes skill authoring/review conventions; do not bulk-import the catalog.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21 | Fits Hermes skill authoring standards and validates current direction. |
| Leverage | 21 | Good rubric can improve every future skill; less direct automation value than scanner. |
| Reuse readiness | 14 | README-only-ish guide plus sample skill; easy to read, not a toolchain. |
| Maturity/trust | 9 | No license detected and no GitHub security policy; treat as idea reference only. |
| Differentiation | 15 | Best concise framing of skill discoverability/progressive disclosure. |

## Verdict

Treat `mgechev/skills-best-practices` as a compact **skill-authoring rubric**, not a dependency. Its progressive-disclosure and discoverability framing matches Hermes's skill system well, but the missing license means quote sparingly and use it as inspiration rather than copied material.

## Reference-stack relevance

- The reference stack's leverage depends on Hermes/GBrain/second-brain skills staying sharp, selectively loaded, auditable, and safe.
- This repo belongs to the **agent-skill ecosystem** category: useful less as another app to run, more as evidence for how skill libraries should be designed, validated, distributed, and secured.
- The immediate stack target is Hermes skill quality, not a new parallel skill runtime.

## What it is

A concentrated guide and sample skill demonstrating professional skill structure: frontmatter discoverability, progressive disclosure, deterministic scripts, and validation prompts.

## Live metadata checked

| Field | Value |
|---|---|
| GitHub URL | https://github.com/mgechev/skills-best-practices |
| Description | Write professional-grade skills for agents, validate them using LLMs, and maintain a lean context window. |
| Stars / forks | 1917 / 137 |
| Primary language | Python |
| Last push | 2026-04-28T16:08:36Z |
| Archived? | False |
| License | no-license-detected |
| Security policy | not detected |

## Evidence checked

- GitHub metadata via `gh repo view mgechev/skills-best-practices` on 2026-05-26.
- README fetched via GitHub API into temporary upstream inspection material.
- Top-level repository contents fetched via GitHub API into the captured upstream metadata snapshot.
- Existing migrated repo note in `wiki/intel/github-repos/repos/mgechev--skills-best-practices.md`.
- README headings/features inspected for install, test, security, and workflow claims.

## Strengths

- Excellent concise explanation of progressive disclosure and frontmatter discoverability.
- Emphasizes deterministic scripts for repetitive checks.
- Useful validation prompt set for skill reviews.
- Low reading cost; high authoring-skill payoff.

## Risks / caveats

- No GitHub license detected; do not copy prose/code wholesale.
- Mostly a guide, not a maintained validation product.
- No security policy detected.

## Integration ideas

- Turn its rubric into a local skill review checklist.
- Patch Hermes skill-authoring guidance with progressive-disclosure / frontmatter discoverability checks if missing.
- Use as a human-readable comparator against Cisco scanner output.

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
