---
type: concept
title: just-every/code
source: 'https://github.com/just-every/code'
category: coding-agent-harness
status: deep-analyzed
usefulness_score: 72
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: '2026-08-19'
license: Apache-2.0
topics:
  - github-repo
  - codex-cli
  - codex-fork
  - coding-agent-harness
  - multi-agent
  - browser-automation
  - provider-routing
  - supply-chain
aliases:
  - Every Code
  - just-every/code
  - '@just-every/code'
  - 'GitHub repo: just-every/code'
---

# just-every/code

> Reference-stack fit as reviewed 2026-08-19; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `72/100` — genuinely well-built Codex fork with several patterns worth stealing, but adopting it would put a second, less-supervised coding runtime on top of the Codex/OMX lane the reference architecture uses.
- **Recommendation:** `distill-pattern` — harvest the patch-validation harness, background review-in-a-worktree, install-collision `doctor`, proxy-mediated CI key isolation, and protected-globs agent-PR guard into the Codex/OMX + Hermes lane. Do not install it as a runtime.
- **Usage observed 2026-08-19:** `reference-only`. Smoke-tested once with a disposable npm prefix; no retained runtime/configuration adoption was reported.
- **Confidence:** `high` — metadata, README, manifests, workflows, and the security-relevant Rust source were read directly, and the released binary was executed with no credentials.
- **Review candidate:** none as adoption. Distil the five patterns below into SStack/OMX doctrine; revisit only if the operator ever wants a second write-capable coding runtime, and only after the sub-agent sandbox-bypass design changes.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 16/25 | Same ecosystem as the reference stack's active Codex/OMX lane — and that is the problem. It reads the existing per-user Codex home (verified in `code-rs/core/src/config/sources.rs:1741`), replaces the `code`/`coder` binary, and claims ownership of orchestration that Hermes already owns. |
| Leverage | 17/25 | Real time-savers on paper: per-patch validation harness, background Auto Review in a separate worktree, CDP browser control. But the reference architecture already has a browser driver, OMX for coding workers, and Hermes as cockpit; incremental leverage is mostly pattern-level. |
| Reuse readiness | 17/20 | `npm install @just-every/code` pulled a prebuilt musl binary and ran in seconds; `doctor` works with zero credentials; ~30 docs pages; extensive `config.toml` surface. Building from source needs a Rust toolchain and a 310k-LOC workspace. |
| Maturity/trust | 10/15 | 457 releases, near-daily cadence, 1,725 test attributes across 217 files, upstream `process-hardening` (no core dumps, no ptrace, `LD_PRELOAD` stripped), strict pnpm supply-chain policy. Against that: bus factor 1, no PR-time test CI, no fork-specific security-disclosure path, ~79 upstream crates missing from the fork's active tree, and unverified binary download in the postinstall fallback. |
| Differentiation | 12/15 | Genuinely differentiated from upstream Codex — validation harness, Auto Review, browser integration, themes, cross-vendor agent commands. But the multi-agent implementation earns its differentiation by disabling every downstream agent's safety layer. |
| **Total** | **72/100** | Strong engineering, wrong ownership boundary, and one design choice the operator should not adopt. |

## Verdict

Every Code is a serious, actively maintained fork of `openai/codex` — not a vibe-coded wrapper. It ships daily releases, a real test suite, a hardened process start-up, and a set of features upstream does not have. For an operator without an established coding lane, it would be a credible pick.

In the dated reference architecture, Codex through OMX is the coding lane, Hermes is the cockpit, a separately authorized Claude lane is complementary, and GBrain/Markdown is the knowledge layer. Every Code wants to be the coding lane *and* the orchestrator *and* the browser driver *and* the provider router. Installing it means two binaries competing for the Codex home, two orchestration models, and two update paths — for features that are mostly patterns that can be selectively adapted.

