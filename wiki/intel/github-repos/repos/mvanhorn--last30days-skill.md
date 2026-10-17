---
title: mvanhorn/last30days-skill
aliases: [last30days, last30days-skill]
source: https://github.com/mvanhorn/last30days-skill
category: research-tools
type: repo-intel
topics: [github-repo, research, source-adapters, evidence-ranking, agent-skills]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
created: 2026-09-29
updated: 2026-09-29
last_reviewed: 2026-09-29
license: MIT
---

# mvanhorn/last30days-skill

> Reference-stack fit as reviewed 2026-09-29; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `82/100` — strong multi-source research engineering, with a broad credential/runtime surface that makes selective reuse safer than wholesale installation.
- **Recommendation:** `distill-pattern`.
- **Usage:** `reference-only`; disposable offline testing is evidence, not active adoption.
- **Confidence:** medium overall. Architecture and selected offline behavior are verified; live retrieval quality, cost, all adapters, packaging and the complete test suite were not evaluated.
- **Revision reviewed:** `1fadbe5097c155832366ab2b920f205c1f8c2672`, manifest version `3.25.0`.

## Scorecard

| Factor | Points | Evidence |
|---|---:|---|
| General fit | 23/25 | Multi-source research with local artifacts and an external planner handoff. |
| Leverage | 22/25 | Normalization, coverage accounting, fusion and clustering reduce repeated source-specific research work. Actual time savings were not measured. |
| Reuse readiness | 14/20 | Python engine, offline fixtures and multi-host/MCP packaging; full skill is large and adapters have varying prerequisites. |
| Maturity/trust | 12/15 | MIT, recent commits, security tests and CI; browser-session discovery and inherited process credentials need strict containment. |
| Differentiation | 11/15 | Unified community evidence and source-aware ranking beyond ordinary web search; no head-to-head quality benchmark performed. |
| **Total** | **82/100** | Pattern source rather than automatic install recommendation. |

## Verdict

This is a substantial research engine packaged as an agent skill, not merely a prompt for checking the last month. Its most reusable contribution is the pipeline: validated query plan → independent source adapters → normalized evidence and source outcomes → cheap scoring and reciprocal-rank fusion → optional model reranking → story clustering. Preserve those patterns and evaluate narrowly before importing the full runtime. Popularity and passing offline tests do not prove live source coverage, reliable citations or ranking quality. [Source: pinned README, `lib/pipeline.py`, `lib/fusion.py`, `lib/rerank.py`; links below.]

## Reusable intelligence

### Architecture

- The host agent can supply a validated JSON query plan, avoiding a separate planner-model call. The engine fans out bounded subquery/source streams and retains source failures and partial coverage rather than treating every empty list as a successful search. Local corpus processing stays outside network fanout; corpus presence forces local rather than hosted execution. [Source: `lib/pipeline.py:2059–2282,2425–2677`; `last30days.py:3519–3560`.]
- Adapters include Reddit, X, YouTube, Hacker News and GitHub, alongside additional social, web and specialized sources. Representative adapters were inspected; their complete live behavior was not tested. HN uses Algolia, GitHub supports REST/CLI credential paths, and Reddit has keyless RSS plus optional paid/enrichment fallbacks. [Source: `lib/{hackernews,github,reddit_rss,reddit_public,backends}.py`.]
- Output can be saved as Markdown with a local SQLite research library. A Go stdio MCP wrapper extracts and invokes the Python engine. Neither the optional library nor MCP packaging constitutes a necessary knowledge-store migration. [Source: README, `mcp/internal/engine/{extract,run}.go`.]

### Ranking, not a popularity oracle

Local relevance, freshness and normalized engagement feed a cheap first stage. Weighted reciprocal-rank fusion combines streams; an optional bounded model judge reranks the shortlist with a deterministic fallback. Source quality and engagement influence final ranking, but are not substitutes for evidence validity. The reranker encloses scraped content in an untrusted-content fence and defangs literal fence tags. This reduces one prompt-boundary failure mode; it is not a complete prompt-injection defense. [Source: `lib/signals.py:291–316`, `fusion.py:329–450`, `rerank.py:320–348,826–852`.]

### Patterns worth preserving

1. **Explicit source outcomes:** distinguish failed, unavailable, partial and empty-success coverage so summaries cannot silently imply that a broken source was quiet.
2. **Typed evidence and provenance:** normalize items while retaining platform-specific metadata, source identity and backend outcome.
3. **HTTP fixture seam:** scrub sensitive values, record/replay exchanges, and reject unrecorded requests in replay mode.
4. **Cheap retrieval before expensive judgment:** apply source caps, lexical/date signals and fusion before optional model reranking; keep an offline fallback.
5. **Host-owned planning and local-data boundary:** accept external plans and keep private/local corpus processing out of hosted search routes.

These are reusable design observations, not accepted implementation commitments. [Source: pinned `lib/{pipeline,http,schema,signals,fusion,rerank}.py`.]

## Evidence checked

