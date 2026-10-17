---
title: breferrari/obsidian-mind
type: repo-intel
aliases: [obsidian-mind, Obsidian Mind]
source: https://github.com/breferrari/obsidian-mind
category: memory-management
topics: [github-repo, repo-intelligence, agent-memory, obsidian, scoped-recall]
status: deep-analyzed
usefulness_score: 83
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-02
license: MIT
---

# breferrari/obsidian-mind

> Opinionated reference-stack evaluation, reviewed 2026-10-02. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `83/100` — compelling source of scoped, explainable recall, correction semantics, and maintained-knowledge promotion; implementation has explicit limits and direct adoption brings a broad vault/hook operating model.
- **Recommendation:** `distill-pattern`.
- **Usage:** `reference-only`; no installation, runtime activation, or implementation of the patterns is claimed.
- **Confidence:** medium. Pinned source was inspected, including tests and workflow configuration; no repository scripts, dependencies, agent integrations, or local test suite were executed.

## Scorecard

| Factor | Points | Evidence and judgment |
|---|---:|---|
| Stack fit | 22/25 | Markdown-first knowledge, MCP and scoped cross-project context; template and supported agent integrations carry integration cost. |
| Leverage | 22/25 | Applicability filtering, explainability and correction propagation can reduce stale or misplaced guidance; outcome improvement not measured here. |
| Reuse readiness | 15/20 | Concrete modular TypeScript implementation and documented contracts; porting is not plug-and-play and has not been tested. |
| Maturity/trust | 12/15 | MIT, recent release, adoption signal and cross-platform CI configuration; cooperative boundaries and untested live integrations limit confidence. |
| Differentiation | 12/15 | Strong combination of scope-before-ranking, supersession across scope changes and bounded promoted-content resolution. |

## Verdict

Worth studying as a memory-design reference rather than treating it as a ready-made replacement for an established knowledge stack. Its strongest contribution is not a new database: it makes the applicability, correction history, and origin of remembered guidance explicit. Borrow narrowly into an existing execution or retrieval owner; avoid importing the full vault layout, hooks and command framework merely to obtain those semantics. [Sources: README and recall/promoted modules at the pinned revision below.]

## What it is

An opinionated Obsidian vault template with agent instructions, commands, hooks, and an MCP interface. Documentation describes Claude Code, Codex CLI and Gemini CLI integrations, optional QMD retrieval, durable lesson capture, project work records, and reasoning over notes. These documented integrations are not evidence of tested Hermes compatibility. [Source: [pinned README](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/README.md).]

## Metadata and maintenance snapshot

Checked through GitHub API on **2026-10-02**:

