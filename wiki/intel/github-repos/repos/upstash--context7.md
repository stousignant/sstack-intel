---
title: upstash/context7
type: repo-intel
aliases:
  - context7
  - GitHub repo: upstash/context7
source: https://github.com/upstash/context7
category: documentation-context
topics: [github-repo, mcp, docs, coding-agents, context]
status: deep-analyzed
usefulness_score: 86
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-05-27
license: MIT
---

# upstash/context7

> Reference-stack evaluation as reviewed 2026-05-27; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `86/100` — high immediate utility for reducing hallucinated library/API usage, but not a local-first knowledge base.
- **Recommendation:** `adopt-now` as an **on-demand docs lookup tool**, not as canonical memory.
- **Usage observed 2026-05-27:** `not-used`.
- **Review candidate:** configure for a single coding client or use `npx ctx7 docs/library` ad hoc; avoid writing “always use Context7” into global Hermes instructions until behavior is observed.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | Useful for coding agents and MCP; less aligned with local-first due hosted docs service. |
| Leverage | 23/25 | Strong time saver when working with fast-moving APIs. |
| Reuse readiness | 19/20 | Simple `npx ctx7 setup`, MCP server, CLI, SDK packages, huge adoption. |
| Maturity/trust | 13/15 | MIT, very active, large community; repository health profile only 50% and backend/parser/crawler are private. |
| Differentiation | 10/15 | Best-known docs lookup surface, but hosted and overlaps with Context Hub/official docs. |

## Verdict

Context7 is worth using tactically. The sharp boundary: it solves **up-to-date external docs in prompts**, not private or project-specific memory. Use it when coding against libraries; do not let it become another always-on source of unreviewed instructions in Hermes' global prompt.

## Reference-stack relevance

- Fastest path to fewer stale-API mistakes in Hermes/GBrain/second-brain coding work.
- Already supports MCP and CLI modes, so it can be used without a custom integration project.
- Helps Hermes reuse current docs instead of guessing from model training data.

## What it is

Context7 is a documentation retrieval platform with CLI, MCP server, TypeScript SDK, and agent-skill integrations. It resolves a library ID and injects current, version-specific docs/examples into an agent's context.

## Evidence checked

- Live GitHub metadata via `gh repo view` on 2026-05-27: 56,236 stars, 2,662 forks, MIT, TypeScript, pushed 2026-05-26, latest release tag `@upstash/context7-pi@0.1.0` on 2026-05-25.
- README inspected: install, OAuth/API-key note, CLI/MCP modes, library ID/version tips, available tools, packages, disclaimer.
- `package.json` inspected: monorepo with build/test/typecheck/lint scripts and packages for MCP, SDK, Vercel AI SDK tools, CLI.
- Local bounded smoke test: `npx --yes ctx7 --help` with an isolated disposable npm cache succeeded and showed `setup`, `remove`, `library`, `docs`, `skills`, login/logout commands. NPM emitted an engine warning for `mute-stream` because local Node was `v24.14.1` and a dependency wanted `^24.15.0` or newer.

## Strengths

- Very low-friction docs retrieval; can be used ad hoc via `npx ctx7 library` / `npx ctx7 docs`.
- MCP mode and CLI+skill mode cover most coding-agent surfaces.
- Supports explicit library IDs and version hints, which reduces matching ambiguity.
- Large adoption signal and active release cadence.

## Risks / caveats

- README explicitly says community-contributed docs are not guaranteed accurate, complete, or secure.
- Supporting API backend, parsing engine, and crawling engine are private; the repo is not the whole system.
- OAuth/API-key flow and hosted service reduce local-first purity.
- Global “always use Context7” rules can add latency/noise and could import untrusted documentation into prompts.

## Integration ideas

- Add a Hermes skill/rule that says: use Context7 only for external library/API docs, never for repo-local or personal-memory truth.
- Prefer exact `/owner/project` library IDs when known.
- Consider an allowlist for common coding targets rather than broad automatic invocation.

## Alternatives / related repos

- [andrewyng/context-hub](andrewyng--context-hub.md) — open markdown content + local annotations, smaller ecosystem.
- [oraios/serena](oraios--serena.md) — code structure/context, not library docs.

## Review guidance

- Tactical single-client setup remains a candidate; no installation or commitment is established by this review.
