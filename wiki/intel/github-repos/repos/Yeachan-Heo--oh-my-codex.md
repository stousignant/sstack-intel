---
type: concept
title: Yeachan-Heo/oh-my-codex
usage: reference-only
source: 'https://github.com/Yeachan-Heo/oh-my-codex'
status: deep-analyzed
topics:
  - github-repo
  - codex-cli
  - agent-orchestration
  - multi-agent
  - skills
  - hooks
  - tmux
  - workflow-layer
aliases:
  - oh-my-codex
  - OMX
  - GitHub repo: Yeachan-Heo/oh-my-codex
license: MIT
category: coding-agent-harness
ingested_at: '2026-06-14T10:22:21.147Z'
source_kind: 'mcp:put_page'
ingested_via: 'mcp:put_page'
last_reviewed: '2026-06-14T00:00:00.000Z'
recommendation: adopt-now
score_confidence: high
usefulness_score: 91
---

# Yeachan-Heo/oh-my-codex

> Reference-stack evaluation as reviewed 2026-06-14. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `91/100` — very high signal as a Codex-native worker harness if Hermes remains the cockpit/source of truth; still too overlapping and high-authority to become the primary runtime.
- **Recommendation:** `adopt-now` — run a disposable-profile bakeoff where Hermes launches/verifies one OMX-backed Codex worker lane; adopt only that worker-lane shape if it improves reliability without global config drift.
- **Usage observed 2026-06-14:** `reference-only`.
- **Confidence:** `high`
- **Review candidate:** Test OMX as an optional Codex worker harness under disposable `CODEX_HOME`, with Hermes owning task routing, worktree boundaries, approvals, verification, and durable notes.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Directly relevant to Codex CLI, multi-agent coding, skills, hooks, tmux/HUD, and Hermes/OpenClaw interop; fit improves if scoped as a Hermes-supervised worker lane rather than a runtime replacement. |
| Leverage | 25/25 | Strong patterns for clarify → plan → critique → durable execution, team coordination, state surfaces, worker preflight, and proof-bundle gates. |
| Reuse readiness | 17/20 | npm package, built successfully from source, `omx --help` and `omx doctor` ran locally; safe real use still needs isolated Codex profile/setup. |
| Maturity/trust | 13/15 | Extremely active, MIT in package/workspace, broad tests/docs; caveat: GitHub license API returned no root license file and npm audit found moderate transitive advisories. |
| Differentiation | 12/15 | Strongest Codex-native analogue to oh-my-claudecode-style workflow layers; differentiates via Codex plugin layout, OMX wiki/state/MCP/Hermes bridge, and team protocol. |
| **Total** | **91/100** | Pattern-rich and compatible with a Hermes-supervised Codex worker lane, but global setup remains the wrong default. |

## Verdict

OMX is worth treating as a high-priority Codex **worker-lane harness candidate**, not as a new default runtime. It wraps Codex CLI with skills, hooks, agent teams, tmux/HUD visibility, durable goals, state/wiki operations, notification gateways, and setup/doctor checks. These capabilities matter when a workflow needs Hermes to supervise a separate Codex execution lane.

The architecture update is important: if **Hermes remains orchestrator and source of truth** — Discord cockpit, memory, task routing, worktree creation, approval policy, final diff review, tests/smoke checks, commits/pushes, and GBrain/second-brain notes — then OMX no longer has to be evaluated as a competing cockpit. It can be tested as a bounded Codex runtime enhancer inside isolated worker lanes.

Default stance: **Hermes owns the operating system; OMX may earn a narrow role inside Codex worker lanes after a disposable-profile bakeoff.** Installing it globally would still be premature because it mutates Codex config/hooks/prompts and can create a second skill/state/memory surface.

## Reference-stack relevance

