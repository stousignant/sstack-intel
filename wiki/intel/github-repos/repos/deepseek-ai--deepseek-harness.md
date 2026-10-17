---
title: deepseek-ai/deepseek-harness
type: repo-intel
source: https://github.com/deepseek-ai/deepseek-harness
category: coding-agent-harness
status: deep-analyzed
usefulness_score: 75
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-08-17
license: MIT
---

# deepseek-ai/deepseek-harness

> Opinionated reference-stack evaluation, reviewed 2026-08-17. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `75/100` — The most rigorously engineered open agent harness reviewed so far, and the strongest available reference for plugin-composed harness architecture and gate-enforced agent process; but it remains a days-old developer preview that would add another full agent runtime to a Hermes-first stack.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-08-17:** `reference-only`.
- **Confidence:** `high`.
- **Review candidate:** Keep mining patterns, not runtime dependencies. The first GitHub prerelease (`dsh-v0.1.0-rc.7`) now exists, but the compatibility trigger has **not** fired: it is still an RC under the explicit `SESSION_FORMAT_VERSION: 0` / no-compatibility stance. Do **not** stand up `dsh` as a runtime. Revisit only when a release carries an actual compatibility promise, or if the Claude Code / Codex subagent bridges become the cheapest supervised multi-runtime lane.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 18/25 | Pattern fit is exceptional and it is not DeepSeek-locked (`llm-pi-ai` routes Anthropic/OpenAI/any OpenAI-compatible gateway; `subagent-claude-code`, `subagent-codex`, `hooks-claude-code`, `hooks-codex` bridge the reference coding-worker lanes). Runtime fit is poor: Hermes is the reference primary runtime and Claude Code/Codex are the reference coding-worker lanes. |
| Leverage | 19/25 | Very high durable leverage on harness self-improvement through its process layer; near-zero immediate time saved, and a real risk of consuming weeks. |
| Reuse readiness | 13/20 | MIT, published to npm, `npx` works with no build (verified), and a first GitHub prerelease now exists. But it remains a developer preview with an explicit breaking-change warning, 219 packages, and a pnpm + Node ^22.19/>=24 monorepo. |
| Maturity/trust | 11/15 | 640 test files, per-file **100%** coverage threshold, 34 `verify-*` gates, keyless snapshot replay, real-API e2e, MIT + THIRD_PARTY_NOTICES, safe defaults, opt-in telemetry. Offset by days of public life, `0.1.0-rc.7`, closed contribution, and squashed public history. |
| Differentiation | 14/15 | Nothing else in the 177-repo corpus does Cordis-style reversible-effect plugin composition, capability seams, or the model-visible⟺logged invariant. |
| **Total** | **75/100** | Best-in-class harness *engineering reference*; wrong thing to adopt as a runtime right now. |

## Verdict

DeepSeek Harness is a well-funded lab's MIT harness product. Its plugin-based architecture—agent loop, model adapter, tool registry, and session log—makes behavior changes compositional rather than privileged-core patches and is worth studying. Direct adoption remains a poor default: it is a *developer preview* whose `AGENTS.md` warns "**THERE WILL BE COMPATIBILITY-BREAKING CHANGES**" and pins `SESSION_FORMAT_VERSION` at `0` "with no compatibility promise"; external pull requests are not accepted and Issues/PRs are disabled; and running it would add a full runtime beside Hermes and coding-worker lanes. Treat it as a design reference and distill process patterns into existing procedures. Its CONTRIBUTING.md describes it as "an idea, an official showcase, and a source of inspiration, but not a mandate from us."

## Workload fit

- **It is the missing worked example for [harness engineering](../../../concepts/ai-engineering/harness-engineering.md) at production scale.** Every principle already on that page — deterministic nodes for deterministic tasks, progressive disclosure, promote harness changes like state transitions — appears here as executed, gate-enforced code rather than as advice.
- **The `.agents/` layer is a directly portable governance pattern for harness self-improvement.** 684 Agent Notes across a `proposed/implemented/rejected/archived` lifecycle, four postmortems that ask "why our process let it through" rather than "what was the fix", and 34 `verify-*` scripts that mechanically enforce the conventions. This is [self-harness](../../../concepts/ai-engineering/self-harness.md)'s promotion gate applied to a human+agent codebase.
- **It is not a DeepSeek silo.** `llm-pi-ai` routes Anthropic, OpenAI, and hand-declared OpenAI-compatible gateways by config; `subagent-claude-code` invokes the official Claude Agent SDK as a subagent provider; `hooks-claude-code` and `hooks-codex` execute existing Claude Code and Codex hook configs on DSH's interception points. That makes it the most credible "supervise my other runtimes from one harness" reference available.
- **`tool-ralph` is the Ralph loop implemented as an ordinary plugin, not a mode.** Compare it with the related [witt3rd/oh-my-hermes](witt3rd--oh-my-hermes.md) pattern: this implementation adds a bounded round cap, structured handoff validation, and an explicit refusal to treat a worker's self-report as certification.
- **The counter-signal matters as much as the signal.** Harness recursion can become infrastructure work that consumes effort without delivering useful outcomes. A 219-package harness with outstanding docs is exactly the artifact that could absorb a month and produce no income movement. Reading it is cheap; running it is not.

