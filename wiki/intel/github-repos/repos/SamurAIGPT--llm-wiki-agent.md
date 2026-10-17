---
title: SamurAIGPT/llm-wiki-agent
type: repo-intel
aliases:
  - llm-wiki-agent
  - LLM Wiki Agent
  - GitHub repo: SamurAIGPT/llm-wiki-agent
source: https://github.com/SamurAIGPT/llm-wiki-agent
category: llm-wiki-second-brain
topics: [github-repo, llm-wiki, second-brain, knowledge-graph, codex, obsidian]
updated: 2026-06-07
tags:
  - llm-wiki
  - github-repos
  - tool-intel
  - second-brain
  - knowledge-graph
  - codex
  - obsidian
topic: llm-wiki
role: repo-card
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: medium
last_reviewed: 2026-05-24
license: MIT
---

# SamurAIGPT/llm-wiki-agent

> Reference-stack evaluation as reviewed 2026-05-24. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

> Topic hub: [LLM-wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md)

## Decision

- **Usefulness score:** `82/100` — very strong conceptual fit and already influencing the stack, but less reusable as a direct tool than as a pattern source.
- **Recommendation:** `distill-pattern`
- **Usage observed 2026-05-24:** `pattern-in-use`. Pattern influence, not production use of the upstream tool.
- **Review candidate:** borrow deterministic health checks, append-only logs, graph-aware maintenance, and bounded generated-wiki sandboxes; do not point it at the canonical vault.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Near-perfect fit for the agent-maintained Markdown wiki direction. |
| Leverage | 21/25 | Strong pattern leverage for Hermes/GBrain workflows and repo-intelligence batches. |
| Reuse readiness | 13/20 | Useful scaffold and scripts, but less productized than an installable CLI and still requires agent discipline. |
| Maturity/trust | 12/15 | MIT, readable local-first repo, deterministic health script; no releases and LLM-quality claims are not benchmarked. |
| Differentiation | 12/15 | Clear raw-source → agent-owned-wiki → health/lint/graph pattern worth preserving. |
| **Total** | **82/100** |  |

## Verdict

**Pattern already in use; upstream tool still sandbox-only.** `llm-wiki-agent` is a compact implementation of an agent-maintained Markdown wiki: immutable raw inputs, structured pages, wikilinks, health/lint checks, and graph output. It can complement—but does not replace—an established retrieval/index layer or canonical Markdown source. A bounded copied-corpus trial can compare generated pages with curated output; run deterministic `health.py` before LLM-powered `lint.py` and inspect explicit versus inferred edges.


## Workload fit

- It addresses a recurring knowledge-work workload: turning scattered documents, repository notes, and research inputs into a persistent interlinked Markdown wiki rather than isolated chat summaries.
- It is agent-harness-native rather than SaaS-native: the repo ships `AGENTS.md`, `CLAUDE.md`, `GEMINI.md`, and Claude slash commands, so the workflow is portable across Codex, Claude Code, Gemini CLI, and OpenCode.
- For workflows using Hermes with GBrain and a canonical Markdown knowledge base, its bounded-ingestion pattern can add generated synthesis with repeatable structural checks.
- Its local-file-first outputs and MIT license support inspectability, portability, and low lock-in.

## Reuse / inspiration potential

- **Direct reuse:** plausible as a sandbox, not as the canonical brain. Clone it into a test workspace, feed it a small copied corpus, and compare its generated wiki against GBrain/Obsidian output.
- **Pattern to borrow:** immutable raw inputs + agent-owned `wiki/` outputs + append-only `log.md` (upstream wiki/tool layout) + deterministic health gate + periodic semantic lint + graph output.
- **Stack area improved:** second-brain ingestion, repo-intelligence output structure, graph/lint quality gates, and agent-owned maintenance workflows.
- **Autonomy leverage:** gives Hermes a concrete pattern for maintaining a generated knowledge layer with repeatable health checks instead of relying on memory and ad hoc summaries.
- **Freedom leverage:** if adapted well, this kind of workflow reduces manual note maintenance and makes accumulated sources easier to turn into decisions, experiments, and reusable assets.

## What it is

`llm-wiki-agent` is a Python/Markdown knowledge-base scaffold and agent instruction pack. Users place source material in the raw-input directory, then ask an AI coding agent to ingest/query/lint/build-graph. The agent writes into `wiki/` using a defined schema: source notes, entity pages, concept pages, synthesis pages, an index, an overview, and a log. Python helper scripts support conversion, structural health checks, semantic linting, query synthesis, and graph generation.

## Evidence checked

