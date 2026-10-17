---
title: kytmanov/obsidian-llm-wiki-local
type: repo-intel
aliases:
  - obsidian-llm-wiki-local
  - obsidian-llm-wiki
  - olw
  - GitHub repo: kytmanov/obsidian-llm-wiki-local
source: https://github.com/kytmanov/obsidian-llm-wiki-local
category: llm-wiki-second-brain
topics: [github-repo, llm-wiki, obsidian, local-llm, ollama, cli, knowledge-compilation, markdown]
updated: 2026-06-07
tags:
  - llm-wiki
  - github-repos
  - tool-intel
  - obsidian
  - local-llm
  - ollama
  - cli
  - knowledge-compilation
  - markdown
topic: llm-wiki
role: repo-card
status: deep-analyzed
usefulness_score: 90
recommendation: adopt-now
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-24
license: MIT
stars: 649
forks: 105
primary_language: Python
latest_release: v0.8.5
---

# kytmanov/obsidian-llm-wiki-local

> Reference-stack fit as reviewed 2026-05-24; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

> Topic hub: [LLM-wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md)

## Decision

- **Usefulness score:** `90/100` — the strongest direct CLI/code reference for a Hermes-native LLM Wiki compiler: local-first, Python, tested, review-first, provider-flexible, and close to the assessed Markdown-workflow requirements.
- **Recommendation:** `adopt-now` as a sandbox/reference CLI; **do not** make it canonical writer until we validate output quality on copied corpora.
- **Usage observed 2026-05-24:** `reference-only`. Clone inspection and test-suite execution, not runtime adoption.
- **Review candidate:** use this as the main implementation reference for a Hermes-native CLI spec. If piloting an existing tool before building, pilot `olw` on a throwaway vault with a local/OpenAI-compatible provider.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Local-first Markdown/Obsidian CLI maps cleanly to second-brain/GBrain/Hermes; review-first drafts protect canonical vault. |
| Leverage | 23/25 | Could directly save synthesis time for bounded source batches and gives a concrete codebase to borrow from. |
| Reuse readiness | 18/20 | PyPI/uv install, CLI, docs, provider wizard, tests; maintenance mode and successor caveat reduce direct-adoption score. |
| Maturity/trust | 14/15 | 779 tests passed locally, MIT, CI, release, good schemas/state model. |
| Differentiation | 11/15 | Best local-first deterministic compiler in the set; less product/UI breadth than `nashsu/llm_wiki`. |
| **Total** | **90/100** |  |

## Verdict

If a concrete need arises for a CLI that "handles the LLM Wiki altogether," `obsidian-llm-wiki-local` is the closest existing implementation checked. It has the right primitives: `init`, `setup`, `ingest`, `compile`, `review`, `approve`, `reject`, `query`, `lint`, `maintain`, `watch`, `compare`, Git undo, SQLite state, draft publishing, manual-edit protection, provider abstraction, and a real test suite. The catch: the README says it is now in maintenance mode and new work is moving to `kytmanov/synto`. That means we should **study and pilot it**, but if we build our own Hermes/GBrain-native CLI, use its architecture as a reference rather than forking it blindly.

## Workload fit

- It provides a CLI for turning raw notes into an AI-maintained Obsidian wiki with draft review and local/provider-flexible inference.
- It is local-first by default with Ollama, but also works with OpenAI-compatible endpoints including LM Studio, vLLM, Groq, Together, Azure, etc.
- It preserves hand edits and writes drafts before approval, supporting the requirement to keep generated output out of a canonical vault until reviewed.
- It gives Hermes a deterministic state machine to learn from instead of relying on prompt-only procedures.

## What it is

A Python CLI package (`obsidian-llm-wiki`, command `olw`) that converts raw Markdown notes in an Obsidian-style vault into synthesized wiki articles. It uses a fast model for analysis/routing and a heavier model for article writing. The pipeline is:

```text
raw Markdown inputs
→ ingest: fast model extracts summary/wiki/concepts/references/language/quality
→ compile: heavy model writes concept drafts into wiki/.drafts/
→ review: human/agent approves or rejects
→ approve: publish to wiki/
→ query/lint/maintain/watch/compare
```

Live metadata checked 2026-05-24:

- Repo: <https://github.com/kytmanov/obsidian-llm-wiki-local>
- Stars/forks: 649 / 105
- License: MIT
- Primary language: Python
- Latest release: `v0.8.5`, published 2026-05-17
- README explicitly says the project is in maintenance mode and successor work is happening in `kytmanov/synto`.

## Evidence checked

- Shallow upstream clone inspected in disposable storage.
- GitHub metadata via `gh repo view`.
- README quickstart/features/provider docs.
- Key files inspected: `pyproject.toml`, `src/obsidian_llm_wiki/cli.py`, `src/obsidian_llm_wiki/models.py`, `src/obsidian_llm_wiki/pipeline/compile.py`, `src/obsidian_llm_wiki/providers.py`, `src/obsidian_llm_wiki/client_factory.py`, `CLAUDE.md`, tests.
- Test run: `uv run pytest` completed with `779 passed, 1 skipped, 3 warnings` in 281 seconds.