## What it is

`dsh` is an open-source agent harness from DeepSeek AI, built on a vendored copy of [Cordis](https://github.com/cordiverse/cordis), whose thesis is that **everything is a plugin**. A running instance is a plugin tree composed at boot from ordered layers: bundles (`dsh-base`, `dsh-web-app`, `dsh-headless`) supply Cordis config rows, a profile stacks them, and user `cordis.patch.yml` files plus `--patch` overlays override any row by id. Registrations are reversible effects that unwind when their plugin unloads, so there is no privileged core to patch — new behavior mounts beside the existing plugins.

The product surfaces are a Web UI (`dsh web`, default `127.0.0.1:3080`), a headless one-shot runner, an ACP automation server, a JSON-RPC SDK, and a Python SDK with a bundled Node-free runtime. The 219 workspace packages cover the agent loop, tools, sandboxing, skills, subagents, workflows, compaction, spill, goals, plan mode, LSP, MCP, session persistence/query, and a full React client.

Two architectural ideas carry most of the design. A **capability seam** is a swappable capability with exactly three roles — Service Definition, Service Provider, Consumer — and adding a capability means designing all three; because the filesystem and subprocess providers share one execution world, pointing them at a remote sandbox moves Bash, PTY, and LSP with them, with no provider forks. The **model-visible ⟺ logged** invariant requires that anything reaching a model request be reconstructable from the append-only session log, asserted at runtime, which is what makes fork, resume, replay, transcripts, and telemetry all derivable from one stream.

## Evidence checked

- **GitHub metadata refresh** via `gh api repos/deepseek-ai/deepseek-harness`, checked 2026-08-17: `149617` stars, `15322` forks, `open_issues_count: 0`, pushed `2026-08-17T12:01:58Z`. These are launch-attention signals, not adoption evidence. Baseline license, language, contribution posture, and repository settings remain as checked on 2026-08-16.
- **Releases/tags:** first GitHub prerelease `dsh-v0.1.0-rc.7`, published `2026-08-17T12:01:58Z`, commit `99f6f02fecdb7dff40c3fbc9470f5907c29f74ca`. It is a prerelease, not a compatibility promise.
- **npm:** `npm view @deepseek-ai/dsh` on 2026-08-17 → version `0.1.0-rc.7`, `latest`/`next` both `0.1.0-rc.7`, modified `2026-08-17T13:12:50.723Z`.
- **Clone:** `git clone --depth 50` → a disposable source-inspection workspace, 110 MB. Shallow log shows PR merges up to `#2521` and `release(dsh): 0.1.0-rc.5`, but `git log --reverse` bottoms out at the single tip commit `47f9438` (2026-08-13) — the public repo is a squashed mirror of internal development (a `.gitlab-ci.yml` is present alongside `.github/`). `git shortlog -sn --all` → 32 authors, top five: Yichen Jiang (270), imccyu (228), Tianyi Cui (224), Turtle (143), _Kerman (104).
- **License verified from `LICENSE`:** MIT, "Copyright (c) 2026 DeepSeek". Third-party disclosure in `THIRD_PARTY_NOTICES.md` (15.8 KB).
- **Contribution posture from `CONTRIBUTING.md`:** "We are sorry that we cannot accept external pull requests at the moment." Feedback goes to GitHub Discussions; ecosystem contribution is via the `dsh-plugin` topic.
- **Docs read:** `README.md`, `AGENTS.md` (149 lines; `CLAUDE.md` is a symlink to it), `docs/architecture.md`, `docs/subsystems/sandbox.md`, `docs/subsystems/permission-presets.md`, `docs/subsystems/skills.md`, `docs/subsystems/goal.md`, `docs/subsystems/spill.md`, `docs/subsystems/session-telemetry.md`, `docs/postmortem/README.md`, `.agents/notes/README.md`, `.agents/skills/dsh-code-review/SKILL.md`, `packages/llm/llm-deepseek/README.md`, `packages/llm/llm-pi-ai/README.md`, `packages/workflow/tool-ralph/README.md`, `packages/extensions/tool-cordis/README.md`, `packages/subagent/subagent-claude-code/README.md`, `packages/hooks/hooks-claude-code/README.md`, `CONTRIBUTING.md`, `BENCHMARK.md`.
- **Package inventory:** `find packages -maxdepth 2 -mindepth 2 -type d` → **219** packages across 48 groups. Notable: `subagent/subagent-claude-code`, `subagent/subagent-codex`, `subagent/subagent-acp`, `hooks/hooks-claude-code`, `hooks/hooks-codex`, `workflow/tool-ralph`, `extensions/tool-cordis`, `sandbox/sandbox-local`, `sandbox/sandbox-windows-acl`, `spill/spill-policy`, `guard/repeat-tool-reminder`, `guard/timeout-policy`, `runtime-diagnostics/invariants`, `session-query/tool-session-query`, `web/web-search-exa`, `web/web-search-perplexity`.
- **Test/gate posture:** `find packages -name '*.test.ts'` → **640** test files. `vitest.config.ts` sets coverage `thresholds` of `statements/branches/functions/lines: 100` per file with the comment "100% or it doesn't merge". `scripts/` holds 124 TypeScript scripts of which **34** are `verify-*` gates. 15 GitHub Actions workflows including `ci.yml`, `e2e.yml`, `sandbox.yml`, `landlock-run.yml`, `pi-ai-provider-e2e.yml`, `e2b-e2e.yml`.
- **Agent Notes inventory:** `.agents/notes` holds **684** English notes — `implemented/` 507, `archived/` 143, `proposed/` 25, `rejected/` 11 — under a closed class set (`feature`, `bug-fix`, `simplification`, `architecture`, `process`, `testing`) enforced by `scripts/agent-note-tree.ts`. Eleven repo-local agent skills under `.agents/skills/`. Four postmortems under `docs/postmortem/`.
- **Smoke test 1 (no credentials):** `npx --yes @deepseek-ai/dsh@0.1.0-rc.6 --help` → exit `0`, printed the launcher usage (profiles, `--patch` overlays, `--dump-config`, `web`/`plugin` subcommands). One deprecation warning (`node-domexception@1.0.0`).
- **Smoke test 2 (no credentials):** `DSH_HOME=<tmp> npx --yes @deepseek-ai/dsh@0.1.0-rc.6 --profile headless --dump-default-config` → printed the composed plugin tree, **81** rows, saved to a disposable source-inspection workspace. Verified from that dump: default model row is `provider: deepseek-official, model: deepseek-v4-flash`; `llm-pi-ai` is mounted in the base bundle; `sandbox-local` + `sandbox-policy` + `bash-sandbox` + `pwsh-sandbox` are all present; the `permission-presets` table ships `read-only`/`workspace-write`/`danger-full-access` with `approval: ask` on the first two; the effective default is `workspace-write` + `ask` via `DSH_PERMISSION_MODE ?? 'workspace-write'`.
- **repomix:** not generated. The repository's own bilingual `docs/` tree and per-package READMEs are higher-quality evidence than a pack would be, and selective reads kept context bounded.
- **Local evidence cache:** a disposable source-inspection workspace (clone under `repo/`, config dump at `headless-config.yml`). Temporary; not vault state.

## Strengths

- **Composition instead of patching, with reversible registrations.** Every contribution goes through `ctx.effect()` / `ctx.on()` and a registry's `register()` returns its disposer, so unloading a plugin unwinds exactly what it added. `dsh --profile web --dump-config` prints the tree the machine actually boots and every printed row is overridable by id — verified against the headless profile above.
- **Capability seams are enforced as a three-role unit.** Service Definition / Service Provider / Consumer, "complete, never one role." This is why swapping the filesystem and subprocess providers relocates Bash, PTY, and LSP to a remote sandbox without forking any consumer.
- **The `model-visible ⟺ logged` runtime invariant.** A new model-visible input requires a new session event, and a runtime invariant asserts reconstructability. Replay, fork, resume, transcripts, and telemetry are all projections of one append-only log rather than parallel bookkeeping.
- **Safe-by-default execution with honest enforcement reporting.** Default preset is `workspace-write` + `ask`. The sandbox seam reports enforcement as `full` or `partial` and requires consumers needing an absolute boundary to reject `partial` — older Landlock ABIs and the Windows ACL runner's Everyone/hard-link gaps are named as current partial cases rather than papered over. Postmortem 0004 exists specifically because a partial-enforcement notice once misclassified child failures.
- **Telemetry is a mounted capability, off unless chosen.** `session-telemetry` is a seam whose only shipped provider is a verbatim OpenTelemetry pipeline; "nothing here reaches a model request", and every backend must disclose its sharing policy (`full` / `feedback-only` / `disabled`) through a required `sharing` member. No ambient phone-home in the default composition.
- **Process rigor is mechanically gated, not aspirational.** Per-file 100% coverage; `pnpm run doc-sync` runs every documentation gate; `verify-export-jsdoc`, `verify-cordis-config`, `verify-doc-budgets`, `verify-agent-note-format`, `verify-archived-agent-notes` (which pins archived notes with sidecar hashes and an append-only frozen-content manifest); "Non-trivial changes MUST include an Agent Note in the same PR."
- **The prose standard is unusually good and directly reusable.** `AGENTS.md` bans metaphor, bans narrating control flow, and requires that before writing `contract`, `boundary`, or `shape` you ask whether a more exact term exists — "write `response fields`, `JSON validation`, or `ESM exports` instead of `response shape`, `validation boundary`, or `module shape`."
- **Multi-runtime bridges are first-class, not demos.** `subagent-claude-code` deliberately omits the SDK `settingSources` option so Claude Code reads the host's normal user/project/local settings, sets `persistSession: false`, disables `AskUserQuestion`, and maps every SDK error subtype to a typed result; it reports `inheritsParentContext: false` and never copies or modifies login state.
- **Fully bilingual documentation** (English + `zh` + `.i18n.yaml` sidecars) across `docs/`, package READMEs, and Agent Notes, with translation itself gated behind explicit user invocation.

## Risks / caveats

- **Developer preview with an explicit no-compatibility stance.** `AGENTS.md` carries a "Pre-release stance: foundation over blast radius" section instructing maintainers to "rename or repackage freely", states "Backends reject old on-disk formats", and pins `SESSION_FORMAT_VERSION` at `0` "with no compatibility promise". Any local investment can be invalidated by the next `rc`.
- **A tag now exists, but stability still does not.** `dsh-v0.1.0-rc.7` is the first GitHub prerelease; the repository still declares breaking changes and no session-format compatibility promise. A tag is better release hygiene, not adoption readiness.
- **Contribution is closed and the feedback channel is thin.** Issues and pull requests are disabled on the repository (`has_issues: false`, `has_pull_requests: false`), external PRs are explicitly not accepted, and DeepSeek states it is "a very small team" that "may not be able to reply to every post" in Discussions. Users have no supported bug-report path beyond an upvote.
- **Public history is a squashed mirror.** The visible tree bottoms out at one commit dated 2026-08-13 despite referencing internal PR `#2521` and a `.gitlab-ci.yml`. Blame, bisect, and pre-release review history are unavailable, so the 640 test files and 34 gates must be trusted as artifacts rather than audited as a development record.
- **150k stars in four days is hype velocity, not adoption evidence.** Star count here reflects DeepSeek's brand, not production use. Nothing in the repo has been exercised by third parties at scale yet.
- **Weight.** 219 packages, 110 MB checkout, pnpm workspaces, Node ^22.19 || >=24, a vendored framework with its own sync procedure, and a build spanning `tsc` + `tsdown`. This is not a sidecar; it is a platform.
- **The self-referential toolset is bash-equivalent trust.** `tool-cordis` lets the model define and run code against the live runtime, and its own README says "The sandbox isolates globals but is not a security boundary … host-realm helpers make escape possible … Treat this toolset like bash access." Dynamic packages "may affect other sessions in that process." It is not in the default headless composition, and it should not be enabled casually.
- **Prompt-injection surface is the usual agent-harness one.** MCP client, `web-fetch-http`, and three web-search providers all feed untrusted text into a loop with Bash and filesystem tools. The sandbox and approval defaults mitigate this; they do not remove it.
- **Vendor gravity in defaults.** The default model row is `deepseek-official` / `deepseek-v4-flash` even in the headless profile, and `web-search-deepseek` ships in-tree. Provider independence is real but requires configuration; review this before exposing private or production data.
- **Benchmark/eval claims are absent, not merely unverified.** `BENCHMARK.md` is three lines and only tells you to run the Python SDK's `jsonrpc-agent` variant in isolated workspaces. There is no eval suite, no scored task set, and no published harness result in the repository, so any "coding-agent evaluation/training" interest has to come from the architecture, not from measurements.

## Integration ideas

- **Reuse the Agent Note lifecycle, not the tooling.** Combine baseline/reason/verification/retirement fields with a `proposed → implemented → rejected → archived` lifecycle, a closed class set and a rule that non-trivial changes carry a note in the same change. A lightweight convention may suffice; adopting the 34 gate scripts would be overbuilding.
- **Steal the postmortem framing for Hermes/LifeOS incidents.** "A bug reached a place it shouldn't have, and the interesting part is why our process let it through" plus the three-part write-when test (subtle, systemic, costly to rediscover) is a useful postmortem trigger, paired with a link to the resulting guardrail.
- **Adopt the enforcement-completeness vocabulary for containment.** `full` vs `partial` as a *reported fact*, with consumers required to reject `partial` when they need an absolute boundary, is a better model than a boolean "sandboxed" flag. This maps onto `sstack-release-containment` and the LifeOS containment policy directly.
- **Borrow the prose standard for skill and doc authoring.** The "name the exact thing instead of writing `shape`/`boundary`/`contract`" rule and the "docs state contracts, not reasoning transcripts" rule belong in `sstack-hermes-skill-authoring` and `sstack-instruction-audit`.
- **Read `tool-ralph` before writing any Hermes long-running loop.** The valuable details are the round cap as both default and ceiling, the structured handoff with a serialized size ceiling that *fails* rather than truncates, the workspace-as-authority instruction with no conversation seed, and the explicit statement that completion is "a worker reported the outcome, not independent certification."
- **Treat `hooks-claude-code` as a spec, not a dependency.** It documents which Claude Code command-hook semantics are portable across harnesses — matcher, exit-code/stdout codec, most-restrictive merge, `${CLAUDE_PLUGIN_ROOT}`/`${CLAUDE_PROJECT_DIR}` substitution. That is a useful reference when SStack hooks need to work under both Claude Code and Hermes.
- **What not to do:** do not mount `dsh` as a runtime, point it at real workspaces, enable `tool-cordis`, or build a Hermes↔DSH bridge. The pattern value is available from source inspection without runtime integration.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — the reference primary runtime; DSH is the architectural contrast (plugin composition + reversible effects vs Hermes's configured runtime), not a replacement candidate.
- [openclaw/openclaw](openclaw--openclaw.md) — the previous best gateway/plugin-manifest architecture reference at 88; DSH is stronger on composition semantics and process rigor, weaker on stability and openness to contribution.
- [witt3rd/oh-my-hermes](witt3rd--oh-my-hermes.md) — Hermes-native RALPlan/Ralph; `tool-ralph` is the same idea with bounded rounds and validated structured handoffs.
- [OpenHands/OpenHands](OpenHands--OpenHands.md) — the other mature full coding-agent platform benchmark; OpenHands has real published eval results, DSH has better architecture documentation and none.
- [fivetaku/fablize](fivetaku--fablize.md) — verification/completion harness; complements DSH's "worker report is not certification" stance.
- [chopratejas/headroom](chopratejas--headroom.md) — context-compression sidecar; DSH's `spill` seam plus `compaction-tool-result-pruner` solve the same tool-output bloat problem in-tree.
- [ai-boost/awesome-harness-engineering](ai-boost--awesome-harness-engineering.md) — the discovery map for this category; DSH is the worked implementation it points toward.
- [Harness Engineering](../../../concepts/ai-engineering/harness-engineering.md) and [Self-Harness](../../../concepts/ai-engineering/self-harness.md) — the concept pages this repo supplies production evidence for.

## Review candidates and completed evidence

- Review candidate: Extract the Agent Note lifecycle + postmortem trigger into a single SStack doctrine proposal; decide adopt-or-drop rather than leaving it as reading.
- Completed: Refresh for the first tagged GitHub prerelease (`dsh-v0.1.0-rc.7`); verdict unchanged because it carries no compatibility promise.
- Review candidate: Refresh when DSH drops the "developer preview" / `SESSION_FORMAT_VERSION: 0` stance or publishes a compatibility promise — that is the trigger that could move `reuse readiness` and `maturity/trust`.

**Refresh trigger:** a compatibility promise replacing the `SESSION_FORMAT_VERSION: 0` stance, a non-RC release with migration guidance, or neutral benchmark/adoption evidence.
