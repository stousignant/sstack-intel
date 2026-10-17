---
title: AgriciDaniel/claude-obsidian
type: repo-intel
aliases:
  - claude-obsidian
  - Claude Obsidian
  - GitHub repo: AgriciDaniel/claude-obsidian
source: https://github.com/AgriciDaniel/claude-obsidian
category: llm-wiki-second-brain
topics: [github-repo, llm-wiki, obsidian, claude-code, agent-skills, second-brain, knowledge-management]
updated: 2026-06-07
tags:
  - llm-wiki
  - github-repos
  - tool-intel
  - obsidian
  - claude-code
  - agent-skills
  - second-brain
  - knowledge-management
topic: llm-wiki
role: repo-card
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-24
license: MIT
stars: 5456
forks: 621
primary_language: Python
latest_release: v1.6.0
---

# AgriciDaniel/claude-obsidian

> Reference-stack evaluation as reviewed 2026-05-24. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

> Topic hub: [LLM-wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md)

## Decision

- **Usefulness score:** `84/100` — excellent pattern library for Claude/Obsidian LLM Wiki operations, but it would overlap the agent and indexing layers already assigned to Hermes and GBrain.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-24:** `reference-only`. Inspected in a disposable clone; not adopted as a runtime.
- **Review candidate:** steal the operational ideas that fit Hermes: hot cache, manifest/delta tracking, cross-project vault referencing, deterministic address allocation, semantic tiling, and separate ingest/query/lint/save skills. Do **not** clone its whole vault layout over the canonical second-brain.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 22/25 | Strong Obsidian/wiki fit, but assumes Claude Code + plugin/vault conventions rather than Discord → Hermes → second-brain → GBrain. |
| Leverage | 22/25 | Very good source of skill design, wiki lifecycle, hot cache, and maintenance patterns. |
| Reuse readiness | 15/20 | Easy to inspect and MIT; direct install is Claude Code/plugin-oriented and would overlap with existing Hermes skills. |
| Maturity/trust | 13/15 | Popular, MIT, release `v1.6.0`, docs, tests for deterministic helpers; young but coherent. |
| Differentiation | 12/15 | Strongest "skills + Obsidian vault as product" reference in the set. |
| **Total** | **84/100** |  |

## Verdict

`claude-obsidian` is better treated as a pattern source than a CLI to adopt. It treats the wiki as the product, chat as interface, and agent skills as the operating system around an Obsidian vault. Where Hermes owns skills, memory, and interaction while GBrain owns indexing/query and curated Markdown remains canonical, the best reuse is **instruction architecture and maintenance mechanics**; another Claude-first vault companion would create overlapping control planes.

## Reference-stack relevance