The decisive finding is not maturity, it is the sub-agent design. When `/code`, `/solve`, `/plan`, or Auto Drive launch a write-mode sub-agent, the fork spawns the vendor CLI with its safety layer explicitly disabled — `--dangerously-skip-permissions` for Claude Code, `--sandbox=false --dangerously-skip-permissions` for Antigravity, `--yolo` for Copilot, `-y` for Qwen, `--dangerously-bypass-approvals-and-sandbox` for its own binary (`code-rs/core/src/agent_defaults.rs:16-33`). The source comment is candid: *"Agents: run without OS sandboxing; rely on per-branch worktrees for isolation"* (`code-rs/core/src/agent_tool.rs:1805`). A git worktree bounds where the agent is *supposed* to work; it does nothing to bound a process that has been told to skip approvals. The sub-agent also inherits the full parent environment and keeps `HOME` intact so vendor CLIs can use the invoking user's existing Claude and Gemini login sessions (`agent_tool.rs:1809-1880`).

Under the reference-stack authority boundary, cross-vendor workers must use explicitly authorized supervised lanes. Every Code's launch design can instead drive an existing subscription session unsupervised with permissions off.

Take the patterns. Leave the runtime.

## Reference-stack relevance

- **It overlaps the reference coding lane.** Every Code reads the Codex `auth.json` credential file when the per-user Code home does not exist and no env override is set — so an ordinary `coder` invocation can pick up existing Codex credentials unless its home/environment is isolated. Writes go only to the per-user Code home, so the collision is read-side, but it is real.
- **The validation harness is the single best steal.** Per-patch, category-grouped external validators (`shellcheck`, `tsc`, `eslint`, `mypy`, `pyright`, `golangci-lint`, `cargo-check`, `actionlint` as functional; `prettier`, `markdownlint`, `yamllint`, `shfmt`, `hadolint` as stylistic) with a tool allowlist and per-tool timeout (`code-rs/core/src/config_types.rs:622-726`). That maps directly onto Hermes hooks and the OMX worker lane's definition-of-done.
- **Auto Review is the second steal.** A background watcher that reviews every code-changing turn in a *separate* worktree and reports issues plus ready-to-apply fixes without blocking the main thread. That is the "verify, don't just generate" loop the reference lens favors.
- **Their CI shows two patterns worth copying.** `issue-code.yml` runs the agent against a local responses-API proxy on `127.0.0.1:5057` so the agent never sees the raw `OPENAI_API_KEY`, and guards `PROTECTED_GLOBS` (`.github/**`, all lockfiles and `package.json`) against agent edits. Both are useful review candidates for repositories where coding agents open PRs.
- **`doctor` demonstrated a binary-collision hazard in the review environment.** It detected VS Code's `code` 1.131.0 in two system-bin locations, matching the README warning; a global install can therefore be messy.

## What it is

A community fork of `openai/codex` by the Every / just-every org (`justevery.com`), published as `@just-every/code` with a `coder` binary. Rust TUI coding agent, ChatGPT sign-in or API key, MCP client and server, sandbox modes, plus fork-specific additions: Auto Drive orchestration, Auto Review, CDP browser integration, a theme system, `/settings`, a patch validation harness, and `/plan` `/solve` `/code` commands that fan work out to Claude, Gemini/Antigravity, Copilot, and Qwen CLIs.

Repo layout is unusual and important: `code-rs/` is the fork's live workspace (605 Rust files, ~310k LOC), while `codex-rs/` is a read-only mirror of `openai/codex:main` refreshed by an automated job every 30 minutes, used as a backport source. `AGENTS.md` states the rule explicitly: *"Treat `codex-rs` as a read-only mirror of `openai/codex:main`; edit Rust sources under `code-rs` instead."*

## Evidence checked

**Metadata** (re-verified 2026-08-19, `gh repo view` / `gh api`) — matches the earlier Hermes observation exactly:

