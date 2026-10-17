---
title: truefoundry/trueforge
type: repo-intel
aliases:
  - trueforge
  - TrueForge
  - "GitHub repo: truefoundry/trueforge"
source: https://github.com/truefoundry/trueforge
category: agent-runtime
topics: [github-repo, agent-harness, agent-runtime, mcp, sandbox, agent-ui]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-08-19
license: MIT
---

# truefoundry/trueforge

> Reference-stack evaluation as reviewed 2026-08-19; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — unusually complete and well-tested for its age, but most context/runtime patterns overlap capabilities Hermes already has; the strongest novel value is sandbox hardening plus an HTTP/SDK/UI product surface.
- **Recommendation:** `distill-pattern` — keep Hermes as the reference stack’s primary runtime; mine TrueForge's typed agent-spec, turn-event, approval, MCP OAuth, sandbox, and embeddable-UI contracts rather than adopting a second control plane.
- **Usage observed 2026-08-19:** `reference-only`. inspected and built in a disposable clone; no runtime installation or configuration was established by this review.
- **Confidence:** `high` for architecture/build quality and the fit judgment; `medium` for production maturity and benchmark claims because the public repo is less than a month old and no credentialed end-to-end run was performed.
- **Review candidate:** Revisit when Hermes needs a stable external agent API/embeddable UI or multi-user hosted execution; otherwise borrow only concrete contracts during relevant Hermes/SStack work.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Directly overlaps Hermes skills, MCP, sessions, approvals, subagents, compaction, sandboxing, and provider routing; lacks Discord, GBrain/vault ownership, and private credentialed skill repos. |
| Leverage | 20/25 | Strong sandbox and productization reference, but adopting it would split runtime and operating knowledge where deferred tools, code execution, and output control already exist in Hermes. |
| Reuse readiness | 17/20 | MIT, published npm packages, local SQLite mode, Docker/Helm, docs, SDK, tests, and a clean build; meaningful features still require model credentials and sandbox/provider setup. |
| Maturity/trust | 11/15 | Company-backed, active multi-contributor development, CI, security policy, 1,484 passing tests, and release provenance; still four weeks old, pre-1.0, internally driven, and missing supply-chain security gates. |
| Differentiation | 14/15 | SRT-backed local sandboxing, typed HTTP/SDK/UI surface, OIDC-hosted mode, resumable turns, user-scoped MCP OAuth, and local/hosted scaling are real differentiators. |
| **Total** | **82/100** | High-value architecture source; wrong time to add as a parallel active runtime. |

## Verdict

TrueForge is not vaporware. The code implements the advertised agent loop, deferred MCP tools, per-tool approvals, dynamic subagents, context compaction, oversized-result offloading, skills mounted into sandboxes, persistent session/turn stores, local and hosted deployment modes, an SDK, and an embeddable UI. Nyx's independent `claude -p` pass ran 1,484 tests across core/server/UI plus the published CLI; all passed. The catch is strategic rather than technical: nearly all agent-runtime value overlaps the reference [Hermes Agent](NousResearch--hermes-agent.md) stack, and Hermes already has deferred tool loading, bounded programmatic tool use, large-output control, skills, delegation, and compaction. Treat TrueForge as a sandbox/API/UI design oracle, not a migration target.

## Reference-stack relevance

- **Agent productization:** TrueForge shows a coherent way to expose one harness through chat, HTTP API, TypeScript SDK, and embeddable UI. That is useful if Hermes capabilities ever need to become a product or a stable app-facing service.
- **Typed runtime policy:** Its inline `AgentSpec` makes iteration limits, tool selection, approval rules, sandbox access, subagents, compaction, large-result handling, UI, and user questions explicit and serializable.
- **Security architecture:** Local sandbox commands get a curated environment, deny-by-default filesystem reads, root-scoped writes, and an outbound-domain allowlist; remote sandbox and OAuth flows are first-class rather than bolted on.
- **Scalability reference:** SQLite/one-process local mode and Postgres + Redis hosted mode share the same API, with turn persistence, peering, cancellation, and OIDC role handling.
- **Benchmark/eval fuel:** The repo includes a reproducible-looking blind-judge harness comparing the same enterprise tasks across TrueForge, Claude Managed Agents, and DeepAgents, though its published result table remains vendor-generated evidence.

## What it is

TrueForge is a TypeScript monorepo from TrueFoundry that packages an agent execution loop as:

