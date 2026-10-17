---
title: cisco-ai-defense/skill-scanner
type: repo-intel
aliases:
  - skill-scanner
  - GitHub repo: cisco-ai-defense/skill-scanner
source: https://github.com/cisco-ai-defense/skill-scanner
category: skill-security
topics: [github-repo, agent-skills, hermes-skills, skillpacks, security, prompt-injection, static-analysis, supply-chain]
status: deep-analyzed
usefulness_score: 90
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-26
license: Other
---

# cisco-ai-defense/skill-scanner

> Opinionated reference-stack evaluation, reviewed 2026-05-26. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `90/100` — Highest immediate action value: a purpose-built scanner for agent skills with static, dataflow, YARA, LLM, CI/SARIF, and pre-commit modes. Worth sandbox-testing against Hermes/user skills before trusting more third-party skillpacks.
- **Recommendation:** `adopt-now`.
- **Usage observed 2026-05-26:** `not-used`.
- **Review candidate:** Sandbox-run this scanner against copied Hermes/user skills, then decide whether to add it to skill authoring/review workflows.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24 | Direct fit because Hermes and second-brain increasingly rely on third-party/user skills. |
| Leverage | 24 | Could prevent prompt injection/data exfiltration before skillpacks are trusted or imported. |
| Reuse readiness | 17 | Python package, CLI, SDK, GitHub Actions, pre-commit, SARIF; needs sandbox trial before production use. |
| Maturity/trust | 14 | Active, tests/docs/security policy present; license is reported as Other and must be checked before redistribution. |
| Differentiation | 11 | Purpose-built skill-security scanner; rare and immediately relevant. |

## Verdict

Treat `cisco-ai-defense/skill-scanner` as the one repo in this batch worth an **adopt-now sandbox**. Hermes is accumulating skills from multiple sources; a scanner for prompt injection, exfiltration, malicious commands, and suspicious skill behavior is exactly the kind of guardrail needed before scaling skill imports.

## Workload fit

- Reliable agent workflows benefit from skills that are selectively loaded, auditable, safe, and validated against their intended tasks.
- This repo belongs to the **agent-skill ecosystem** category: useful less as another app to run, more as evidence for how skill libraries should be designed, validated, distributed, and secured.
- The immediate stack target is Hermes skill quality, not a new parallel skill runtime.

## What it is

A security scanner for agent skill files. It combines static rules, bytecode/pipeline inspection, behavioral dataflow, optional LLM analysis, VirusTotal/cloud integrations, SARIF reporting, and CI/pre-commit workflows.

## Live metadata checked

| Field | Value |
|---|---|
| GitHub URL | https://github.com/cisco-ai-defense/skill-scanner |
| Description | Security Scanner for Agent Skills |
| Stars / forks | 2046 / 256 |
| Primary language | Python |
| Last push | 2026-04-30T01:53:23Z |
| Archived? | False |
| License | Other |
| Security policy | https://github.com/cisco-ai-defense/skill-scanner/security/policy |

## Evidence checked

- GitHub metadata via `gh repo view cisco-ai-defense/skill-scanner` on 2026-05-26.
- README fetched via GitHub API into [upstream README](https://github.com/cisco-ai-defense/skill-scanner).
- Top-level repository contents fetched via GitHub API into the captured upstream root listing.
- Existing migrated repo note in the curated repo-intelligence folder.
- README headings/features inspected for install, test, security, and workflow claims.

## Strengths

- Directly targets the new attack surface: agent skills as executable/prompt supply chain.
- CI/pre-commit/SARIF paths make it operationally adoptable.
- Multiple analysis modes reduce reliance on one brittle detector.
- Docs are explicit about limitations and safe interpretation of findings.

## Risks / caveats

- License reported as `Other`; inspect `LICENSE` before redistribution or vendoring.
- LLM/cloud analyzers may need credentials and can add cost/privacy concerns.
- No scanner proves a skill safe; treat results as guardrail evidence, not a guarantee.

## Integration ideas

- Run on a copied subset of Hermes skills first.
- If useful, add as an optional pre-commit/CI check for SStack skill changes (`skills/shared/...`).
- Use findings to patch vulnerable or overbroad skills before importing more third-party skills.

## Alternatives / related repos

- [microsoft/skills](microsoft--skills.md)
- [google/skills](google--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)
- [cisco-ai-defense/skill-scanner](cisco-ai-defense--skill-scanner.md)
- [mgechev/skills-best-practices](mgechev--skills-best-practices.md)
- [Agent Skills Ecosystem Comparison](../comparisons/agent-skills-ecosystem.md)

## Review candidates and context

- Non-binding guidance; executable state belongs to the established issue tracker.
- Do not wire into production/CI until the license and false-positive profile are understood.
