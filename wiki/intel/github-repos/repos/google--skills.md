---
title: google/skills
type: repo-intel
aliases:
  - GitHub repo: google/skills
source: https://github.com/google/skills
category: agent-skills
topics: [github-repo, agent-skills, hermes-skills, skillpacks]
status: deep-analyzed
usefulness_score: 74
recommendation: reference-only
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-26
license: Apache-2.0
---

# google/skills

> Reference-stack fit as reviewed 2026-05-26; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `74/100` — Useful official Google/GCP skill catalog and Apache-licensed reference, but mostly valuable when the operator is actively using GCP/Gemini/Cloud Run rather than as a default Hermes skill source.
- **Recommendation:** `reference-only`.
- **Usage observed 2026-05-26:** `reference-only`.
- **Review candidate:** Distill the useful skill-design patterns into Hermes skill authoring/review conventions; do not bulk-import the catalog.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 18 | Good reference for GCP/Gemini tasks; less universal for current stack. |
| Leverage | 16 | Useful when Google Cloud/Gemini work becomes active, otherwise mostly dormant reference. |
| Reuse readiness | 17 | Simple skills repo and npx install; narrow product scope. |
| Maturity/trust | 14 | Apache-2.0, Google-backed, pushed 2026-05-21, security policy enabled. |
| Differentiation | 9 | Official Google skill catalog; not uniquely useful outside GCP. |

## Verdict

Treat `google/skills` as a **reference-only official vendor skill catalog**. It is useful when the operator is doing GCP/Gemini work, and its Apache-2.0 license makes pattern reuse comfortable. It is not a top active-stack priority unless Google Cloud becomes a near-term deployment surface.

## Reference-stack relevance

- The reference stack's leverage depends on Hermes/GBrain/second-brain skills staying sharp, selectively loaded, auditable, and safe.
- This repo belongs to the **agent-skill ecosystem** category: useful less as another app to run, more as evidence for how skill libraries should be designed, validated, distributed, and secured.
- The immediate stack target is Hermes skill quality, not a new parallel skill runtime.

## What it is

Google's official Agent Skills catalog for Google products and technologies, including GCP services, Gemini/API surfaces, and Google Cloud architectural guidance.

## Live metadata checked

| Field | Value |
|---|---|
| GitHub URL | https://github.com/google/skills |
| Description | Agent Skills for Google products and technologies |
| Stars / forks | 10554 / 831 |
| Primary language | Python |
| Last push | 2026-05-21T16:27:48Z |
| Archived? | False |
| License | Apache-2.0 |
| Security policy | https://github.com/google/skills/security/policy |

## Evidence checked

- GitHub metadata via `gh repo view google/skills` on 2026-05-26.
- README fetched via GitHub API into temporary upstream inspection material.
- Top-level repository contents fetched via GitHub API into the captured upstream metadata snapshot.
- Existing migrated repo note in `wiki/intel/github-repos/repos/google--skills.md`.
- README headings/features inspected for install, test, security, and workflow claims.

## Strengths

- Official source for GCP/Gemini/Google product skills.
- Apache-2.0 license and active maintenance.
- Good vendor-specific reference when Google Cloud work appears.
- Small/simple enough to inspect without heavy tooling.

## Risks / caveats

- Mostly relevant only when GCP/Gemini work is active.
- Less evidence of tests in the README than Microsoft/Cisco/Agent Skills repos.
- Should not become generic Hermes context by default.

## Integration ideas

- Keep as a reference source for future GCP/Gemini deployment work.
- Use its Well-Architected style as inspiration for cloud-specific Hermes skills if the operator starts a GCP project.
- Do not install globally.

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
