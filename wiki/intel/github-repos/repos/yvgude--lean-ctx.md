---
title: yvgude/lean-ctx
type: repo-intel
source: https://github.com/yvgude/lean-ctx
category: context-engineering
status: deep-analyzed
usefulness_score: 88
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: Apache-2.0
---

# yvgude/lean-ctx

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `88/100` — Strongest context-budget/runtime candidate in this batch: local-first MCP/context layer with compression, routing, memory, verification, and explicit Codex/Claude/Copilot support.
- **Recommendation:** `adopt-now`.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Sandbox LeanCTX on one copied non-sensitive coding repo and measure token savings, answer quality, and whether its memory/routing layer fights Hermes tool discipline.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 23/25 | Directly maps to Hermes/GBrain boundaries between agent context, retrieval, and canonical knowledge. |
| Leverage | 23/25 | Can save time or sharpen agent work if bounded. |
| Reuse readiness | 17/20 | Evidence from README/root files/package/license. |
| Maturity/trust | 13/15 | Based on activity, docs, tests/security/license surface. |
| Differentiation | 12/15 | Distinctive pattern/tool relative to Hermes/GBrain/Obsidian. |

## Verdict

LeanCTX is worth a bounded sandbox because it attacks a real pain point for long-running agent work: agents keep rereading files, wasting tokens, and losing useful session state. The catch is exactly the same reason it is powerful: it wants to sit between agent and context as a broad MCP/context layer. Do not make it global until it proves quality gains without becoming a second memory/control plane.

## Reference-stack relevance

- Fits the current push toward better long-running Hermes/Codex work: less context waste, better retrieval, safer memory boundaries, and higher-quality repo/document ingestion.
- The key decision boundary is whether the repo is a **bounded sidecar** or a **new owner of memory/context**. Sidecars can be sandboxed; parallel truth stores should be pattern sources until they beat Hermes/GBrain/session_search.
- Evidence from this batch should feed concrete improvements to SStack, GBrain, Wikic, and repo-intelligence workflows rather than spawning another ungoverned tool layer.

## What it is

LeanCTX — the Context OS for AI development. One local binary that compresses, remembers, routes, and verifies every token between your code and the model. 63 MCP tools, 10 read modes, up to 99% token savings. Works with Cursor, Claude Code, Copilot, Windsurf, Codex, Gemini.

## Evidence checked

- GitHub metadata: stars `2390`, forks `246`, pushed `2026-06-03T09:39:54Z`, archived `False`.
- Topics: ai, cursor, llm, mcp, rust, token-optimization, agentic-coding, claude-code, copilot, developer-tools, ai-coding, context-engineering, gemini-cli, mcp-server, reduce-token-costs, context-layer.
- Upstream evidence: https://github.com/yvgude/lean-ctx; the following fetched files were inspected at review time.
- Files fetched: README.md, LICENSE, SECURITY.md, root-contents.json, recent-commits.json.

## Strengths

- Local-first Apache-licensed context layer with active commits on review day.
- README claims 63 MCP tools, multiple read modes, compression, routing, memory, and verification across Claude Code/Codex/Copilot/Cursor-style agents.
- Has unusually rich project docs at root: `ARCHITECTURE.md`, `BENCHMARKS.md`, `CONTRACTS.md`, `LEANCTX_FEATURE_CATALOG.md`, `SECURITY.md`, and `VISION.md`.

## Risks / caveats

- Large surface area: context compression, memory, shell output handling, MCP tools, and routing all affect agent behavior.
- Token-savings claims need representative answer-quality checks, not just README benchmarks.
- Should not own canonical memory beside Hermes memory, `session_search`, GBrain, and the vault.

## Integration ideas

- Treat as part of the **context-memory-brain** decision surface, not as an automatic install.
- If sandboxed, use copied/non-sensitive data first and record whether it improves quality/time/cost versus the existing Hermes/GBrain/Obsidian path.
- Extract reusable patterns into existing execution/knowledge owners, SStack skills, or Wikic/GBrain design notes only after a bounded test proves the gap.

## Alternatives / related repos

- [Context / memory / brain tools comparison](../comparisons/context-memory-brain-tools.md)
- [oraios/serena](oraios--serena.md)
- [Graphify-Labs/graphify](Graphify-Labs--graphify.md)
- [kytmanov/obsidian-llm-wiki-local](kytmanov--obsidian-llm-wiki-local.md)
- [garrytan/gbrain](garrytan--gbrain.md)

## Review guidance

- Candidates remain non-binding evaluation guidance.