- 3,895 stars, 235 forks, 26 watchers, Apache-2.0 (`LICENSE` is Apache 2.0 with `Copyright 2025 OpenAI` preserved), created 2025-08-10, last push 2026-08-11T21:11Z, 780 MB.
- `fork: true`, parent and source both `openai/codex`.
- Latest release `v0.6.172` published 2026-08-10; 457 releases total; npm `@just-every/code@0.6.172` modified 2026-08-10.
- 27 open issues, 9 open PRs; issues and discussions enabled. Oldest open issues date to 2025-09-22 with little movement, so the backlog is stale even though releases ship daily.
- Contributors: `zemaj` 3,523 commits, then a long tail of `*-oai` upstream authors carried in by merges. Fork-side commits since 2026-06-01 are effectively `james`/`jif` plus a GitHub Action. **Bus factor 1.**

**Source and docs read** (shallow blobless clone, `codex-rs` mirror and `third_party` excluded):

- `README.md`, `AGENTS.md` (= `CLAUDE.md` symlink), `SECURITY.md`, `CHANGELOG.md`, `package.json`, `pnpm-workspace.yaml`, `config.toml.example`, `docs/` (30 pages incl. `auto-drive.md`, `sandbox.md`, `execpolicy.md`, `skills.md`).
- `code-rs/core/src/agent_defaults.rs` — sub-agent CLI catalog and launch args.
- `code-rs/core/src/agent_tool.rs` (3,444 lines) — sub-agent spawn, worktree setup, env construction, API-key mirroring.
- `code-rs/core/src/config/sources.rs` — Code-home versus legacy Codex-home resolution.
- `code-rs/core/src/config_types.rs` — validation harness config, GitHub workflow checks.
- `code-rs/tui/src/updates.rs` — update check and auto-upgrade.
- `code-rs/core/src/bridge_client.rs` (974 lines) — Code Bridge WebSocket client, secret-based auth frame, heartbeat staleness.
- `code-rs/browser/src/manager.rs` (2,709 lines), `config.rs`, `page.rs` — CDP control, `ps aux` scan for `--remote-debugging-port`, temp vs persistent user-data-dir.
- `code-rs/process-hardening/src/lib.rs` — pre-main hardening.
- `codex-cli/postinstall.js` (~800 lines), `codex-cli/scripts/preinstall.js`, `codex-cli/package.json`.
- `.github/workflows/` — all 11 workflows, especially `release.yml`, `issue-code.yml`, `upstream-merge.yml`, `preview-build.yml`.
- `scripts/ci-tests.sh`.

**Clone/evidence:** disposable clone (`git clone --depth 1 --filter=blob:none`, sparse-checkout excluding `codex-rs/` and `third_party/` — 48 MB working tree). No repomix pack: at 780 MB with a full upstream mirror vendored in-tree, a pack would have been dominated by mirrored upstream code rather than fork code, so targeted reads of the fork's own `code-rs` tree were the higher-signal substitute.

**Smoke checks** (disposable npm prefix, no credentials, no global install, `CODE_HOME` redirected to a disposable scratch directory):

| Command | Outcome |
|---|---|
| `npm install @just-every/code@0.6.172` (local prefix) | Success in 2s; 137 MB; binary came from optional platform package `@just-every/code-linux-x64-musl`, not the GitHub-download fallback. |
| `./node_modules/.bin/coder --version` | `code 0.6.172` |
| `./node_modules/.bin/coder --help` | Full command list: `exec`, `auto`, `login`, `mcp`, `mcp-server`, `app-server`, `apply`, `resume`, `cloud`, `doctor`, `preview`, `llm`, `bridge`. |
| `./node_modules/.bin/coder doctor` | Detected the `code` collision with VS Code 1.131.0 in two system-bin locations; reported npm global roots; exited 0. |

Not attempted, and why: `cargo` is not installed in the review environment, and compiling a 310k-LOC Rust workspace (`build-fast.sh`, which `AGENTS.md` says "can take 20+min from a cold cache") plus a toolchain download is disproportionate for a triage when the published binary is what a user would actually install. `cargo nextest run` was likewise not run locally; the release workflow evidence below covers test reality. No login, no API calls, no model usage.