- OMX is one of the closest external mirrors of the “Hermes as agent cockpit” direction, but built around Codex CLI instead of Hermes.
- If kept subordinate to Hermes, it could become a useful **Codex worker-lane harness**: Hermes dispatches/approves/verifies, while OMX handles Codex-side setup, doctor checks, hooks/HUD, and worker ergonomics.
- Its default workflow language — `$deep-interview` → `$ralplan` → optional `$prometheus-strict` → `$ultragoal` / `$team` — is a useful comparison point for SStack planning, critique, and done-proof skills.
- The repo contains practical patterns for Codex plugin skill distribution, setup/doctor diagnostics, tmux/HUD lifecycle, team worker ownership, notification gateways, and state/wiki/MCP parity surfaces.
- Its gate-heavy release notes and runtime-reliability focus are more decision-relevant than the hype/star count when evaluating evidence-first tooling and reviewed self-improvement.

## What it is

`oh-my-codex` / OMX is a Node/TypeScript plus Rust workflow layer for OpenAI Codex CLI. It ships an `omx` CLI, Codex plugin layout, skill bundle, native hooks, tmux/HUD runtime helpers, team orchestration, durable goal modes (`ultragoal`, `ralph`, `performance-goal`, `autoresearch-goal`), local state/wiki/code-intel CLI surfaces, and optional MCP/OpenClaw/Hermes compatibility paths.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-06-13: `30,868` stars, `2,429` forks, created 2026-02-02, pushed 2026-06-13, latest release `v0.18.11` on 2026-06-09, not archived, not a fork.
- README: official npm package is `oh-my-codex`; recommended path is `codex --version`, `npm install -g oh-my-codex`, `omx setup`, then `omx --worktree=feat/task --madmax --high`; README warns `--madmax` bypasses Codex approvals/sandbox.
- Package manifests: `package.json` version `0.18.11`, Node `>=20`, MIT license, `omx` bin, build/test/doctor/plugin verification scripts; Cargo workspace version `0.18.11`, MIT license, Rust `1.73`.
- Clone of [the upstream repository](https://github.com/Yeachan-Heo/oh-my-codex) inspected; key files inspected included `README.md`, `package.json`, `Cargo.toml`, `docs/team-coordination-protocol.md`, `docs/openclaw-integration.md`, `docs/agents.html`, `plugins/oh-my-codex/*`, and `src/cli/doctor.ts`/team-related files by file search.
- Local smoke test in disposable clone: `npm ci && npm run build && node dist/cli/omx.js --help` succeeded; `node dist/cli/omx.js doctor --json` ran and reported `10 passed, 7 warnings, 0 failed` in this unconfigured environment.
- `npm audit --omit=dev --json` reported two moderate transitive vulnerability buckets (`hono`, `qs`) with fixes available. Treat this as a sandbox review item, not a blocker for pattern capture.
- GitHub license API returned 404 for a license endpoint, but npm/package and Cargo workspace declare `MIT`, and README badges MIT.

## Strengths

- **Codex-native workflow layer:** closest observed repo to a complete Codex CLI operating system: setup, launch policies, worktrees, tmux/HUD, hooks, auth slots, state, wiki, code-intel, MCP, and teams.
- **Good operational semantics:** team protocol explicitly distinguishes lightweight fan-out from coordinated work and names shared source-of-truth, ACK-readback handoffs, mutual monitoring, backup/reassignment, adaptability checkpoints, and team orientation.
- **Doctor-first posture:** README requires `omx doctor`, `codex login status`, and `omx exec --skip-git-repo-check -C . "Reply with exactly OMX-EXEC-OK"` before treating runtime as ready.
- **Plugin/skill packaging evidence:** plugin tree includes ~30 skill files plus plugin metadata, hooks, `.mcp.json`, and app metadata; useful for SStack projection/skillpack packaging ideas.
- **Interop clues:** OpenClaw/generic notification gateway docs use activation env gates and structured event formats; changelog mentions bounded Hermes MCP coordination and safer tmux/MCP lifecycle fixes.
- **Build proof:** source built locally without needing Codex credentials, and CLI help/doctor were executable from the compiled `dist` output.

## Risks / caveats

- **Broad runtime authority:** setup touches Codex config, hooks, prompts/skills, plugin cache, tmux, MCP, and runtime state. Do not install globally without a disposable `CODEX_HOME`/profile and explicit consent.
- **Sandbox-bypass ergonomics:** README prominently recommends `--madmax --high`; it warns this bypasses approvals/sandbox, but that default is too sharp for private repos unless paired with worktrees and trust boundaries.
- **Overlap with Hermes/SStack:** direct adoption would create a second cockpit and another skill/workflow source of truth. This is mostly resolved only if OMX is constrained to a Hermes-supervised Codex worker lane.
- **Competing state risk:** OMX wiki/state can be useful telemetry, but should not become durable memory; GBrain/second-brain remains canonical.
- **License metadata inconsistency:** package/Cargo/README say MIT, but GitHub's license endpoint returned 404, likely no root `LICENSE` recognized. For code reuse beyond ideas, verify license text before copying.
- **Dependency audit warnings:** local production audit found moderate transitive advisories in `hono` and `qs` with fixes available.
- **Hype/velocity risk:** 30k+ stars and rapid release cadence in a young repo are impressive but also demand extra skepticism around supply-chain and workflow-surface changes.

## Integration ideas

- Distill OMX's doctor/smoke-test contract into Hermes/SStack: separate install-shape checks from real model/auth execution proof, and report warnings vs hard failures cleanly.
- Test whether OMX can be a Hermes-supervised Codex worker lane: Hermes creates the task/worktree, launches the lane, captures transcript/proof bundle, reviews diff/tests, and owns final commit/push.
- Compare `docs/team-coordination-protocol.md` against Hermes `delegate_task`, Kanban, and any future agent-board semantics; steal ACK/readback, owner, blocked-worker, and integration-risk language.
- Mine plugin-skill mirroring and setup verification for SStack's “one shared source projected into harnesses” convention.
- Treat `ultragoal` / final-review proof gates as a reference for SStack definition-of-done and acceptance-verification skills.
- If a Codex CLI worker lane is needed, test OMX with `CODEX_HOME="$DISPOSABLE_CODEX_HOME"` and a copied toy repo first; never point initial setup at a canonical Codex/Hermes environment.

## Worker-lane bakeoff protocol

Adoption test shape:

1. Create disposable Codex home: `CODEX_HOME="$DISPOSABLE_CODEX_HOME"`.
2. Use a toy repo or temporary worktree, not canonical Hermes/GBrain/SStack.
3. Install/run OMX only there, with an isolated npm prefix as well as disposable Codex home: `npm install --prefix "$DISPOSABLE_PREFIX" oh-my-codex`, then run that local `omx` binary for `setup` and `doctor --json`. Do not use a global npm install for this sandbox.
4. Have Hermes launch exactly one Codex worker through OMX on a tiny task.
5. Require a proof bundle:
   - exact env vars used;
   - files touched under `CODEX_HOME`;
   - git status before/after;
   - command transcript;
   - whether hooks were installed;
   - whether Hermes can capture and verify output;
   - cleanup procedure.
6. Decision rule:
   - **Adopt worker-lane** if it cleanly improves Codex execution without global config drift;
   - **Distill patterns only** if useful but invasive;
   - **Reject** if it creates config drift, competing state, or verification gaps.

## Alternatives / related repos

- [Yeachan-Heo/oh-my-claudecode](Yeachan-Heo--oh-my-claudecode.md) — analogous Claude Code workflow/team layer from the same author family; stronger if the active lane is Claude Code, but suitability depends on the chosen worker lane and its access/budget boundaries.
- [automazeio/ccpm](automazeio--ccpm.md) — stronger PRD/epic/GitHub issue execution routing; less of a Codex runtime overlay.
- [obra/superpowers](obra--superpowers.md) — focused cross-harness skill/methodology layer; smaller and easier to distill.
- [steipete/agent-scripts](steipete--agent-scripts.md) — high-signal shared agent instruction/scripts corpus with maintainer orchestration patterns.
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — the reference cockpit/runtime in this evaluation; OMX should inform Hermes, not replace it by default.

## Review candidates and guidance

- Review candidate: Run a disposable-profile OMX worker-lane bakeoff only if a Codex secondary lane is relevant to a concrete workload.
- Review candidate: Extract a small comparison note or SStack issue for OMX-style doctor/runtime-readiness checks if Hermes lacks an equivalent proof bundle.
- Review candidate: Compare OMX team coordination protocol against Hermes delegated-agent handoff semantics before designing any new agent board.
