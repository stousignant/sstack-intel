---
title: Agent Skills Ecosystem Comparison
created: 2026-05-26
updated: 2026-06-15
type: comparison
tags: [github-repos, agent-skills, hermes-skills, skill-security]
status: active
sources:
  - wiki/intel/github-repos/repos/anthropics--skills-skill-creator.md
  - wiki/intel/github-repos/repos/microsoft--skills.md
  - wiki/intel/github-repos/repos/google--skills.md
  - wiki/intel/github-repos/repos/addyosmani--agent-skills.md
  - wiki/intel/github-repos/repos/cisco-ai-defense--skill-scanner.md
  - wiki/intel/github-repos/repos/mgechev--skills-best-practices.md
  - wiki/concepts/ai-engineering/agent-skill-overlays-and-upstream-drift.md
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-15
review_cadence: quarterly
---

# Agent Skills Ecosystem Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Install/sandbox now:** [cisco-ai-defense/skill-scanner](../repos/cisco-ai-defense--skill-scanner.md) — scan copied Hermes/user skills before trusting more third-party skillpacks.
- **Distill into Hermes skill practice:** [anthropics/skills skill-creator](../repos/anthropics--skills-skill-creator.md), [addyosmani/agent-skills](../repos/addyosmani--agent-skills.md), [microsoft/skills](../repos/microsoft--skills.md), [mgechev/skills-best-practices](../repos/mgechev--skills-best-practices.md).
- **Keep as conditional vendor reference:** [google/skills](../repos/google--skills.md) — useful when GCP/Gemini work becomes active.

**Do not ingest skill repositories wholesale.** The leverage is a **quality/security pipeline for Hermes skills**: authoring rubric, selective loading, validator/scanner, and action extraction.

## Upstream customization / overlay verdict

Current agent-skill ecosystems provide skill scopes, plugin namespaces, visibility controls, and plugin distribution, but not a mature standard for “overlay this upstream skill with local changes.” Claude Code supports personal/project/enterprise precedence and `skillOverrides`; plugin skills are namespaced (`plugin-name:skill-name`) rather than directly shadowed. Codex frames skills as reusable workflows and plugins as distribution units, with `AGENTS.md`, memories, MCP, and subagents as complementary layers. The Agent Skills standard provides arbitrary `metadata`, but no merge/override semantics. [Source: [agent skill overlays and upstream drift](../../../concepts/ai-engineering/agent-skill-overlays-and-upstream-drift.md), 2026-06-15]

Reusable implication: treat upstream skills as pristine dependencies or pattern sources. Put stack-specific behavior in separately owned companion/replacement skills with overlay metadata, use host settings to disable/hide upstream skills when needed, and reserve patch queues or forks for explicit exceptions.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Local-first | Verdict |
|---|---:|---:|---:|---|---|---|
| [anthropics/skills skill-creator](../repos/anthropics--skills-skill-creator.md) | 24/25 | 13/15 | Medium | Apache-2.0 folder license | Yes | Distill eval loop, human review, baseline comparison, and trigger-description testing. |
| [cisco-ai-defense/skill-scanner](../repos/cisco-ai-defense--skill-scanner.md) | 24/25 | 14/15 | Medium | Other | Yes | Sandbox now as skill-security scanner. |
| [addyosmani/agent-skills](../repos/addyosmani--agent-skills.md) | 22/25 | 13/15 | Low | MIT | Yes | Distill lifecycle/command taxonomy. |
| [microsoft/skills](../repos/microsoft--skills.md) | 22/25 | 14/15 | Low | MIT | Yes | Distill catalog/testing/distribution patterns. |
| [mgechev/skills-best-practices](../repos/mgechev--skills-best-practices.md) | 21/25 | 9/15 | Very low | no license detected | Yes | Use as authoring rubric only. |
| [google/skills](../repos/google--skills.md) | 18/25 | 14/15 | Low | Apache-2.0 | Yes | Reference for GCP/Gemini tasks. |

## Category map

The repos split into three subtypes:

1. **Vendor skill catalogs** — Microsoft and Google. Useful when their ecosystems are active; dangerous if bulk-loaded into Hermes by default.
2. **Skill authoring/lifecycle references** — Anthropic skill-creator, Addy Osmani, and Minko Gechev. Useful as process/quality guidance; Anthropic is strongest on eval/review mechanics.
3. **Skill security tooling** — Cisco Skill Scanner. Useful as a practical guardrail before importing or publishing skills.

## Conditional reference-stack guidance

Recommended first step: **Cisco scanner in static mode**. For a Hermes-based skill library considering third-party skills, run this bounded evaluation:

1. Use a disposable copy of a representative skill subset, excluding secrets and personal content.
2. Run `cisco-ai-defense/skill-scanner` in local/static mode first, no cloud/LLM analyzers.
3. Compare findings against the skill-authoring rubric from Addy/Microsoft/Mgechev.
4. Update the existing skill-authoring/review procedure only if the scanner/rubric exposes a reproducible gap.

If this experiment is noisy, keep the scanner as reference-only. If it catches real issues with low noise, consider it for the existing skill-review workflow.

## Open questions

- Does Skill Scanner handle Hermes skill layout cleanly, or does it need an adapter/custom metadata filename?
- Is the Cisco license compatible with local use and CI integration?
- Which Hermes skill-authoring guidance already covers progressive disclosure, discovery frontmatter, and deterministic validation?
