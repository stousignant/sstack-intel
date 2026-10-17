---
title: nvk/llm-wiki
type: repo-intel
aliases:
  - nvk llm-wiki
  - LLM Wiki protocol
  - GitHub repo: nvk/llm-wiki
source: https://github.com/nvk/llm-wiki
category: llm-wiki-second-brain
topics: [github-repo, llm-wiki, agent-skills, codex-plugin, claude-code-plugin, opencode, research-workflow, knowledge-management]
updated: 2026-06-07
tags:
  - llm-wiki
  - github-repos
  - tool-intel
  - agent-skills
  - codex-plugin
  - claude-code-plugin
  - opencode
  - research-workflow
  - knowledge-management
topic: llm-wiki
role: repo-card
status: deep-analyzed
usefulness_score: 86
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-24
license: MIT
stars: 463
forks: 62
primary_language: Shell
latest_release: v0.10.2
---

# nvk/llm-wiki

> Reference-stack evaluation as reviewed 2026-05-24; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

> Concept: [LLM-wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md)

## Decision

- **Usefulness score:** `86/100` — strongest protocol/operations reference for a multi-agent LLM Wiki, but mostly instruction/plugin packaging rather than a self-contained compiler runtime.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-24:** `reference-only`. cloned and inspected; no active install.
- **Review candidate:** borrow hub/topic isolation, inventory/dataset layers, deterministic local helpers, audit/librarian semantics, archive lifecycle, and multi-runtime packaging ideas for a Hermes-native design.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Agent-native, Markdown-first, multi-runtime, and maps well to Hermes skills/GBrain; its hub structure may be too separate from an established vault layout. |
| Leverage | 23/25 | Excellent operating semantics for source queues, topic wikis, inventory, audits, datasets, collection, and archiving. |
| Reuse readiness | 15/20 | Installable as Claude/Codex/OpenCode plugin/instructions, plus deterministic helper script; not a conventional library/CLI compiler. |
| Maturity/trust | 13/15 | MIT, recent releases, tests/fixtures, sync scripts; young but actively hardened. |
| Differentiation | 12/15 | Best multi-runtime protocol and topic-hub model in the set. |
| **Total** | **86/100** |  |

## Verdict

`nvk/llm-wiki` is not the simplest tool to run, but it is the most mature **operating protocol**. It frames the agent as compiler/query engine and the wiki as an executable artifact. Its big contribution is not a model provider or UI; it is the lifecycle model: hub → topic wikis → source captures, compiled wiki, inventory, datasets and output → compile/query/lint/audit/librarian/archive/collect. For an existing Hermes/GBrain deployment, adapt the lifecycle semantics while retaining the current runtime and canonical knowledge source.

## Reference-stack relevance

- It explicitly supports multiple agent runtimes: Claude Code, OpenAI Codex, OpenCode, Pi, and any agent via `AGENTS.md`.
- It has a stronger notion of **topic isolation** than the other repos, useful when ingesting repos, articles, YouTube, and multiple research domains without cross-contamination.
- It adds durable operational layers missing from simpler LLM Wiki repos: inventory, datasets, output artifacts, audits, librarian passes, archive lifecycle, and collection catalogs.
- It aligns with Hermes' direction: skills/protocols orchestrate deterministic helpers; local Markdown remains inspectable; agents perform judgment.

## What it is

A portable LLM Wiki protocol distributed as Claude Code plugin, Codex plugin, OpenCode/Pi instruction file, and standalone `AGENTS.md`. It also includes a local deterministic helper script at `scripts/llm-wiki` for checks that do not need an LLM, especially `lint` and `archive`.

Its default structure is a lightweight hub with isolated topic wikis:

```text
HUB/
├── wikis.json
├── _index.md
├── log.md
└── wiki/topics/<topic>/
    ├── raw/
    ├── wiki/
    ├── inventory/
    ├── datasets/
    ├── output/
    ├── inbox/
    ├── log.md
    └── config.md
```

Live metadata checked 2026-05-24:

- Repo: <https://github.com/nvk/llm-wiki>
- Stars/forks: 463 / 62
- License: MIT
- Primary language: Shell, with large Markdown/plugin payload and Python helper script
- Latest release: `v0.10.2`, published 2026-05-23

## Evidence checked

