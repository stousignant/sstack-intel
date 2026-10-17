---
title: andrewyng/context-hub
type: repo-intel
aliases:
  - context-hub
  - chub
  - GitHub repo: andrewyng/context-hub
source: https://github.com/andrewyng/context-hub
category: documentation-context
topics: [github-repo, docs, agent-skills, annotations, context]
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-27
license: MIT
---

# andrewyng/context-hub

> Opinionated reference-stack evaluation, reviewed 2026-05-27. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `78/100` — excellent pattern for open docs + local annotations, but less immediately useful than Context7 unless registry coverage is strong for the libraries used by the target workflow.
- **Recommendation:** `distill-pattern`; optionally use ad hoc where it has the exact docs needed.
- **Usage observed 2026-05-27:** `not-used`.
- **Review candidate:** steal the local-annotation feedback loop for Hermes skills/docs; do not install as a global dependency yet.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Skill/docs registry plus annotations map well to Hermes skill memory. |
| Leverage | 19/25 | Could reduce repeated API mistakes, but coverage is smaller than Context7. |
| Reuse readiness | 16/20 | NPM package works; docs and skill are simple. |
| Maturity/trust | 12/15 | MIT, active release, good community profile, but young repo and narrower package. |
| Differentiation | 11/15 | Local annotation loop is the standout; otherwise overlaps with Context7/official docs. |

## Verdict

Context Hub is more valuable as a **design pattern** than as a default runtime dependency. The important idea is not “another docs lookup CLI”; it is that agents can attach local annotations to docs and see those notes automatically on future fetches. Hermes already has skills and memory; this pattern could make repeated coding gotchas durable without polluting global memory.

## Reference-stack relevance

- Provides a small, concrete example of self-improving agent documentation loops.
- The local annotation model maps directly to Hermes' “durable learnings should become memories/skills” rule.
- Open markdown registry is inspectable and more local-friendly than opaque hosted docs services.

## What it is

Context Hub (`chub`) is a JavaScript CLI and open markdown registry for LLM-optimized docs/skills. Agents search/fetch docs, annotate gaps locally, and send feedback to doc authors.

## Evidence checked

- Live GitHub metadata via `gh repo view` on 2026-05-27: 13,414 stars, 1,175 forks, MIT, JavaScript, latest release `v0.1.4` on 2026-04-27, pushed 2026-05-24.
- README inspected: quickstart, how it works, commands, self-improving agents, incremental fetch, annotations/feedback, contributing/license.
- `package.json` inspected: monorepo with `cli` workspace.
- NPM metadata checked: `@aisuite/chub` version `0.1.4`, MIT.
- Local bounded smoke test: `npx --yes @aisuite/chub --help` (using a disposable npm cache) succeeded and printed remote help/agent workflow. It did not require installing globally.

## Strengths

- Simple mental model and CLI: `chub search`, `chub get`, `chub annotate`, `chub feedback`.
- Local annotations are the core feature: future agents see prior corrections/workarounds automatically.
- Content is plain markdown with YAML frontmatter and PR-based contribution.
- Lower opacity than Context7 because the content registry is visible in the repo/CDN model.

## Risks / caveats

- Registry coverage and freshness need to be tested against the target workflow's actual libraries before relying on it.
- It is young and not MCP-native in the same way Context7 is.
- Could become yet another docs source if not routed through a clear “external API docs only” policy.

## Integration ideas

- Distill local annotations into a Hermes skill improvement: when an agent learns a library gotcha, save it in a scoped skill/reference file instead of free-floating memory.
- Use `chub` ad hoc for libraries it covers well; compare against Context7 output on one real coding task.
- Consider “docs gotcha cache” inside second-brain or Hermes skills if repeated problems emerge.

## Alternatives / related repos

- [upstash/context7](upstash--context7.md) — more adopted, hosted/MCP-oriented docs retrieval.
- [microsoft/skills](microsoft--skills.md) and [addyosmani/agent-skills](addyosmani--agent-skills.md) — skillpack quality references.

## Review candidates and context

- Non-binding guidance; executable state belongs to the established issue tracker.
