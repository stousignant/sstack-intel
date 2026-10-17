---
title: AsyncFuncAI/deepwiki-open
type: repo-intel
aliases:
  - deepwiki-open
  - Grok Wiki
  - GitHub repo: AsyncFuncAI/deepwiki-open
source: https://github.com/AsyncFuncAI/deepwiki-open
category: code-intelligence
topics: [github-repo, repo-intelligence, codebase-documentation, llm-wiki, rag, self-hosted]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT
---

# AsyncFuncAI/deepwiki-open

> Reference-stack evaluation as reviewed 2026-05-28. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — strongest as a self-hosted DeepWiki pattern/reference for repo documentation, but too broad and UI-heavy to replace an established code-intelligence layer.
- **Recommendation:** `distill-pattern` — steal the repo → generated wiki → diagrams → RAG-chat flow; do not install as a default Hermes dependency yet.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Use as a comparison benchmark when improving Hermes/GBrain repo documentation flows, especially generated wiki review and diagram UX.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 21/25 | Directly overlaps repo-intelligence and LLM Wiki workflows; supports GitHub/GitLab/Bitbucket and local-ish operation. |
| Leverage | 22/25 | Could compress unfamiliar-codebase onboarding and generate human-readable docs/diagrams fast. |
| Reuse readiness | 17/20 | Docker/Next/FastAPI setup, multi-provider support, README/API docs, but likely more app than sidecar. |
| Maturity/trust | 12/15 | MIT, very active, huge star/fork counts, tests present; security posture not clearly documented in root. |
| Differentiation | 12/15 | Open DeepWiki-style product with wiki UX and RAG; overlaps GBrain/Serena/Graphify but emphasizes documentation output. |

## Verdict

DeepWiki-Open is worth keeping as a **design oracle** for generated repository wikis, not as a new canonical memory/index layer. The useful pattern is the product loop: fetch a repo, build a code corpus, generate structured wiki pages and Mermaid diagrams, then support RAG-style questions against that generated documentation. Where GBrain already owns indexing/query and curated Markdown is the durable artifact, use DeepWiki-Open to improve repo-intelligence and LLM Wiki workflows rather than create a competing source of truth.

## Reference-stack relevance

- Could provide a reference UX for turning codebase analysis into navigable docs instead of ephemeral chat summaries.
- Multi-provider support, including Ollama/OpenRouter/OpenAI/Gemini/Bedrock-style paths, fits the “reuse tools, avoid bespoke unless needed” preference.
- The danger is seductive duplication: another app, another vector/RAG store, another generated-wiki surface. Use it to improve Hermes/GBrain workflows rather than adding it as always-on infra.

## What it is

DeepWiki-Open, now branded around Grok Wiki, is an open-source implementation attempt of DeepWiki. The README says it analyzes repositories, generates comprehensive documentation, creates visual diagrams, and organizes the output into an interactive wiki. The backend is FastAPI/Poetry Python; frontend is Next 15/React 19.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 16,606 stars, 1,866 forks, MIT, Python primary language, pushed 2026-05-22.
- README: repo-to-wiki generation, diagrams, GitHub/GitLab/Bitbucket support, Grok Wiki live download link.
- Root files: `Dockerfile`, `docker-compose.yml`, `src/`, `api/`, `tests/`, `test/`, `package.json`, `uv.lock`.
- `package.json`: Next 15, React 19, Mermaid, markdown rendering, syntax highlighting.
- `api/pyproject.toml`: FastAPI, Uvicorn, OpenAI, Gemini, Ollama, Bedrock, FAISS, tiktoken, dotenv.
- `api/README.md`: local storage, conversation history, RAG implementation, provider env vars and config files.

## Strengths

- Clear open-source implementation of the DeepWiki product pattern.
- Self-hostable enough to study locally; Docker and multiple provider configs exist.
- Strong visual/documentation emphasis: generated wiki + Mermaid diagrams + chat.
- Good fit as a benchmark for whether a repo-intelligence note helps a reader understand an unfamiliar repository.

## Risks / caveats

- UI/app scope is heavier than a Hermes CLI/skill; likely overkill for routine repo analysis.
- Requires model and embedding credentials or local Ollama setup; not a zero-cost deterministic tool.
- Generated docs can become plausible-looking sludge unless there is a review/curation gate.
- No root `SECURITY.md` found in the inspected metadata; private repo/token support deserves caution.

## Integration ideas

- Distill a Hermes workflow: repo metadata + selected docs/code → generated outline/diagrams → human/agent review → curated repo note, not raw generated wiki commits.
- Compare generated DeepWiki-style output against existing `wiki/intel/github-repos/repos/*` notes for one repo.
- Use its diagram/wikification UX as inspiration for future GBrain repo-architecture pages.

## Alternatives / related repos

- [Graphify-Labs/graphify](Graphify-Labs--graphify.md) — queryable graph/report sidecar rather than generated wiki app.
- [Egonex-AI/Understand-Anything](Egonex-AI--Understand-Anything.md) — interactive knowledge graph and guided codebase tours.
- [VectifyAI/PageIndex](VectifyAI--PageIndex.md) — reasoning/tree-index retrieval for long documents.
- [garrytan/gbrain](garrytan--gbrain.md) — current canonical index/query layer.

## Review candidates and context

- Candidate: a bounded codebase-understanding bakeoff across the DeepWiki/Graphify/Understand-Anything cluster.