- **GitHub metadata:** `SamurAIGPT/llm-wiki-agent`; Python; MIT; 2,715 stars; 319 forks; pushed `2026-05-06`; no latest release; topics include `llm`, `knowledge-base`, `wiki`, `claude-code`, `knowledge-graph`, `obsidian`, `markdown`, `codex`, `rag`, `gemini`, `personal-knowledge-management`.
- **README:** checked from `https://raw.githubusercontent.com/SamurAIGPT/llm-wiki-agent/main/README.md` and the repomix pack. It claims source ingest, entity/concept pages, living overview, contradiction flags, graph output, lint reports, and multi-format ingest via `markitdown`.
- **DeepWiki / external summary:** attempted `https://deepwiki.com/SamurAIGPT/llm-wiki-agent`, but the fetch returned empty content in this environment. Treat this run as README + GitHub metadata + repomix code inspection, not DeepWiki-validated.
- **repomix pack:** generated a temporary Repomix inspection pack; 28 files, ~42,286 tokens, ~166k chars. Not stored in the vault.
- **Key files inspected:** `README.md`, `AGENTS.md`, `docs/automated-sync.md`, `wiki/tools/ingest.py`, `wiki/tools/health.py`, `wiki/tools/lint.py`, `wiki/tools/query.py`, `wiki/tools/build_graph.py`, `pyproject.toml`, `LICENSE`.
- **Local smoke test:** inspected in a disposable clone of [the upstream repository](https://github.com/SamurAIGPT/llm-wiki-agent) and ran `python3 wiki/tools/health.py --json`; it completed successfully on the empty starter wiki with no structural issues.

## Verified / plausible / source claims

- **Verified:** repo contains multi-agent instruction files (`AGENTS.md`, `CLAUDE.md`, `GEMINI.md`), Claude command files, Python tools for ingest/query/lint/health/graph, a raw-input starter directory, `wiki/`, and `graph/` directories, and MIT license.
- **Verified:** `wiki/tools/health.py` is deterministic and ran successfully in a local clone with no API calls.
- **Verified from code:** `wiki/tools/ingest.py` supports many convertible extensions through `markitdown`, calls LiteLLM, updates `index.md` (upstream wiki/tool layout), `overview.md` (upstream wiki/tool layout), source/entity/concept pages, appends log entries, and runs post-ingest validation.
- **Plausible:** the wiki-building workflow can be useful for bounded corpora and research sandboxes, especially when a coding agent is already driving the process.
- **Source claim:** contradiction flagging and high-quality entity/concept extraction depend on LLM behavior and were not independently benchmarked in this pilot.

## Strengths

- **Useful implementation reference:** it is a small, readable example of an agent-maintained LLM wiki workflow that can inform Hermes/GBrain ingestion and validation.
- **Local-first Markdown shape:** outputs are normal files and wikilinks, so results can be inspected, diffed, indexed, or imported elsewhere.
- **Harness-portable:** the same core workflow is documented for Codex/OpenCode via `AGENTS.md`, Claude via `CLAUDE.md` and slash commands, and Gemini via `GEMINI.md`.
- **Health/lint separation:** deterministic `health.py` is explicitly separated from LLM-powered `lint.py`, which is a good cost-control and reliability pattern for Hermes/GBrain tasks.
- **Graph layer is simple and inspectable:** graph output is JSON/HTML built from wikilinks and optional inferred edges, rather than hidden in a proprietary service.
- **Maintenance signal is decent:** recent commits in April/May 2026 added multi-format ingest, dependency pinning, and docs updates; GitHub currently shows one open issue and one open PR.

## Risks / caveats

- **Not a replacement for GBrain:** it is a scaffold/instruction pack, not a full retrieval/indexing system with embeddings, source registration, CLI/MCP integration, or Hermes-native tools.
- **Quality depends on the agent:** the most important operations are LLM-mediated, so output consistency will depend on the active model, prompt following, and context management.
- **No release discipline yet:** GitHub reports no latest release; treat it as a fast-moving repo rather than stable infrastructure.
- **Potential vault-sprawl risk:** if pointed directly at the canonical second-brain without guardrails, it could generate lots of duplicate or low-quality pages. Use a sandbox/copied corpus first.
- **LiteLLM/API dependency for real ingest/lint/query:** README says no separate API key is needed if your coding agent does the work, but the Python scripts themselves call LiteLLM for LLM operations.
- **Graph inference cost/risk:** inferred edges can add value, but they can also hallucinate weak links unless confidence thresholds and audits are strict.

## Integration ideas

- **Repo-intelligence output pattern:** adapt the raw-input directory → generated wiki → health/lint/report pattern to the GitHub-stars pipeline. Raw evidence remains temporary; curated repo notes go into `wiki/intel/github-repos/repos/`.
- **Second-brain sandbox:** create a disposable copy of a small non-sensitive Markdown corpus and test whether `llm-wiki-agent` produces useful entity/concept/overview pages without contaminating the canonical vault.
- **GBrain companion, not competitor:** use this repo as inspiration for generated synthesis pages and structural checks, then index the curated outputs with GBrain.
- **Hermes skill improvement:** borrow the health/lint boundary for Hermes knowledge workflows: fast deterministic checks every run; slower LLM quality audits only periodically or when a threshold is met.
- **Graph experiment:** compare its graph output against GBrain graph/timeline goals when a defined graph-quality question justifies the comparison.

## Alternatives / related repos

- [atomicstrata/llm-wiki-compiler](atomicstrata--llm-wiki-compiler.md) — likely better for compiling raw sources into a wiki as a CLI/tooling pipeline.
- [garrytan/gbrain](garrytan--gbrain.md) — the AI/index/query layer over the canonical Markdown vault.
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md) — more graph/visualization-heavy codebase/document knowledge graph direction.
- [Michaelliv/markit](Michaelliv--markit.md) — source normalization tool that overlaps with `markitdown`/conversion needs.
- [SamurAIGPT/llm-wiki-agent](SamurAIGPT--llm-wiki-agent.md) should be compared against GBrain and LLM Wiki compiler before adopting any generated-wiki workflow broadly.

## Review candidates and guidance

- Review candidate: Sandbox test: copy 5–10 non-sensitive Markdown files into a disposable llm-wiki-agent raw-input directory, run an agent-assisted ingest, and compare the generated `wiki/` against current GBrain/Obsidian notes.
- Review candidate: Extract reusable design rules into the `github-star-repo-intelligence` skill if this pattern proves useful for repo-intelligence batches.
- Completed: Created comparison note for `llm-wiki-agent`, `llm-wiki-compiler`, and GBrain roles in [LLM Wiki tools comparison](../comparisons/llm-wiki-second-brain.md).
- Guidance: Do not point it directly at the canonical vault until the sandbox shows high-quality, low-duplication output.
