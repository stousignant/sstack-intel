---
title: VectifyAI/PageIndex
type: repo-intel
aliases:
  - PageIndex
  - GitHub repo: VectifyAI/PageIndex
source: https://github.com/VectifyAI/PageIndex
category: retrieval
topics: [github-repo, repo-intelligence, rag, retrieval, tree-search, vectorless-rag]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT
---

# VectifyAI/PageIndex

> Reference-stack evaluation as reviewed 2026-05-28. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — high-value retrieval architecture pattern for long structured documents, but not a near-term replacement for GBrain search/indexing.
- **Recommendation:** `distill-pattern` — study tree-index + reasoning retrieval for long docs; only sandbox after a real retrieval eval shows vector/BM25/chunking failure.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Add PageIndex-style tree retrieval to the retrieval-eval candidate list, especially for PDFs/books/specs where structure matters.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 20/25 | Relevant to second-brain/PDF/book/spec retrieval, less direct for Markdown vault/code intelligence. |
| Leverage | 21/25 | Could improve traceable retrieval for long professional docs if claims hold. |
| Reuse readiness | 15/20 | MIT, self-hosted examples, requirements and runner; still model/API dependent and docs/site-heavy. |
| Maturity/trust | 12/15 | Very active, popular, examples exist; benchmark claims need independent eval. |
| Differentiation | 14/15 | Clear alternative to vector chunking: tree structure + reasoning traversal. |

## Verdict

PageIndex is the most interesting **retrieval architecture** repo in this batch. It should not displace GBrain where Markdown/Git is the canonical knowledge source and GBrain owns hybrid keyword/vector/graph retrieval. PageIndex is worth distilling for a narrower failure class: long, structured documents where section hierarchy and traceable page/section reasoning may outperform similarity search.

## Reference-stack relevance

- Books, PDFs, specs, meeting packets, and long research documents are a recurring second-brain ingestion problem.
- PageIndex's “table of contents tree → reasoning traversal → tight page ranges” pattern could reduce irrelevant vector chunks and improve citation traceability.
- It gives a concrete design alternative for future GBrain retrieval evals: do not argue vector vs. reasoning abstractly; compare on representative workload questions.

## What it is

PageIndex is a vectorless, reasoning-based RAG framework. It builds a hierarchical tree index from a document and uses LLM reasoning to search the tree and retrieve relevant pages/sections, rather than embedding artificial chunks into a vector database. The README also advertises hosted chat/API/MCP paths, but the repo includes self-hosted examples.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 32,269 stars, 2,786 forks, MIT, Python primary language, pushed 2026-05-26.
- README: “Vectorless, Reasoning-based RAG,” no vector DB/chunking, tree structure index, traceable page/section retrieval, PageIndex File System and MCP/API claims.
- Root files: `pageindex/`, `cookbook/`, `examples/`, `run_pageindex.py`, `requirements.txt`, the `.claude` configuration directory.
- `requirements.txt`: `litellm`, PyMuPDF, PyPDF2, dotenv, PyYAML; OpenAI Agents optional for examples.
- `run_pageindex.py`: supports PDF or Markdown input, model overrides, TOC/page/node thresholds, optional summaries/text/node IDs, Markdown thinning.
- `examples/agentic_vectorless_rag_demo.py`: OpenAI Agents SDK demo with tools for document metadata, document structure, and tight page-content ranges.

## Strengths

- Strong conceptual differentiation from vector-only RAG.
- Traceability and structure awareness are directly relevant to high-stakes docs.
- Self-hosted code path exists; not only a SaaS landing page.
- The agent example enforces tight retrieval ranges and answer-from-tool-output discipline.

## Risks / caveats

- Benchmark/accuracy claims should be treated as README claims until reproduced on workload-specific evals.
- More LLM calls and reasoning steps can increase latency/cost vs GBrain hybrid search.
- Hosted API/MCP path may be convenient but should not become canonical storage or retrieval without privacy review.
- It targets long documents more than the everyday Markdown/code graph use case.

## Integration ideas

- Add PageIndex as a retrieval-eval candidate for long PDFs/books/specs after defining 10–20 expected-answer questions.
- Distill its TOC/tree-search strategy into GBrain document ingestion design: preserve section hierarchy and page spans, then reason over structure before fetching chunks.
- Use the agent example's “get structure before content; fetch tight ranges; answer only from tool output” discipline in document QA prompts.

## Alternatives / related repos

- [garrytan/gbrain](garrytan--gbrain.md) — canonical local brain index/search/graph.
- [MemPalace/mempalace](MemPalace--mempalace.md) — memory retrieval benchmark/reference.
- [Gentleman-Programming/engram](Gentleman-Programming--engram.md) — local memory sidecar.
- [AsyncFuncAI/deepwiki-open](AsyncFuncAI--deepwiki-open.md) — repo RAG/wiki app rather than long-document tree retrieval.

## Review candidates and context

- Candidate: a PageIndex-style retrieval eval on long structured documents, with expected answers and page/section citations.