## Verified / plausible / source claims

- **Verified:** CLI package exposes `obsidian-llm-wiki` and `olw` entrypoints.
- **Verified:** project is Python 3.11+, MIT, has substantial offline test coverage, and uses Pydantic models for structured LLM output.
- **Verified:** `AnalysisResult`, `SingleArticle`, and `QueryAnswer` schemas are deliberately small/flat for small-model reliability.
- **Verified:** compile writes to `wiki/.drafts/` and has manual-edit protection based on content hashes.
- **Verified:** provider registry supports Ollama, LM Studio, vLLM, Groq, Together, OpenAI-compatible providers, Azure, and custom endpoints; API keys live in user config/env, not vault config.
- **Verified:** `olw compare` can build isolated preview vaults for model/provider switches.
- **Plausible:** local small models can produce acceptable wiki drafts with the right schemas/prompts; this was not model-smoke-tested because no local inference endpoint was available in this run.
- **Source claim:** README's "self-improving" framing depends on draft review and feedback quality over repeated compiles.

## Strengths

- **Best CLI shape in the set.** It is a real Python CLI, not only instructions.
- **Review-first publication.** Drafts go to `wiki/.drafts/`; approval is explicit.
- **Manual-edit protection.** The compiler detects hand-edited articles and skips overwriting them.
- **State model is practical.** SQLite tracks raw note lifecycle, concepts, articles, failures, query syntheses, and hashes.
- **Provider-flexible without Copilot.** This directly answers the earlier concern: LLM Wiki workflows do not need Copilot if the CLI supports local/OpenAI-compatible providers.
- **Query does not require embeddings.** It routes via index/page selection; embeddings can stay optional in a Hermes design.
- **Git-aware safety.** Automatic operations commit with `[olw]` prefix and `olw undo` uses `git revert`.
- **Tests are real.** The local test run passed 779 tests, which is much stronger evidence than README-only repos.

## Risks / caveats

- **Maintenance mode.** Direct adoption may put us on a path the author considers superseded by `Synto`.
- **Raw note model may not match an existing vault.** It expects a raw-input directory, a wiki directory, `.olw/state.db`, and `wiki.toml`; an established vault may use a different structure.
- **Output quality still needs model validation.** Tests mock clients; they prove code behavior, not that generated concepts are good for a target corpus.
- **SQLite state adds a second state layer.** Useful for a CLI, but needs careful boundaries with Git, GBrain, and Obsidian if adopted.
- **Watcher/auto-commit could be dangerous on canonical vault.** Good for isolated vaults; risky if pointed at the canonical Markdown vault without a review policy.

## Best ideas to steal

1. **Two-tier model roles:** fast analyzer/router + heavier writer.
2. **Small flat schemas for LLM output** to improve reliability on local models.
3. **Draft review lifecycle:** compile → draft → approve/reject with rejection feedback.
4. **Manual-edit protection** through body hashes.
5. **State DB for source/concept/article lifecycle** while keeping Markdown as durable artifact.
6. **Provider wizard + per-invocation overrides** without leaking API keys into vault files.
7. **Model/provider compare mode** in isolated preview vaults.
8. **Git safety:** `[tool]` commit prefixes and undo via revert.
9. **Lint/maintain/query as CLI subcommands** with JSON-capable outputs in a Hermes version.

## Integration ideas

- First pilot: create a throwaway vault, copy 5-10 raw-ish repo README/docs excerpts, run `olw init`, `olw ingest --all`, `olw compile`, `olw review`, inspect drafts.
- If designing a native knowledge compiler, use `olw` as the reference for CLI command surface and state transitions, but replace the LLM backend with Hermes agent/tool calls or Hermes-configured provider adapters.
- For canonical second-brain use, never run watch/auto-approve. Use `compile --drafts` / review queue / git diff / GBrain sync.
- Check `kytmanov/synto` before writing code, because it may already generalize the desired compiler/review capabilities.

## Alternatives / related repos

- [nashsu/llm_wiki](nashsu--llm_wiki.md) — fuller desktop app with graph/search/web clipper/API.
- [atomicstrata/llm-wiki-compiler](atomicstrata--llm-wiki-compiler.md) — existing Node CLI with review queue and MCP surface.
- [AgriciDaniel/claude-obsidian](AgriciDaniel--claude-obsidian.md) — skillpack/vault operating pattern.
- [nvk/llm-wiki](nvk--llm-wiki.md) — multi-runtime protocol/hub/topic model.
- [SamurAIGPT/llm-wiki-agent](SamurAIGPT--llm-wiki-agent.md) — simpler agent scaffold.

## Review candidates and guidance

- Review candidate: Analyze `kytmanov/synto` before committing to a custom CLI build.
- Review candidate: Run an `olw` sandbox on copied non-sensitive raw sources if we want evidence of generation quality.
- Review candidate: Borrow the CLI/state/review architecture for the Hermes-native LLM Wiki CLI spec.