**Observed smoke side effect:** the binary created a 71 MB versioned cache. No Code home was created and the existing Codex home's mtime was unchanged in that test. Disposable-home and cache containment both matter; this is not a claim about present operator state.

## Strengths

- **Real release engineering.** 457 releases, near-daily. `release.yml` runs `cargo nextest run --no-fail-fast --locked` across the workspace plus `scripts/ci-tests.sh` CLI smokes (`--version`, `completion bash`, `doctor`) before publishing. **Verified**, not a README claim.
- **Real test mass.** 1,725 `#[test]`/`#[tokio::test]` attributes across 217 files in `code-rs`.
- **Supply-chain hygiene in the workspace.** `pnpm-workspace.yaml` sets `minimumReleaseAge: 10080` (7 days), `blockExoticSubdeps: true`, `strictDepBuilds: true`, `trustPolicy: no-downgrade`, and an explicit `allowBuilds` allowlist. `package.json` pins ~18 transitive `resolutions`.
- **Process hardening inherited and kept.** `PR_SET_DUMPABLE 0`, core-size rlimit 0, ptrace-deny on macOS, `LD_PRELOAD`/`DYLD_*` stripped pre-main.
- **Telemetry is opt-in.** The OTel exporter defaults to `OtelExporter::None`; nothing is emitted without a configured endpoint. Auto-upgrade also defaults to **off** (`auto_upgrade_enabled: cfg.auto_upgrade_enabled.unwrap_or(false)`).
- **Install-time care.** The postinstall detects an existing non-Every `code` on PATH and *skips* creating the global shim rather than shadowing it; global aliasing is gated on `npm_config_global === 'true' && !isNpx`.
- **Honest legal framing.** README states plainly that it is not affiliated with OpenAI, preserves upstream LICENSE/NOTICE, and tells users not to evade provider rate limits or rotate accounts.
- **Upstream tracking is automated and PR-gated.** `upstream-merge.yml` polls `openai/codex` every 30 minutes and pushes to an `upstream-merge` branch — not straight to `main`.

## Risks / caveats

- **Sub-agent sandbox bypass is the headline risk.** Write-mode agents launch with `--dangerously-skip-permissions` / `--sandbox=false` / `--yolo` / `--dangerously-bypass-approvals-and-sandbox`, inheriting the full parent env and the user's real `HOME`, so they can operate through the invoking user's logged-in Claude/Gemini/Copilot sessions with guardrails off. Worktrees are the only isolation and they are not a security boundary. **Verified in code.**
- **No PR-time test CI.** Only `release.yml` runs `cargo test`/`nextest`, and it triggers on push to `main` — i.e. after merge. PRs get `preview-build.yml` (compile + artifact) and `blob-size-policy.yml` only. Regressions are caught at release time, not review time.
- **Bus factor 1.** One human maintainer drives the fork; the rest of recent commit volume is merged upstream authorship and automation.
- **No fork-specific security disclosure path.** `SECURITY.md` is still upstream's, routing reports to OpenAI's Bugcrowd program and OpenAI's docs. Fork-introduced vulnerabilities (browser control, sub-agent spawn, bridge, postinstall) have no owner-declared reporting channel.
- **The fork is behind upstream on architecture.** ~79 crates present in the mirrored `codex-rs/` are absent from the fork's live `code-rs/` — including upstream's `memories`, `hooks`, `core-plugins`, `code-mode`, `connectors`, `keyring-store`, and `agent-graph-store`. Divergence is being managed by hand-picked backports, which is a growing maintenance debt, not a solved problem.
- **Postinstall is heavyweight and the fallback download is unverified.** ~800 lines of Node that resolve platform triples, manage a per-user binary cache, and manipulate bin shims. The GitHub-release fallback (`releases/download/v${version}/${archiveName}`) has no checksum or signature verification in the script — the normal path is the npm optional platform package, but the fallback exists.
- **Auto-upgrade escalates to sudo.** When enabled, it runs `npm install -g @just-every/code@latest` and, on failure, retries as `sudo -n` (`updates.rs:281-296`). Off by default; unacceptable if ever turned on.
- **Browser integration reaches into real sessions.** `/chrome` scans `ps aux` for any Chrome with `--remote-debugging-port` and attaches — that means logged-in cookies and sessions, on top of the internal headless mode.
- **README pushes a broad install footprint.** The optional-agents section instructs users to `curl -fsSL https://antigravity.google/cli/install.sh | bash` and globally install four vendor CLIs. Each is its own supply-chain decision.
- **Binary-name collision was observed at review.** `code` resolved to VS Code; `coder` avoided that naming collision.
- **Hype calibration.** README's feature list is **verified** against real implementations — this is not a claims-only repo. The `/solve` "fastest preferred" claim cites arXiv 2505.17813 but ships no benchmark of its own; treat orchestration-quality claims as **plausible, unmeasured**.

