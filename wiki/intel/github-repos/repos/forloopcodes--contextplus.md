---
title: forloopcodes/contextplus
type: repo-intel
aliases:
  - contextplus
  - GitHub repo: forloopcodes/contextplus
source: https://github.com/forloopcodes/contextplus
category: code-context
topics: [github-repo, repo-intelligence, agent-memory, context-management]
status: deep-analyzed
usefulness_score: 82
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# forloopcodes/contextplus

> Reference-stack fit as reviewed 2026-05-30; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `82/100` — Small MIT MCP sidecar with concrete code-context tools, local Ollama embeddings by default, AST/file-skeleton/feature-hub/RAG graph semantics; worth a bounded sandbox against GBrain/Serena/Graphify.
- **Recommendation:** `adopt-now`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Sandbox on a copied/non-sensitive repo with no hosted embeddings; compare 5 code-navigation questions against GBrain/Serena/manual workflow.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Relevant to Hermes/GBrain/context/memory workflows, with varying risk of duplicate canonical stores. |
| Leverage | 22/25 | Could improve recall, context budget, code navigation, or session continuity if bounded correctly. |
| Reuse readiness | 17/20 | README/manifests provide install paths; safe adoption still requires sandboxing and boundary checks. |
| Maturity/trust | 10/15 | Live metadata: 1911 stars, 160 forks, pushed 2026-05-02T06:48:20Z, license MIT. |
| Differentiation | 10/15 | Differentiates mainly by evals, hooks, UX, or low-token code/context tools versus current Hermes/GBrain stack. |

## Verdict

Small MIT MCP sidecar with concrete code-context tools, local Ollama embeddings by default, AST/file-skeleton/feature-hub/RAG graph semantics; worth a bounded sandbox against GBrain/Serena/Graphify. The default stance is **one canonical memory/index layer**: Hermes memory + session search + GBrain + the second-brain vault. These repos are valuable only when they improve a specific boundary — recall quality, context-budget observability, code-navigation speed, or team/shared-memory UX — without creating a second truth store.

## Reference-stack relevance

- The reference stack already has memory and search; the leverage is not “more memory,” it is **better evaluated recall with clean ownership boundaries**.
- Agent hooks and MCP context tools can save tokens/time, but they also increase ambient capture and secret-leak risk.
- Good patterns here can make Hermes more self-improving: session capture, compaction, retrieval evals, purge/logout controls, and low-token code context.

## What it is

Context+ is a TypeScript MCP server for large codebases, combining Tree-sitter ASTs, RAG, spectral clustering, and Obsidian-style feature hubs into code-navigation tools.

## Live metadata checked

- Source: <https://github.com/forloopcodes/contextplus>
- Description: Semantic Intelligence for Large-Scale Engineering. Context+ is an MCP server designed for developers who demand 99% accuracy. By combining RAG, Tree-sitter AST, Spectral Clustering, and Obsidian-style linking, Context+ turns a massive codebase into a searchable, hierarchical feature graph.
- Stars / forks: 1911 / 160
- Primary language: TypeScript
- License: MIT
- Latest release: none observed
- Last pushed: 2026-05-02T06:48:20Z
- Topics: mcp-server

## Evidence checked

- GitHub metadata via `gh repo view forloopcodes/contextplus` on 2026-05-30.
- README from [upstream README](https://github.com/forloopcodes/contextplus/blob/HEAD/README.md).
- License, package manifest, security policy, and top-level contents where present under temporary upstream inspection material.

## Strengths

- Concrete MCP tools: `get_context_tree`, `get_file_skeleton`, feature hubs, memory graph upsert/search, and interlinked context.
- Low-friction `npx`/`bunx` setup and MIT license.
- Local Ollama embedding provider is the default; other providers are optional.

## Risks / caveats

- “99% accuracy” is a README claim and needs a real code-navigation bakeoff.
- Creates another code/memory graph; must not become a competing canonical index unless it clearly wins.
- Security/auth posture is less developed than bigger tools; inspect code before broad MCP enablement.

## Integration ideas

- Feature hubs as Obsidian-style wikilink maps could pair well with repo-intelligence and codebase-understanding notes.
- File skeleton and context tree tools are exactly the kind of low-token code navigation Hermes lacks natively.

## Alternatives / related repos

- [thedotmack/claude-mem](thedotmack--claude-mem.md)
- [rohitg00/agentmemory](rohitg00--agentmemory.md)
- [supermemoryai/claude-supermemory](supermemoryai--claude-supermemory.md)
- [forloopcodes/contextplus](forloopcodes--contextplus.md)
- [mksglu/context-mode](mksglu--context-mode.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [oraios/serena](oraios--serena.md)
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md)

## Review candidates and context

- Add Context+ to the codebase-understanding sandbox comparison queue.
- Recommendations are non-binding review candidates; executable work belongs in the established issue tracker.