1. `@truefoundry/trueforge-core` — model/tool loop, sessions, capabilities, MCP, subagents, context management, sandbox abstraction, and tracing interfaces.
2. `@truefoundry/trueforge` — Hono HTTP server/CLI, SQLite or Postgres stores, Redis event/peering support, settings/catalog APIs, OIDC, MCP OAuth, local/Daytona sandbox providers, and bundled frontend serving.
3. `@truefoundry/trueforge-sdk` — generated TypeScript client and event/resource types.
4. `@truefoundry/trueforge-ui` plus `packages/frontend` — embeddable and bundled chat/settings interfaces.
5. Docker Compose and Helm deployment surfaces plus a Python benchmark harness.

The public repo was created on 2026-07-23 and had roughly 1,875 stars, 129 forks, 20 open issues, 7 open PRs, and 314 merged PRs when reviewed. GitHub showed an MIT license, 18 contributors, a 2026-08-19 push, and same-day package/chart releases. Nyx found the last 60 merged PRs were authored by TrueFoundry staff or bots, so community adoption is ahead of community governance.

## Architecture evidence

### Agent contract and execution loop

- [`packages/trueforge-core/src/agent-session/schemas/agentSpec.ts`](https://github.com/truefoundry/trueforge/blob/main/packages/trueforge-core/src/agent-session/schemas/agentSpec.ts) defines a strict, serializable agent contract with model parameters, MCP server/tool selectors, default approvals for `@write` and `@destructive`, lazy tool loading, sandbox policy, dynamic subagents, compaction, large-tool-response offloading, generative UI, questions, skills, and a bounded iteration limit.
- [`packages/trueforge-core/src/agent-session/builtinsFromSpec.ts`](https://github.com/truefoundry/trueforge/blob/main/packages/trueforge-core/src/agent-session/builtinsFromSpec.ts) wires enabled capabilities into the runtime rather than leaving them as documentation-only switches.
- [`packages/trueforge-core/src/core/runtime/DeferredTool.ts`](https://github.com/truefoundry/trueforge/blob/main/packages/trueforge-core/src/core/runtime/DeferredTool.ts) implements MCP discovery and deferred invocation, including approval propagation.
- The session/turn schemas and stores persist context, events, required actions, usage metrics, subagent threads, sandbox state, and resumable approval/tool-response messages.

### Sandbox and secret boundaries

- [`packages/trueforge/src/sandbox/local/core/hostRun.ts`](https://github.com/truefoundry/trueforge/blob/main/packages/trueforge/src/sandbox/local/core/hostRun.ts) uses Anthropic's sandbox runtime with deny-root filesystem policy, root-scoped writes, curated environment variables, dependency checks, process-group handling, output limits, and a network allowlist for Python/GitHub hosts.
- The local sandbox is substantial, but it is still a privileged host supervisor invoking `bwrap`/`socat`/`rg` on Linux and exposing selected system paths read-only. It deserves its own security review before real secrets or production workloads.
- [`packages/trueforge/src/utils/secretRedaction.ts`](https://github.com/truefoundry/trueforge/blob/main/packages/trueforge/src/utils/secretRedaction.ts) redacts API responses and safely merges redacted writebacks. Store schemas nevertheless appear to persist provider/MCP/sandbox credentials in database records; no application-level at-rest encryption was verified.
- Standalone mode binds to `localhost` by default but has no login. The README and startup banner correctly warn that it is not hardened for shared or internet-facing use.
- When OIDC is unset, auth middleware grants the local identity admin rights. The default host is loopback, but container deployments bind `0.0.0.0`; exposing a container without OIDC would expose an admin agent control plane.
- Hosted mode supports OIDC with fail-closed claim parsing and admin/user role resolution, but deployment, secret storage, TLS, database hardening, and tenant isolation remain operator responsibilities.

### Deployment and product surface

- Local mode uses one process and SQLite; hosted mode uses Postgres + Redis with Docker Compose or Helm.
- The OpenAPI, generated SDK, SSE/turn polling behavior, UI SDK, settings catalogs, and deployment charts make this more product-oriented than a terminal-only harness.
- Package manifests publish npm provenance and pin a current Node/pnpm toolchain. CI runs formatting, typechecking, linting, builds, package tests, and SQLite/Postgres store contract tests.

## README claims versus evidence

| Claim | Assessment | Evidence |
|---|---|---|
| Runs model calls, MCP tools, skills, sandboxing, approvals, context management, and session state | **Verified in code and tests** | Agent spec, capability wiring, MCP/tool selectors, sandbox providers, session stores, and core tests. |
| Supports local SQLite and hosted Postgres + Redis modes | **Verified in code/config** | `config.ts`, DB migrations/stores, Redis event subscription, Compose, Helm, CI store-contract tests. |
| Any major provider / OpenAI-compatible models | **Plausible and manifest-backed** | AI SDK dependencies for Anthropic, OpenAI, Google, Alibaba, Moonshot, and OpenAI-compatible providers; no credentialed provider run performed. |
| Sandbox keeps secrets in the harness | **Plausible with caveat** | Curated sandbox env and stored connector/provider configs; at-rest encryption was not found during this bounded review. |
| Same accuracy as Claude Managed Agents at lower cost | **Source claim with reproducibility assets** | Benchmark scripts, blind-grading method, and setup are present, but the dataset is external, results are vendor-produced, only 14 tasks × 3 trials, and no independent reproduction was run. |
| Scales to shared/production deployments | **Plausible, not production-verified here** | OIDC, Postgres/Redis, Helm, persistence, and peering exist; no load, isolation, upgrade, or disaster-recovery test was run. |

## Strengths

- The implementation is unusually complete for a repo this young; advertised capabilities map to concrete code and tests.
- Runtime policy is explicit and typed instead of being scattered across prompts and environment variables.
- Human approvals are selector-driven and default to write/destructive tool annotations.
- Deferred tool loading, large-result offloading, and compaction directly target context cost and reliability.
- Sessions, turns, events, required actions, cancellation, and polling form a clean app-facing execution contract.
- Local-first trial path is cheap: Node, one process, SQLite, localhost.
- MIT license, npm provenance, security reporting, active CI, and multi-contributor company backing improve trust.

## Risks / caveats

- **Very young and pre-1.0:** the repo is less than a month old, package versions are around `0.1.x`/`0.2.x`, and APIs may churn rapidly.
- **Parallel-runtime tax:** adopting it would duplicate Hermes providers, sessions, skills, MCP configuration, approvals, UI, and operating procedures without replacing GBrain or the canonical vault.
- **Secrets and auth:** settings hold powerful model/MCP/sandbox credentials. API redaction is present, but application-level encryption at rest was not verified.
- **Standalone/container footgun:** no login and local admin identity by default; safe only on localhost as documented. Container `0.0.0.0` binding requires OIDC or equivalent network containment.
- **Sandbox complexity:** stronger than raw host execution, but not a magic boundary. Local mode depends on host sandbox tooling and selected readable system paths; remote Daytona adds another trust/provider boundary.
- **Approval metadata dependency:** default `@write`/`@destructive` approval behavior relies on MCP tool annotations. Unannotated tools are exempt unless explicitly selected or `@all` is required.
- **Skill supply chain:** git-backed skills are limited to public GitHub/GitLab HTTPS sources, may use mutable refs, and can ship executable scripts. Private credentialed skill repositories cannot mount directly, and branch/tag pinning is recommended rather than enforced.
- **Dependency supply chain:** CI has strong format/type/build/test gates but no checked CodeQL, Dependabot, SAST, SBOM, or package-audit gate; the workspace currently uses `minimumReleaseAge: 0`.
- **Vendor benchmark:** useful methodology, but not independent proof and too small to drive a migration.
- **No end-to-end model smoke:** local verification intentionally avoided credentials and did not execute an actual agent turn, OIDC login, MCP OAuth flow, or sandbox command.

## Comparison to the reference stack

| Surface | TrueForge | Hermes/GBrain/SStack | Take |
|---|---|---|---|
| Primary interaction | Bundled web chat, HTTP API, SDK, embeddable UI | Discord/CLI/TUI/gateway cockpit | TrueForge wins for app embedding; Hermes wins for the reference stack’s assumed daily interface. |
| Agent/runtime features | Typed spec, sessions/turns, MCP, approvals, subagents, compaction, sandbox | Broad tool registry, skills, delegation, processes, browser, cron, gateway, plugins, profiles | Heavy overlap; no migration case. |
| Persistent knowledge | Session DB and public-git-backed skills | Canonical Markdown vault + GBrain + session search + compact memory | the reference stack has the stronger durable knowledge architecture; private credentialed skill repositories are not directly mountable. |
| Proactivity | Long turns and API-driven execution | Cron jobs, gateway delivery, continuable sessions, background processes | Hermes is already better aligned with proactive personal operation. |
| Hosted/team mode | OIDC, Postgres, Redis, Helm, app API | Primarily personal/local cockpit with messaging gateways | TrueForge is the stronger service/team product reference. |
| Portable personalization | Skills/config/catalogs | SStack-managed skills/config/procedures across harnesses | SStack remains the right ownership layer. |
| Product SDK/UI | First-class generated SDK and embeddable UI | TUI/gateway/plugins; less app-SDK oriented | TrueForge's clearest differentiation and best pattern source. |

## Patterns worth stealing

1. **SRT-backed local sandbox:** reuse the `@anthropic-ai/sandbox-runtime` wiring, curated environment, read/write boundaries, network allowlist, dependency preflight, and output caps if Hermes needs a hardened local code-execution substrate.
2. **Serializable agent run spec:** one validated object for model, tools, approval selectors, sandbox, subagents, compaction, output handling, and interaction capabilities.
3. **Turn-as-resource API:** durable turn state with streamed events, required actions, resume messages, cancellation, polling fallback, and aggregate usage metrics.
4. **Approval selector policy:** `@write`, `@destructive`, `@all`, and explicit tool names, surfaced in the API rather than buried in UI logic.
5. **Embeddable UI adapter:** separate the reusable UI package from the server and bundled frontend.
6. **Benchmark harness shape:** identical prompts/tools, blind criteria-only judge, resumable cells, hard timeouts, cost normalization, and multiple trials.

TrueForge's deferred schema discovery, Code Mode, large-result offloading, subagents, and compaction are strong implementations, but they are validation/comparison material rather than net-new ideas for an environment where Hermes already exposes deferred tools, `execute_code`, output reduction/offloading, delegation, and context compression.

## Evidence checked

- Primary repository: https://github.com/truefoundry/trueforge
- Disposable clone: a disposable source checkout
- Independent review produced through subscription-authenticated `claude -p` with API/provider environment variables unset; its executed results are retained below.
- Inspected commit: `cc1e831635aa2071235f647333cefbd83922675a`
- GitHub metadata via `gh repo view` and REST APIs on 2026-08-19.
- Key files: `README.md`, `SECURITY.md`, `package.json`, `.github/workflows/ci.yml`, package manifests, agent-spec/capability/runtime files, session/store schemas and tests, local sandbox implementation, auth/config, secret redaction, Docker Compose, Helm catalog, OpenAPI/SDK/UI surfaces, and `benchmark/README.md` plus scripts.
- DeepWiki was linked by the project but not used as primary evidence.
- No repomix pack was generated; the shallow source clone was small enough for selective direct inspection.

## Local verification

Executed in the disposable clone without model/API credentials:

```text
pnpm install --frozen-lockfile
→ PASS in 5s; 1,300 workspace packages installed from the lockfile

pnpm test:trueforge-core
→ PASS: 38 suites, 374 tests passed, 1 skipped

pnpm typecheck && pnpm build
→ PASS: all workspace typechecks and production builds completed
→ Caveat: frontend build emitted large-chunk warnings, including multi-megabyte generated bundles/workers

Nyx independent smoke pass
→ PASS: core 374, server 273, UI 837 tests; 1,484 total passing
→ PASS: npx @truefoundry/trueforge@0.1.4 --help
```

The build left the cloned repository's tracked working tree clean. A full agent smoke was not run because it requires model credentials and configuration; the Docker smoke additionally expects a populated `.env` and would exercise external-service boundaries beyond this ingest.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — the reference stack’s primary agent runtime and cockpit; keep as the center of gravity.
- [openclaw/openclaw](openclaw--openclaw.md) — broader gateway/product architecture reference.
- [can1357/oh-my-pi](can1357--oh-my-pi.md) — coding-agent harness benchmark with stronger IDE/LSP/DAP differentiation.
- [OpenHands/OpenHands](OpenHands--OpenHands.md) — mature agent platform/SDK/UI benchmark.
- [NVIDIA/OpenShell](NVIDIA--OpenShell.md) — stronger dedicated containment/security substrate reference.

## Review guidance

- No new executable task is justified now. Revisit at v1.0, when private credentialed skill repos ship, or when a concrete Hermes gap appears around local sandboxing, an external agent API, embeddable UI, hosted multi-user execution, or typed run/turn contracts.
- When that trigger appears, compare the narrow TrueForge component or contract against extending Hermes via plugin/MCP/ACP rather than evaluating a wholesale runtime migration.