- Shallow clone inspected at a disposable source checkout.
- GitHub metadata via `gh repo view`.
- README sections on install, quickstart, architecture, runtime packaging, and changelog.
- Key files inspected: `AGENTS.md`, `claude-plugin/skills/wiki-manager/SKILL.md`, [LLM Wiki Skill](https://github.com/nvk/llm-wiki/blob/main/plugins/llm-wiki/skills/wiki/SKILL.md), `plugins/llm-wiki-opencode/skills/wiki-manager/SKILL.md`, `scripts/llm-wiki`, sync scripts, test fixtures, lint assertions.
- Smoke check: `python3 scripts/llm-wiki --help` and `python3 scripts/llm-wiki lint --help` both ran successfully.

## Verified / plausible / source claims

- **Verified:** repo ships runtime-specific packaging for Claude Code, Codex, OpenCode/Pi, plus portable `AGENTS.md`.
- **Verified:** `claude-plugin/skills/wiki-manager/SKILL.md` defines hub path resolution, topic-wiki routing, core principles, workflows for ingestion/collection/inventory/datasets/archive/compile/query/lint/audit/output/lessons-learned, activity logs, and structural guardian checks.
- **Verified:** `scripts/llm-wiki` is a deterministic local helper, not a model runtime; it exposes `lint` and `archive`, validates frontmatter/structure/link/source issues, and supports JSON output.
- **Verified:** the protocol uses dual-linking — Obsidian wikilinks plus Markdown links — to serve both humans and agents.
- **Plausible:** topic isolation and inventory/dataset layers could reduce vault sprawl in broad multi-source ingestion; requires careful mapping to the existing second-brain layout.
- **Source claim:** parallel multi-agent research and thesis-driven investigation are protocol capabilities, not benchmarked runtime performance in this run.

## Strengths

- **Best multi-runtime strategy.** It treats Claude/Codex/OpenCode/Pi wrappers as packaging around one behavior layer.
- **Topic isolation is smart.** Not every source belongs in one giant wiki context. Topic sub-wikis avoid query pollution.
- **Inventory and datasets are first-class.** It separates durable tracking records and large/external data from compiled wiki articles.
- **Audit/librarian semantics are stronger than simple lint.** It has a model for trust, provenance, output drift, and maintenance reports.
- **Derived indexes as cache.** Markdown/frontmatter are source of truth; `_index.md` is a rebuildable navigation layer.
- **Deterministic helper script.** `scripts/llm-wiki` gives agents reliable local checks without needing model calls.
- **Archive lifecycle.** Quiet preservation of old topic wikis is better than deletion or endless active-context bloat.

## Risks / caveats

- **Instruction-heavy.** Much of the system is protocol text; runtime quality depends on the agent following it.
- **Not a direct compiler CLI.** The local helper does not perform LLM compilation; the agent does. For workflows requiring one deterministic command to compile candidates, this is less direct than `olw` or `llm-wiki-compiler`.
- **Separate hub may conflict with canonical vault.** The reference stack assumes an existing canonical Markdown vault and retrieval registration; a separate hub could become a competing brain.
- **Complexity creep.** Inventory, datasets, collect, audit, librarian, output, archive, thesis research — useful, but too much for v0 of a Hermes-native CLI.
- **Plugin ecosystems differ.** Codex/Claude/OpenCode packaging ideas are useful, but Hermes skill/tool packaging has its own conventions.

## Best ideas to steal

1. **Hub/topic isolation** — especially for broad article/video/repo ingestion where not all domains should contaminate each other.
2. **Inventory layer** for candidates, source queues, watch items, durable questions, and tasks that are not factual wiki claims.
3. **Dataset manifests** for large/external corpora instead of copying everything into Markdown.
4. **Derived index protocol** — rebuildable `_index.md` from frontmatter/files, not a fragile hand-maintained truth source.
5. **Dual links** for Obsidian + agent/GitHub readability.
6. **Structural guardian** after writes: verify what changed, indexes, directory placement, registry sync, archived scope.
7. **Audit/librarian workflows** for trust and provenance, not just broken-link linting.
8. **Multi-runtime packaging as generated mirrors** from one source of truth.

## Integration ideas

- Treat the existing Markdown vault as the hub/canonical source, not a separate knowledge root, unless a reversible experiment proves topic sub-wikis should live elsewhere.
- Add an inventory/candidate layer for future ingestion queues: articles to read, repos to analyze, YouTube videos to ingest, concepts needing enrichment.
- For a Hermes CLI, start with a narrow subset: `init`, `ingest`, `propose`, `review`, `lint`, `sync`, `inventory`. Defer full audit/librarian/collect/dataset machinery until v1.
- Use `scripts/llm-wiki` as a reference for local deterministic lint/JSON output, not as the whole runtime.

## Alternatives / related repos

- [kytmanov/obsidian-llm-wiki-local](kytmanov--obsidian-llm-wiki-local.md) — best direct Python CLI compiler reference.
- [atomicstrata/llm-wiki-compiler](atomicstrata--llm-wiki-compiler.md) — best existing Node compiler with review queue/MCP.
- [nashsu/llm_wiki](nashsu--llm_wiki.md) — best full product implementation.
- [AgriciDaniel/claude-obsidian](AgriciDaniel--claude-obsidian.md) — best Claude/Obsidian skillpack reference.
- [SamurAIGPT/llm-wiki-agent](SamurAIGPT--llm-wiki-agent.md) — simpler starter scaffold.

## Review candidates and guidance

- Review candidate: Use the hub/topic/inventory/dataset/audit semantics as inspiration for the Hermes-native LLM Wiki spec.
- Guidance: Do not create a separate home-directory brain unless mapping to the canonical vault is explicit and reversible.
