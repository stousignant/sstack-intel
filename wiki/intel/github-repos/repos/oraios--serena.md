---
title: oraios/serena
type: repo-intel
aliases:
  - serena
  - GitHub repo: oraios/serena
source: https://github.com/oraios/serena
category: code-intelligence
topics: [github-repo, mcp, code-intelligence, coding-agents, semantic-editing]
status: deep-analyzed
usefulness_score: 92
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-27
license: MIT
---

# oraios/serena

> Reference-stack evaluation as reviewed 2026-05-27; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `92/100` — strongest immediate candidate in this sprint because it gives existing coding agents IDE-like semantic retrieval/editing through MCP.
- **Recommendation:** `adopt-now` for a **bounded sandbox**, then decide whether to wire into Hermes/Codex defaults.
- **Usage observed 2026-05-27:** `not-used`.
- **Review candidate:** install with `uv tool install -p 3.13 serena-agent`, run `serena init`, and test on a copied repo or non-critical local checkout before enabling broadly.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | MCP-native; explicitly supports Claude Code, Codex, OpenCode, VSCode/Cursor/JetBrains; maps to Hermes coding workflows. |
| Leverage | 24/25 | Could reduce fragile grep/read/edit loops and improve agent performance on large repos. |
| Reuse readiness | 18/20 | PyPI/uv install, docs, CLI, MCP server, project workflow; needs setup discipline. |
| Maturity/trust | 13/15 | MIT, active release `v1.5.3` on 2026-05-26, tests/lint/type-check tasks and pinned security deps visible in `pyproject.toml`. |
| Differentiation | 13/15 | Broader and more agent-facing than plain code graph search; semantic editing/refactoring is the standout. |

## Verdict

Serena is the most actionable repo in the context/memory/code-intelligence cluster. It should not replace GBrain/code graph tools; it should be evaluated as a **coding-agent MCP sidecar** that provides symbol search, references, and safer semantic edits. The catch: it is powerful enough to deserve sandboxing first, because broad file/shell/read tools overlap with Hermes' existing tool layer and should be configured narrowly.

## Reference-stack relevance

- Directly improves Hermes/Codex/Claude-style coding sessions by giving agents structured code navigation instead of brute-force file reads.
- Fits the reuse-first principle: adopt an existing MCP toolkit before building a bespoke code-intelligence bridge.
- Could become a default helper for Hermes Agent, GBrain, and second-brain repos if the sandbox proves it saves tokens and reduces edit mistakes.

## What it is

Serena is an MCP toolkit for coding agents. It exposes IDE-like capabilities — symbol lookup, references, diagnostics, symbolic editing, and optional refactoring/debugging — through either language servers or a paid JetBrains plugin backend.

## Evidence checked

- Live GitHub metadata via `gh repo view` on 2026-05-27: 24,688 stars, 1,650 forks, MIT, primary language Python, latest release `v1.5.3` published 2026-05-26, pushed 2026-05-27.
- README sections inspected: “How Serena Works”, “Programming Language Support”, “Features”, “Quick Start”.
- `pyproject.toml` inspected: package `serena-agent`, Python `>=3.11,<3.15`, CLI entrypoints `serena` / `serena-agent`, dev tasks for pytest, ruff, mypy, docs, and pinned transitive deps for security.
- Local bounded smoke test: `uvx --from serena-agent serena --help` with an isolated disposable cache succeeded and showed commands for config, context, init, project, setup, MCP server, tools, memories, and prompts.

## Strengths

- MCP-native and already framed for coding agents rather than human-only IDE use.
- Uses language servers for free/open semantic analysis across 40+ languages; JetBrains backend is optional and paid.
- Provides retrieval and symbolic editing, not just search: `find symbol`, `find referencing symbols`, `replace symbol body`, insert around symbols, diagnostics, and config/mode systems.
- Includes a memory layer, but it can be disabled if Hermes/GBrain remains the canonical memory surface.
- Setup is simple with `uv`, and the smoke test confirms the package starts locally.

## Risks / caveats

- Powerful tool overlap: file read/search/shell tools should likely be disabled or constrained when used inside Hermes/Codex to avoid duplicate authority surfaces.
- Some higher-end capabilities depend on the paid JetBrains plugin; free LSP backend is enough for first sandbox but not equivalent.
- Needs per-project onboarding/config to avoid agents editing the wrong workspace.
- Security posture looks better than average from pinned CVE-related transitive deps, but no `SECURITY.md` was surfaced in the GitHub community profile.

## Integration ideas

- Add Serena as an optional MCP server for coding sessions on copied code, agent-runtime, and Markdown-vault repositories only after a copied-repo sandbox.
- Create a Hermes skill: “use Serena for symbol/refactoring questions before raw file scanning; use native Hermes file tools for actual writes unless semantic edit is clearly safer.”
- Compare Serena against GBrain's `code_def`, `code_callers`, `code_flow`, and `code_refs`; likely split: GBrain for indexed repo intelligence, Serena for live project-aware LSP semantics.

## Alternatives / related repos

- [CodeGraphContext/CodeGraphContext](CodeGraphContext--CodeGraphContext.md) — graph database + MCP/CLI code analysis.
- [upstash/context7](upstash--context7.md) and [andrewyng/context-hub](andrewyng--context-hub.md) — docs/context retrieval rather than code structure.

## Review guidance

- A bounded semantic-retrieval/editing evaluation remains a candidate, not an executable commitment.
