---
title: LLM Wiki Second-Brain Repo Comparison
created: 2026-05-24
updated: 2026-09-13
type: comparison
tags:
  - llm-wiki
  - second-brain
  - github-repos
  - hermes
  - gbrain
  - knowledge-management
topic: llm-wiki
role: comparison
status: archived
sources:
  - wiki/intel/github-repos/repos/nashsu--llm_wiki.md
  - wiki/intel/github-repos/repos/atomicstrata--llm-wiki-compiler.md
  - wiki/intel/github-repos/repos/SamurAIGPT--llm-wiki-agent.md
  - wiki/intel/github-repos/repos/AgriciDaniel--claude-obsidian.md
  - wiki/intel/github-repos/repos/kytmanov--obsidian-llm-wiki-local.md
  - wiki/intel/github-repos/repos/nvk--llm-wiki.md
lifecycle: stable
confidence: medium
last_reviewed: 2026-09-13
review_cadence: quarterly
---

# LLM Wiki Second-Brain Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

> Related concept: [LLM-wiki pattern](../../../concepts/ai-engineering/llm-wiki-pattern.md).

> **Archived decision evidence:** this comparison records the 2026-05/06 build-vs-adopt reasoning that led to Brainforge. The retained design separates deterministic compiler/doctor checks from downstream indexing through GBrain/MCP. The Brainforge `propose` and `sync` command ideas below are retired historical proposals, not supported Wikic commands.

## Executive recommendation

**Build, but not yet as a big app.** The right move is to steal patterns from the ecosystem and create a thin Hermes/GBrain-native CLI + companion skill **after one bounded pilot** proves candidate generation saves time versus Hermes writing curated notes directly.

Default path:

1. **Use existing tools as references/sandboxes**, not as canonical writers.
2. **Pilot `obsidian-llm-wiki-local` or `llm-wiki-compiler` in a disposable sandbox** on copied non-sensitive sources.
3. If generated candidates are useful, build a small repo: `brainforge`.
4. Keep Hermes as the judgment layer, GBrain as the index/query layer, and Markdown files as canonical curated knowledge.

Blunt take: a custom CLI is justified **only** for deterministic state/review/validation around Hermes. Building another desktop app or separate brain would be waste.

## Decision matrix

| Repo | Score | Best role | Direct adopt? | Main thing to steal | Main risk |
|---|---:|---|---|---|---|
| [kytmanov/obsidian-llm-wiki-local](../repos/kytmanov--obsidian-llm-wiki-local.md) | 90 | Best CLI/compiler reference | Pilot in sandbox | Python CLI, SQLite state, draft review, provider abstraction, tests | Maintenance mode; own vault conventions |
| [nashsu/llm_wiki](../repos/nashsu--llm_wiki.md) | 88 | Best full product reference | No, learn/pilot only | Rich ingestion/search/graph/review/API loop | GPL-3.0; desktop-first; overlaps with Hermes/GBrain |
| [atomicstrata/llm-wiki-compiler](../repos/atomicstrata--llm-wiki-compiler.md) | 88 | Existing compiler/candidate generator | Bounded sandbox only | Review queue, file-block write boundary, MCP surface | Provider quirks; generated quality; no Copilot assumption |
| [nvk/llm-wiki](../repos/nvk--llm-wiki.md) | 86 | Best protocol/topic-hub reference | No, distill | Hub/topic isolation, inventory, datasets, audit/librarian, archive lifecycle | Instruction-heavy; separate hub could compete with vault |
| [AgriciDaniel/claude-obsidian](../repos/AgriciDaniel--claude-obsidian.md) | 84 | Best Obsidian/skillpack reference | No, distill | Hot cache, manifest/delta tracking, skills, lint/fold/semantic tiling | Claude-first; can create vault sprawl |
| [SamurAIGPT/llm-wiki-agent](../repos/SamurAIGPT--llm-wiki-agent.md) | 82 | Simple agent-scaffold pattern | Sandbox only | Raw → wiki → health/lint/graph scaffold | Agent discipline; less productized |

## Category map

The ecosystem splits into six useful archetypes:

1. **Full product/app:** `nashsu/llm_wiki` — polished local app shape with graph/search/API/review.
2. **Compiler CLI:** `kytmanov/obsidian-llm-wiki-local`, `atomicstrata/llm-wiki-compiler` — closest to the proposed CLI-centered LLM-wiki design.
3. **Agent scaffold:** `SamurAIGPT/llm-wiki-agent` — simple repo structure + agent instructions.
4. **Obsidian skillpack:** `AgriciDaniel/claude-obsidian` — operating procedures around an Obsidian wiki.
5. **Portable protocol:** `nvk/llm-wiki` — hub/topic/inventory/dataset/audit semantics across Claude/Codex/OpenCode/Pi.
6. **Existing reference stack:** Hermes + GBrain + second-brain — already owns the real runtime, user context, and index layer.

That means the winning design is not "pick one repo." It is **compose the best primitives into the existing reference stack.**

## Build vs adopt verdict

### Adopt wholesale?

**No.** None of the repos should become the canonical writer for the canonical Markdown vault right now.

Why:

- The reference vault already has conventions, repo-intelligence layout, customized operating context, and GBrain registration.
- Generated wiki systems tend to produce lots of pages; that is useful in a sandbox and dangerous in the canonical vault.
- Provider assumptions are uneven. A runtime's subscription/OAuth provider is not necessarily a drop-in backend for a separate compiler CLI; verify compatibility instead of assuming shared credentials.
- GBrain already covers index/query/sync. Adding another RAG-ish layer or app control plane creates duplication.

### Use existing tools as sandboxes?

**Yes.** The best immediate experiment is to run copied sources through `olw` or `llm-wiki-compiler` and compare candidate usefulness.