## Integration ideas

1. **Patch-validation harness → OMX/Hermes.** Port the shape, not the code: a per-patch validator registry, functional vs stylistic grouping, a tool allowlist, and a per-tool timeout, wired into the Codex worker lane's completion gate.
2. **Review-in-a-separate-worktree.** A background reviewer on a ghost commit, in its own worktree, that reports findings as non-blocking notes. Applicable to supervised worker lanes and the reference stack's "verify, don't trust" doctrine.
3. **Proxy-mediated key isolation for agentic CI.** `issue-code.yml`'s pattern — run a local responses proxy, hand the agent `OPENAI_API_KEY="x"` and a loopback `OPENAI_BASE_URL` on port 5057 with a `/v1` endpoint — is a clean way to let an agent run in CI without ever holding the real key.
4. **`PROTECTED_GLOBS` for agent PRs.** Refuse agent edits to `.github/**`, lockfiles, and `package.json` by policy. Cheap, and it closes the most obvious agent-PR escalation path.
5. **Collision-aware `doctor`.** Enumerate every same-named binary on PATH with versions and package-manager provenance, then tell the user exactly which uninstall command to run. Worth copying into SStack's own doctor surfaces.
6. **Explicitly do not adopt:** the sub-agent launch model. If the operator ever wants cross-vendor fan-out, it must go through supervised lanes with permissions intact, not bypass flags.

## Alternatives / related repos

- [Yeachan-Heo/oh-my-codex](Yeachan-Heo--oh-my-codex.md) — the better shape for the same goal: an overlay *on* Codex under Hermes supervision, rather than a fork that replaces it.
- [can1357/oh-my-pi](can1357--oh-my-pi.md) — coding-agent harness benchmark with LSP/DAP and provider breadth.
- [ultraworkers/claw-code](ultraworkers--claw-code.md) — another Rust coding agent in the Codex-derived lineage.
- [fivetaku/fablize](fivetaku--fablize.md) — verification/completion gating patterns that pair with the validation harness idea.
- [nrslib/takt](nrslib--takt.md) — declarative multi-agent coordination with guardrails, the safer counterpart to `/plan` `/solve` `/code`.
- [EveryInc/compound-engineering-plugin](EveryInc--compound-engineering-plugin.md) — the other Every-adjacent repo already tracked.
- [Agent Workflows / Coding Harnesses comparison](../comparisons/agent-workflows-coding-harnesses.md).

## Review candidates and context

- Refresh trigger: revisit if the sub-agent launch model stops disabling downstream safety layers, if PR-time test CI appears, or if a second maintainer joins.
- Pattern distillation (validation harness, review worktree, CI key proxy, protected globs) belongs in SStack/OMX doctrine — promote to a GitHub Issue if it becomes real work rather than tracking it here.
