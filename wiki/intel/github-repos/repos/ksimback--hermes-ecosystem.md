---
title: ksimback/hermes-ecosystem
type: repo-intel
aliases:
  - Hermes Atlas
  - hermesatlas.com
  - GitHub repo: ksimback/hermes-ecosystem
source: https://github.com/ksimback/hermes-ecosystem
category: hermes-extension
topics: [github-repo, hermes, ecosystem-map, discovery, skills, directory]
status: triaged
usefulness_score: 74
recommendation: reference-only
usage: reference-only
score_confidence: high
last_reviewed: 2026-08-31
license: MIT (site code per README; repo licenseInfo null — content CC BY 4.0 for research)
---

# ksimback/hermes-ecosystem

> Reference-stack fit as reviewed 2026-08-31; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `74/100` — a curated, security-reviewed discovery surface for exactly the reference stack's runtime (Hermes Agent); not a tool to install, but the best single catalog for sourcing ecosystem candidates before individual repo ingests.
- **Recommendation:** `reference-only` — use as a discovery/shortlist source feeding `sstack-github-ingest` triage, not as an installed dependency.
- **Usage observed 2026-08-31:** `reference-only`. Consulted as an ecosystem map; nothing installed.
- **Confidence:** `high`
- **Review candidate:** Mine its category tables when the operator asks "what exists for X in the Hermes ecosystem"; verify any candidate against live GitHub metadata before trusting star counts (repo's own star data is API-cached and its ECOSYSTEM.md snapshot is dated 2026-04-11 / Hermes 0.8.0).

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Maps exactly the reference stack's runtime, but is itself a static site + JSON catalog, not an integration point. |
| Leverage | 15/25 | Saves discovery time for skill/plugin/orchestration candidates; the actionable value lands in downstream repo ingests, not here. |
| Reuse readiness | 16/20 | `data/repos.json` is a single source of truth (machine-readable); ECOSYSTEM.md is a clean Markdown mirror; live site at hermesatlas.com. |
| Maturity/trust | 13/15 | 1,245 stars / 104 forks; created 2026-04-08; pushed 2026-08-31 (active); security review included (5 WARN repos, none malicious). License field on GitHub is unset despite README claim. |
| Differentiation | 10/15 | Community-curated with quality filters and RAG chatbot; overlaps with `awesome-hermes-agent` but with live star data and maturity tiers. |
| **Total** | **74/100** | Strong reference catalog; no install case. |

## Verdict

Keep Hermes Atlas as the first-stop discovery surface for Hermes-ecosystem candidates, then run each interesting entry through normal `sstack-github-ingest` triage with live metadata — do not trust its cached star counts or 2026-04-11 snapshot for verdicts. The `repos/security-review.md` WARN list (swarmclaw, hermes-CCC, vessel-browser, gladiator, hermes-skins) is directly useful to pre-flag risky installs. This is a directory, not a tool: no repomix, no smoke test, no adoption path.

## Reference-stack relevance

- It is a quality-filtered, security-reviewed map of the exact runtime covered by the reference lens — the fastest way to discover Hermes-native skills, plugins, memory engines, and orchestration layers worth ingesting.
- `data/repos.json` (240+ repos, 12 categories) is machine-readable: could seed batch triage or star-list reconciliation without manual GitHub searching.
- Its maturity tiers (Production/Beta/Experimental) and security WARN list map cleanly onto SStack's supply-chain review gates for third-party skillpacks.
- Candidate pool relevant to the reference stack's active concerns: orchestration (mission-control, oh-my-hermes), memory (hindsight, honcho-self-hosted, ClawMem), token tracking (tokscale), and skill factories.

## What it is

Community-curated catalog ("Hermes Atlas") of Hermes Agent ecosystem tools — 80+ quality-filtered repos in the live site / 240+ in the current description — with live GitHub star counts (GitHub GraphQL → Redis cache), sparklines, an "Ask the Atlas" RAG chatbot (hybrid BM25 + cosine retrieval over 27 research files, OpenRouter with fallback chain), and a Markdown mirror (`ECOSYSTEM.md`). Vanilla HTML/CSS/JS frontend on Vercel, two Python-free serverless functions, MIT site code, CC BY 4.0 research content. Built by @ksimback; not affiliated with Nous Research.

## Evidence checked

- GitHub README/docs: https://github.com/ksimback/hermes-ecosystem (fetched 2026-08-31)
- GitHub metadata: 1,245 stars / 104 forks, created 2026-04-08, pushed 2026-08-31, no topics beyond hermes-agent ecosystem tags, `licenseInfo: null`
- ECOSYSTEM.md snapshot (downloaded as a disposable upstream snapshot): 12 categories, 292 lines, dated 2026-04-11 / Hermes 0.8.0 — note internal inconsistency (README says 80+ repos; current repo description says 240+)
- Security notes: 5 WARN repos flagged; claims full review of 25+ star repos with no malicious findings (README claim, not independently verified)
- repomix pack: not generated (directory site, no reason)
- Local smoke test: not applicable (static site)

## Strengths

- Current and active: pushed the same day as review; live star counts cached in Redis with 30-day history for sparklines.
- Security posture is unusually good for a directory: explicit review pass, published WARN list, and general curl-pipe-bash warnings.
- Machine-readable single source of truth (`data/repos.json`) plus a clean Markdown mirror.
- Filtering criteria are stated and sensible (Hermes-specific, post-2025-07, quality bar, security review).

## Risks / caveats

- Snapshot staleness: ECOSYSTEM.md dated 2026-04-11 while the repo actively pushes — star counts and entry set drift between the Markdown mirror, live site, and repos.json.
- GitHub `licenseInfo` is null despite README claiming MIT for site code; verify licensing before any code reuse.
- Third-party single-maintainer community project; not affiliated with Nous Research despite being ecosystem-canonical in practice.
- Maturity labels (Production/Beta) are curator judgment, not verification — several "—" star entries are effectively unvetted.
- Repo count inconsistency (80+ vs 240+) suggests the README lags the dataset.

## Integration ideas

- Use `repos.json` as a seed list for batched `sstack-github-ingest` triage of Hermes-ecosystem categories the reference lens cares about (orchestration, memory, skill factories).
- Cross-check its WARN list against any skillpack/plugin before sandbox install; feed flagged repos into the standard supply-chain review recipe.
- Do NOT mirror it into the vault — link it as a discovery source and record only ingested candidates as individual repo notes.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — the runtime this map catalogs.
- [NousResearch/hermes-agent-self-evolution](nousresearch--hermes-agent-self-evolution.md) — official self-improvement layer, itself listed on the Atlas.
- [witt3rd/oh-my-hermes](https://github.com/witt3rd/oh-my-hermes) — Atlas-listed orchestration pack; its upstream source is a discovery reference, not adoption proof.
- 0xNyk/awesome-hermes-agent — the complementary curated list the Atlas points contributions toward.