Recommended pilot order:

1. `kytmanov/obsidian-llm-wiki-local` (`olw`) — because its test suite and review lifecycle are strongest.
2. `atomicstrata/llm-wiki-compiler` — because it already has a review queue/MCP-ish surface and earlier local work exists.
3. `nashsu/llm_wiki` — only if we want to study UI/API/graph/product patterns, not as the main route.

### Build a Hermes-native repo?

**Yes, if the pilot clears the bar.** The build should be small and boring:

```text
brainforge
├── CLI: deterministic ingest/propose/review/lint/sync commands
├── schema: candidate records, source manifest, path allowlist
├── adapters: Hermes-agent prompt runner first; provider adapters later
├── validators: file-block parse, no path escape, no secret writes, no raw mutation
└── skill: tells Hermes when/how to run the CLI and how to judge promotion
```

The CLI should do state and safety. Hermes should do taste/judgment. GBrain should do indexing.

## Historical proposed command contract

The retired Brainforge proposal combined deterministic doctor/lint, immutable source capture, candidate proposal, review list/show/accept, and separately authorized indexing. These are historical design responsibilities, not supported Wikic commands or operating instructions.

Non-negotiables: review-first promotion; immutable source evidence; candidates outside curated folders; structured output; path containment; source diff/readback; explicit backend selection; no canonical writes without accepted review.

## Pattern extraction table

| Pattern | Source repos | Local target |
|---|---|---|
| Draft review queue | `olw`, `llm-wiki-compiler`, `nashsu` | `.brainforge/candidates/` with accept/reject |
| Small flat schemas | `olw` | LLM output contracts for wiki/concepts/articles/queries |
| Manual-edit protection | `olw` | body hashes before updates |
| File-block/path validation | `nashsu`, `llm-wiki-compiler` | no path traversal, allowed subtrees only |
| Source manifest/delta tracking | `claude-obsidian`, `olw` | source hash → generated candidates/pages |
| Hot cache | `claude-obsidian` | optional per-project compact context, not global brain |
| Topic isolation | `nvk/llm-wiki` | map to existing vault sections or sandboxes |
| Inventory/dataset layer | `nvk/llm-wiki` | ingestion queues and external corpus manifests |
| Deterministic lint/doctor | all | fast local checks before/after generation |
| Graph/semantic tiling | `nashsu`, `claude-obsidian`, `llm-wiki-agent` | optional duplicate/link audit; do not over-index early |
| GBrain final sync | reference stack | Separately authorized indexing after accepted source delivery |

## Repo-by-repo synthesis

### `kytmanov/obsidian-llm-wiki-local`

Best direct reference. It proves this can be a real CLI with tests, not just a prompt. Its most valuable pieces are review lifecycle, state DB, provider abstraction, flat schemas, compare mode, and Git undo. If the workload needs to try existing software, start here in a disposable sandbox.

### `nashsu/llm_wiki`

Best product reference. The desktop app has the richest end-to-end loop: document extraction, project graph, LLM provider UI, search, review, local API, and web clipper. But GPL-3.0 and desktop-first architecture make it more of a design oracle than a base for the reference stack's CLI.

### `atomicstrata/llm-wiki-compiler`

Best existing candidate generator already explored locally. The review queue and compiler behavior are useful, but provider assumptions are fragile for this machine. The key lesson: don't make Copilot or raw provider keys implicit; make backend selection explicit and allow Hermes-agent-driven generation.

### `nvk/llm-wiki`

Best operating protocol. It is more ambitious than v0 should be, but its topic hub, inventory, datasets, audit/librarian, archive lifecycle, and multi-runtime packaging are exactly the kind of semantics a future Hermes skill/CLI should grow into.

### `AgriciDaniel/claude-obsidian`

Best skillpack/Obsidian workflow reference. Hot cache, manifest tracking, contradiction callouts, lint, fold, semantic tiling, and deterministic address allocation are excellent patterns. But the operator should not install a Claude-first control plane over the canonical Hermes/GBrain setup.

### `SamurAIGPT/llm-wiki-agent`

Best minimal scaffold. It is useful as a simple mental model: immutable raw sources, generated wiki, deterministic health checks, graph output, and append-only log. It is less compelling as a maintained runtime than `olw` or a Hermes-native wrapper.

## Conditional reference-stack guidance

My take: **keep the proposed build small.** Consider a dedicated repo eventually, but make it a thin CLI/skill pair around Hermes and GBrain, not a new app or competing brain.

The high-leverage sequence:

1. **One pilot:** run `olw` on copied raw sources and inspect drafts.
2. **One spec:** define a Hermes-native CLI boundary with deterministic state/review/validation, not another canonical writer.
3. **One v0 CLI:** implement only source capture, candidate proposal, review, lint, and GBrain sync.
4. **One skill:** teach Hermes to operate the CLI safely and decide what deserves promotion.

What would change my mind:

- If `olw` or `Synto` already works perfectly with the reference stack's vault and provider setup, fork/adapt instead of building.
- If candidate generation is worse than Hermes-authored notes, skip the CLI and just improve the `llm-wiki` skill/pilot workflow.
- If GBrain adds native source→candidate→review workflows soon, use that instead.

## Open questions

- Does `kytmanov/synto` supersede enough of `olw` that it should be the real reference?
- What provider/backend should a Hermes-native CLI call: Hermes agent subprocess, OpenAI-compatible API, local Ollama/vLLM, or pluggable adapters?
- Which first corpus gives a fair pilot: GitHub repo READMEs, article/video transcripts, or non-sensitive synthetic strategy notes?
- Should candidates live in `.brainforge/candidates/`, `research/.../sandbox/`, or a separate ignored worktree?