- Stars: **4,846**; forks: **544**. These are adoption signals, not proof of quality or a measured growth trend.
- License: **MIT**.
- Last push: **2026-10-02T14:11:24Z**.
- Latest release checked: **v8.5.0**, published **2026-10-02T14:11:27Z**.
- Source revision: [`6302ab2babd931e28620f2af96eaf09a90f414b3`](https://github.com/breferrari/obsidian-mind/commit/6302ab2babd931e28620f2af96eaf09a90f414b3).

Source: GitHub repository, release and commits APIs for `breferrari/obsidian-mind`. Snapshot values will age; no claim that the project is currently trending.

## Reusable intelligence

### 1. Artifact-bound context consultation

**Documented pattern:** before changing named consequential surfaces (storage schema, identifier semantics, public interfaces), consult the written decision record and put the outcome in the pre-implementation artifact. Include supporting decisions, contrary evidence and an explicit empty result. This is more specific than a generic instruction to check context. The README's claims about observed agent compliance are author observations, not independently replicated benchmarks. [Source: [README, decision-consultation contract](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/README.md#L280-L350).]

**Transferable use:** attach a short evidence section to an existing plan or PR when risk warrants it. Avoid a new planning artifact or mandatory ceremony for trivial edits. Distinguish durable lessons (`remember`) from project events and verification records (`record_work`).

### 2. Applicability before relevance

**Code verified:** `isVisibleTo` admits general memories, explicit project matches, or platform-scoped overlap; unmatched memories are withheld. Unknown callers see general memories only. The MCP bridge can semantically reorder the already-visible set rather than broadening it. This is relevance routing, not authenticated tenant isolation. [Sources: [memory-recall.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/memory-recall.ts#L216-L245), [mcp-memory-bridge.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/mcp-memory-bridge.ts).]

**Transferable use:** separate research relevance from applicable operating constraints. A semantically similar lesson from another project is not automatically an instruction for the current task.

### 3. Explain included and withheld context

**Code verified:** `visibilityReason` names matching facets or the reason no facet matches. The separate supersession exclusion identifies a retired entry whose replacement is outside the caller's reach. [Source: [memory-recall.ts, explanation and supersession](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/memory-recall.ts#L247-L302).]

**Transferable use:** diagnostic receipts distinguish absent knowledge, scope mismatch and retired knowledge. Keep them available for debugging rather than adding verbose context receipts to every normal answer. Explanation must itself respect disclosure boundaries.

### 4. Corrections must retire stale guidance across scope changes

**Code verified:** the served-set calculation considers supersession and scope together. When a broad lesson is replaced by a narrower one, readers outside the new scope should not continue receiving the retired broad lesson alone. It also accounts for chains of corrections; unresolved references and cycles have deliberate degradation behavior rather than indiscriminate deletion. [Source: [memory-recall.ts, servedAfterSupersession](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/memory-recall.ts#L275-L360).]

**Transferable use:** a correction needs consumer/restatement checks, not just a rewritten paragraph. Preserve provenance while preventing obsolete guidance from returning as current truth. This does not require keeping duplicate live procedure files when version history is sufficient.

### 5. Promotion resolves to maintained, bounded content

**Code verified:** an anchored `promoted:` reference lets recall serve a corrected section or block from a curated note while retaining the capture's reach record. The implementation reuses the central exposure policy, explicitly handles missing anchors, and bounds content at 40 lines and 8,000 characters. A bare note marker does not serve the whole note. [Source: [memory-promoted.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/memory-promoted.ts#L1-L116).]

**Transferable use:** favor the maintained owner over frozen copies of a discovery. Preserve source provenance without turning promotion into competing canonical versions. Anchors need validation and a visible stale-reference outcome.

## Strengths

- Concrete scope/explanation/correction behavior in modular source, rather than memory claims confined to a README.
- Shared note-exposure resolver checks exposed roots, private markers, excluded filenames and symlink containment. [Source: [mcp-exposure.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/mcp-exposure.ts).]
- Write interface includes validation, dry-run, duplicate suppression and dangling-link reporting; atomic-write code and a cross-process regression test explicitly address concurrent writes. Presence of the test is verified, not its local passing result. [Sources: [mcp-server.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/mcp-server.ts), [atomic-write.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/atomic-write.ts), [concurrency test](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/tests/memory-write.concurrency.test.ts).]
- CI configuration runs tests/typechecking on Ubuntu, macOS and Windows with Node 22/24. [Source: [test.yml](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.github/workflows/test.yml).]

## Risks / caveats

- **Cooperative boundary, not OS containment:** MCP filtering cannot stop an agent with independent filesystem access. The README acknowledges the instruction contract's role; do not treat it as a security sandbox. [Sources: README exposure section; mcp-exposure.ts.]
- **Self-declared general scope:** a general memory naming no project is accepted; origin/provenance and warnings do not establish universal applicability. General plus named projects is narrowed, but the no-project case stands. [Source: [memory-write.ts, narrowScope](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/memory-write.ts#L190-L237).]
- **Caller identity is routing, not authentication:** folder-name defaults can collide; `.om-project` supplies a distinct identity. [Source: [mcp-caller.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/lib/mcp-caller.ts).]
- **Post-write hygiene is not prevention:** the write validator cannot block a completed write. [Source: [validate-write.ts](https://github.com/breferrari/obsidian-mind/blob/6302ab2babd931e28620f2af96eaf09a90f414b3/.claude/scripts/validate-write.ts#L44-L79).]
- **CI trigger coverage:** `.claude/settings.json` is absent from the Tests workflow path filters; a hook-config-only edit need not trigger that matrix. Node tests do not prove live agent integrations work. [Source: test.yml.]
- Direct installation imports a substantial operating template; retrieval quality, privacy enforcement and maintenance cost were not measured locally.

## Evidence checked

- Parent refreshed GitHub metadata and confirmed source revision after the independent read-only review.
- Parent read pinned README consultation/exposure passages; scope, explanations and supersession source; write-scope handling; promoted-content bounds; and test workflow configuration.
- Independent source review also inspected MCP server/bridge, exposure policy, caller identity, atomic writes, hook configuration and relevant tests. High-impact scope and correction claims were checked against source by the parent.
- Selective downloaded source snapshots were used, not a full repomix pack. No raw code pack is committed into the vault.
- **Runtime testing:** not performed. This ingest preserves design evidence, not an install or performance certification.

## Alternatives / related repos

- [GBrain](garrytan--gbrain.md) — related retrieval/indexing and agent-addressable knowledge reference.
- [Claude-Mem](thedotmack--claude-mem.md) — related session-capture and memory-compression reference; different persistence/hook trade-offs.
- [Ars Contexta](agenticnotetaking--arscontexta.md) — related Markdown knowledge-system design reference.

These links provide comparative navigation, not a fresh head-to-head benchmark of the alternatives.

## Operating boundary

Architecture, procedure and retrieval changes need separate established owners. This source evaluation does not imply adoption or authorize operating-state changes.

## Review candidates

Non-binding patterns, not implementation tasks:

1. **Artifact-bound consultation:** review whether existing consequential plans expose prior decisions and contrary evidence. Promote only when an actual missed-context failure or clear consumer gap is established.
2. **Scope-before-ranking:** test a representative cross-project constraint against current retrieval behavior. Promote only if an applicability leak is demonstrated and an owning boundary is identified.
3. **Recall explanations:** assess a real missing-context diagnosis. Promote only if an exclusion receipt would materially reduce uncertainty without leaking withheld content.
4. **Correction propagation:** check a real narrowed/superseded procedure and its consumers. Promote only for a demonstrated stale-guidance path.
5. **Maintained-owner promotion:** inspect an actual duplicate discovery/curated pair. Promote only if retrieval repeatedly surfaces the obsolete copy.

## Commitment disposition

**Not promoted.** The request authorizes ingestion, not implementation, runtime installation, skill changes, issue creation or star-list management.

## Timeline

- **2026-10-02** | Pinned repository source and GitHub API — Captured a source-backed pattern evaluation of v8.5.0; retained applicability, explanation, supersession, promotion and security-boundary caveats. No runtime adoption.