- It operationalizes Karpathy's LLM Wiki pattern with a concrete skillpack: `/wiki`, `/save`, `/autoresearch`, `/canvas`, ingest, query, lint, and fold workflows.
- It has good conventions for keeping agent-maintained knowledge durable: immutable sources in the `.raw` directory, `wiki/` generated knowledge, `hot.md` (upstream wiki/tool layout), `log.md` (upstream wiki/tool layout), `index.md` (upstream wiki/tool layout), and source manifests.
- It shows how to make a knowledge system portable across coding agents via `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, Cursor/Windsurf rules, and skills.
- Its DragonScale pieces may inform self-improving memory systems: deterministic address allocation, fold rollups, and semantic tiling for duplicate detection.

## What it is

A Claude Code plugin plus preconfigured Obsidian vault that builds a persistent, compounding wiki from raw sources. The repo is mostly Markdown skills/docs plus small deterministic helper scripts. It ships a sample vault, Obsidian settings/plugins, slash commands, and 11 skills around wiki setup, ingest, lint, query, save, autoresearch, canvas, defuddle, Obsidian syntax, and wiki folding.

Live metadata checked 2026-05-24:

- Repo: <https://github.com/AgriciDaniel/claude-obsidian>
- Stars/forks: 5,456 / 621
- License: MIT
- Primary language: Python
- Latest release: `v1.6.0`, published 2026-04-24
- Topics include `claude-code`, `obsidian`, `second-brain`, `karpathy-llm-wiki`, `agent-skills`, `knowledge-graph`, `ai-second-brain`.

## Evidence checked

- Shallow clone of [the upstream repository](https://github.com/AgriciDaniel/claude-obsidian) inspected.
- GitHub metadata via `gh repo view`.
- README sections on setup, commands, modes, MCP setup, Obsidian plugins, and cross-project vault referencing.
- Key files inspected: `skills/wiki/SKILL.md`, `skills/wiki-ingest/SKILL.md`, `skills/wiki-lint/SKILL.md`, `skills/wiki-fold/SKILL.md`, `scripts/allocate-address.sh`, `scripts/tiling-check.py`, `scripts/boundary-score.py`, `Makefile`, `AGENTS.md`, `CLAUDE.md`, `LICENSE`.
- Test run: `make test` succeeded. It ran address allocation tests, tiling-check unit tests, and boundary-score tests; all passed.

## Verified / plausible / source claims

- **Verified:** repo ships an Agent Skills-style skillpack, slash commands, sample wiki vault, and Obsidian configuration.
- **Verified:** `wiki` skill defines the three-layer model: immutable source docs in the `.raw` directory, `wiki/` LLM-generated KB, and `CLAUDE.md`/skills as schema/instructions.
- **Verified:** `wiki-ingest` includes delta tracking via the source `.manifest.json`, source summary pages, entity/concept pages, overview/index/log/hot-cache updates, and contradiction callouts.
- **Verified:** `wiki-lint` specifies orphan/dead-link/stale-claim/missing-page/frontmatter/address/semantic-tiling checks and report output.
- **Verified:** DragonScale helper tests passed locally; address allocation uses `flock`, and semantic tiling refuses remote Ollama endpoints unless explicitly allowed.
- **Plausible:** hot cache + cross-project referencing can reduce token cost for multi-session project context; quality depends on agents actually following the skill rules.
- **Source claim:** autonomous research and multi-agent ingestion quality are README/skill claims, not independently benchmarked in this run.

## Strengths

- **Skill architecture is strong.** It decomposes wiki management into focused skills instead of one giant prompt.
- **Hot cache is a useful primitive.** `hot.md` (upstream wiki/tool layout) gives future sessions recent context without reading the whole vault.
- **Delta tracking is explicit.** The source `.manifest.json` maps source hash → pages created/updated, which is exactly the kind of state a Hermes CLI should make deterministic.
- **Maintenance is first-class.** Linting, dashboarding, canvas maps, folds, and semantic duplicate checks are not afterthoughts.
- **Security thinking shows up in helper scripts.** `tiling-check.py` refuses remote embedding exfiltration by default, rejects symlinked pages, caps body size, and uses locks/cache versioning.
- **MIT license.** Patterns and small helper ideas are reusable when attribution is retained.

## Risks / caveats

- **Claude-first assumptions.** The install story is Claude Code plugin/marketplace oriented; Hermes should not inherit Claude-specific UX or slash-command assumptions blindly.
- **Potential marketing/community cruft.** The skill includes a community footer and opinionated Obsidian plugin choices. These are not required by the reusable workflow patterns.
- **Prompt discipline burden.** Many core operations depend on the agent carefully following Markdown instructions; deterministic code is limited to helper pieces.
- **Vault sprawl risk.** A typical ingest can create 8-15 pages. That is powerful but dangerous when applied to a canonical vault without review/promotion gates.
- **Sample vault != an established vault.** It prefers the `.raw` source directory + `wiki/`; an existing vault may already have repo-intelligence, concept, project, and indexing conventions.

## Best ideas to steal

1. **Hot cache** as a compact recent-context file for bounded wiki/project contexts.
2. **Source manifest/delta tracking**: source hash, ingest timestamp, pages created/updated.
3. **Skill decomposition**: setup/orchestrator, ingest, query, lint, save, fold, research.
4. **Contradiction callouts** instead of silently overwriting claims.
5. **Deterministic address IDs** for generated pages or durable records where a vault needs stable page identity beyond paths.
6. **Semantic tiling lint** as an optional duplicate detector, with local-only embedding guardrails.
7. **Cross-project wiki reference block**: projects can read a shared vault through `hot.md` → `index.md` → specific pages.

## Integration ideas

- For a future Hermes-native LLM Wiki CLI, copy the *contracts*, not the whole layout: `doctor`, `ingest`, `compile`, `review`, `lint`, `fold`, `sync`.
- Add a source-manifest layer to repo-intelligence ingestion so Hermes can tell which raw sources produced which concept/repo notes.
- Use hot-cache files per major workspace only when they reduce repeated reads; don't create yet another global memory competing with GBrain.
- If DragonScale-like folds return, keep them extractive, idempotent, and dry-run-first.

## Alternatives / related repos

- [nashsu/llm_wiki](nashsu--llm_wiki.md) — richer product/app implementation.
- [atomicstrata/llm-wiki-compiler](atomicstrata--llm-wiki-compiler.md) — better direct CLI candidate generator.
- [kytmanov/obsidian-llm-wiki-local](kytmanov--obsidian-llm-wiki-local.md) — stronger deterministic Python CLI + local provider implementation.
- [nvk/llm-wiki](nvk--llm-wiki.md) — more ambitious multi-agent/hub protocol.
- [SamurAIGPT/llm-wiki-agent](SamurAIGPT--llm-wiki-agent.md) — simpler agent scaffold.

## Review candidates and guidance

- Review candidate: Distill hot-cache + manifest + lint/fold conventions into the Hermes-native LLM Wiki CLI spec.
- Guidance: Avoid installing the Claude plugin as a parallel interface unless a workflow has an explicit Claude Code compatibility requirement.