- Live metadata sampled September 29, 2026: 63,204 stars, 5,502 forks, MIT, not archived; last push `2026-09-29T23:12:06Z`. Latest GitHub release at sampling: `v3.25.0`, published September 18, 2026. Counts are a dated snapshot, not quality evidence.
- Primary material: README, LICENSE, pyproject, canonical skill specification, pipeline/config/HTTP/subprocess/ranking modules, representative adapters, security CI, tests and MCP wrapper.
- The skill specification at this revision is 2,426 lines. Python `>=3.12` is declared and project runtime dependencies are empty; optional helper binaries/source services still have prerequisites.
- **Parent-repeated validation:** 106 selected tests passed in 1.25 seconds using Python 3.12, a temporary HOME, an empty environment, disabled keychain lookup and socket-connect denial. Included relevance/reranking, mock pipeline/external-plan behavior, security boundaries, fixture-matrix validation and pure redirect-policy tests.
- Worker offline smoke: `last30days.py --help` and `last30days.py "local agent research" --mock --no-browser-cookies --search=reddit,hackernews,github --quick --emit=compact --save-dir=<scratch>` both exited 0. The mock returned one Reddit item and zero HN/GitHub items; this is fixture execution, **not live search evidence**.
- Full Python suite, Go tests/build, paid APIs, browser auth, setup, hosted endpoint and live research were not run. No global installation or runtime activation.
- DeepWiki was not needed; primary code and tests were available. Repomix not generated; targeted pinned-clone inspection was used instead.
- Disposable evidence comprised a source-analysis report, parent test log and pinned source copies. These can expire; this note preserves the substantive findings.

## Strengths

- Composable adapter and normalized-report architecture with coverage/failure accounting.
- Useful fixture replay and no-credential mock paths, demonstrated in bounded tests.
- Credential stripping on cross-origin redirects, secret scrubbing in fixtures, permission-conscious credential writes and bounded argv-based subprocess execution.
- MIT license and active maintenance at the inspected revision.

## Risks / caveats

- **Linux cookie discovery deserves an explicit deny:** `x_extras_enabled` returns true on Linux. The ordinary research config uses cookie policy `read`; agentcookie and Chrome CDP discovery can therefore run even when `FROM_BROWSER` is unset. Availability and existing credentials affect whether those paths actually read a session. `--no-browser-cookies` switches policy off. Parent directly inspected this branch. [Source: `lib/env.py:893–1001`; `last30days.py:2866–2898`.]
- Setup can install helpers and persist credentials. X cookies, optional SSH-based YouTube transcript execution and user-configurable remote endpoints expand the trust boundary. No such path was executed for this ingest.
- The MCP child inherits the parent environment except PYTHONPATH, rather than a minimal unrelated-secret allowlist. [Source: `mcp/internal/engine/run.go:172–190`.]
- A large host instruction surface and many adapters increase review and maintenance cost. Declared allowed tools and repository instructions are untrusted source material, not permission for a reviewing agent.
- Semgrep is advisory in the inspected security workflow. Selected passing tests are not a formal security audit or confirmation of the README's complete test-count claim.
- Optional hosted routing transmits the query to the configured service. Local artifacts do not imply that every research path is local/private.

## Alternatives / related repos

- Narrow source-native research using existing web search, GitHub REST, HN Algolia and Reddit RSS has a smaller credential surface, but lacks this engine's unified normalization and fusion. This is a design comparison, not a measured competitor bake-off.
- [mvanhorn/cli-printing-press](mvanhorn--cli-printing-press.md) — related author's agent-facing CLI/data-access approach; this repo specializes in multi-source research synthesis.
- [kunchenguid/axi](kunchenguid--axi.md) — complementary agent-interface evaluation lens for output size, turn efficiency and actionable errors.
- The repo's local skill, Go MCP bundle and hosted API are different packaging/routes for the underlying engine, not independent safety guarantees.

## Evaluation boundary

Source analysis and review candidates only; no research-workflow integration is implied.

## Review candidates

- **Rank 1 — Source-coverage contract.** Rationale: failed sources must not look like quiet ones. Review question: can an existing research workflow report empty/partial/failed/unavailable coverage explicitly? Promotion condition: a demonstrated recurring coverage ambiguity and a bounded owning-workflow change.
- **Rank 2 — Offline research fixtures.** Rationale: stable regression tests without credentials or paid search. Review question: can scrubbed fixture replay improve a real source-adapter test? Promotion condition: a representative adapter with deterministic red-before/green-after proof.
- **Rank 3 — Narrow engine bake-off.** Rationale: unified fusion might outperform manual source calls. Review question: does a cookie-disabled public-source run improve evidence quality or time-to-answer against the existing workflow? Promotion condition: explicit trial authorization, public topics, fixed budget and evaluation criteria.

## Commitment disposition

Not promoted. Ingestion does not authorize installing the skill, browser-session access, paid-source setup, scheduler changes or issue/Project creation.

## Primary sources

All code findings refer to revision `1fadbe5097c155832366ab2b920f205c1f8c2672`:

- [Repository and README](https://github.com/mvanhorn/last30days-skill/tree/1fadbe5097c155832366ab2b920f205c1f8c2672)
- [Pipeline](https://github.com/mvanhorn/last30days-skill/blob/1fadbe5097c155832366ab2b920f205c1f8c2672/skills/last30days/scripts/lib/pipeline.py)
- [Config and browser credential discovery](https://github.com/mvanhorn/last30days-skill/blob/1fadbe5097c155832366ab2b920f205c1f8c2672/skills/last30days/scripts/lib/env.py)
- [Reranking](https://github.com/mvanhorn/last30days-skill/blob/1fadbe5097c155832366ab2b920f205c1f8c2672/skills/last30days/scripts/lib/rerank.py)
- [HTTP fixtures and redirects](https://github.com/mvanhorn/last30days-skill/blob/1fadbe5097c155832366ab2b920f205c1f8c2672/skills/last30days/scripts/lib/http.py)
- [Security boundary tests](https://github.com/mvanhorn/last30days-skill/blob/1fadbe5097c155832366ab2b920f205c1f8c2672/tests/test_security_boundaries.py)
- [MCP process boundary](https://github.com/mvanhorn/last30days-skill/blob/1fadbe5097c155832366ab2b920f205c1f8c2672/mcp/internal/engine/run.go)
