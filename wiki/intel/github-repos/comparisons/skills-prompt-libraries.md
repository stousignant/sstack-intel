---
title: Skills / Prompt Libraries Repo Comparison
created: 2026-06-03
updated: 2026-06-03
type: comparison
tags: [github-repos, repo-intelligence, skills, prompts, agent-workflows, sstack]
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/Cranot--claude-code-guide.md
  - wiki/intel/github-repos/repos/LeoYeAI--openclaw-master-skills.md
  - wiki/intel/github-repos/repos/VoltAgent--awesome-openclaw-skills.md
  - wiki/intel/github-repos/repos/github--awesome-copilot.md
  - wiki/intel/github-repos/repos/google-gemini--gemini-skills.md
  - wiki/intel/github-repos/repos/mattpocock--skills.md
  - wiki/intel/github-repos/repos/midudev--autoskills.md
  - wiki/intel/github-repos/repos/multica-ai--andrej-karpathy-skills.md
  - wiki/intel/github-repos/repos/sickn33--antigravity-awesome-skills.md
---

# Skills / Prompt Libraries Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Mine first:** [mattpocock/skills](../repos/mattpocock--skills.md) and [multica-ai/andrej-karpathy-skills](../repos/multica-ai--andrej-karpathy-skills.md). These best match the reference stack's desired portable skills and Hermes behavior: small, composable, anti-overengineering, and engineering-focused.
- **Use as catalogs, not installs:** [github/awesome-copilot](../repos/github--awesome-copilot.md), [sickn33/antigravity-awesome-skills](../repos/sickn33--antigravity-awesome-skills.md), and [midudev/autoskills](../repos/midudev--autoskills.md). They are useful for registry/installer patterns and discovery, but bulk import is a bad idea.
- **Keep vendor/ecosystem references scoped:** [google-gemini/gemini-skills](../repos/google-gemini--gemini-skills.md), [LeoYeAI/openclaw-master-skills](../repos/LeoYeAI--openclaw-master-skills.md), [VoltAgent/awesome-openclaw-skills](../repos/VoltAgent--awesome-openclaw-skills.md), and [Cranot/claude-code-guide](../repos/Cranot--claude-code-guide.md). Load them when their ecosystem is relevant.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Trust boundary | Verdict |
|---|---:|---:|---:|---|---|---|
| mattpocock/skills | 88 | medium-high | low | MIT | Human-curated skill corpus | Selective shared-skill distillation |
| multica-ai/andrej-karpathy-skills | 86 | medium | low | unknown | Single behavior file | Distill wording/patterns only |
| github/awesome-copilot | 84 | high | low | MIT | Official/community catalog | Discovery index |
| google-gemini/gemini-skills | 78 | high | low | Apache-2.0 | Vendor-specific skills | Task-scoped reference |
| sickn33/antigravity-awesome-skills | 76 | medium | medium | MIT | Huge installable catalog | Watch; inspect schemas/safety |
| midudev/autoskills | 74 | medium | medium | CC-BY-NC-4.0 | Mutating installer | Distill installer UX only |
| Cranot/claude-code-guide | 74 | medium | none | unknown | Community auto-updated guide | Reference with official verification |
| LeoYeAI/openclaw-master-skills | 68 | medium | low | MIT | OpenClaw/MyClaw catalog | Low-priority discovery |
| VoltAgent/awesome-openclaw-skills | 64 | medium | none | MIT | OpenClaw awesome list | Low-priority discovery |

## Category map

1. **Small engineering skill corpora** — best source of reusable shared-skill improvements.
2. **Catalogs/registries** — useful for schemas, `llms.txt`, search, categorization, and installer UX; not safe as bulk dependencies.
3. **Vendor/model-specific skills** — load when building with that vendor; keep out of global Hermes behavior.
4. **OpenClaw ecosystem lists** — useful watchlist material while OpenClaw is on hold.
5. **Documentation aggregators** — good orientation; official docs remain authority.

## Reference-stack recommendation

Next concrete move: do a **selective skill-mining pass** on `mattpocock/skills` and `multica-ai/andrej-karpathy-skills`, then separately design a safe catalog/installer pattern using `awesome-copilot`, `antigravity-awesome-skills`, and `autoskills` as references.

Do not install any bulk skillpack into live Hermes/Claude directories. Keep shared skills curated, owned, and portable; popularity is not a reason to import a prompt landfill.

## Open questions

- Which Matt Pocock skills overlap with existing portable skills and Hermes skills and which are genuinely new?
- Can the shared-skill source expose a safe skill recommendation command that is read-only by default?
- What minimal schema should the shared-skill source use for cross-harness skill metadata, bundles, and projections?
- Should vendor-specific skill repos live as references in the vault, runtime skills, or task-loaded snippets?
