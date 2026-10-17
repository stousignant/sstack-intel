---
title: pingdotgg/t3code
source: https://github.com/pingdotgg/t3code
created: 2026-10-04
updated: 2026-10-04
type: repo-intel
tags: [coding-agents, remote-access, agent-ui, authorization, event-sourcing]
category: coding-tools
status: deep-analyzed
usefulness_score: 80
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-04
license: MIT
---

# pingdotgg/t3code

> Reference-stack evaluation as reviewed 2026-10-04; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

**80/100 — distill-pattern; medium confidence.** A substantial open-source, multi-provider coding-agent control surface with useful remote-environment ownership, scoped authorization, and durable-intent semantics. Direct adoption requires a separately scoped isolated trial and security review; this review did not install or run it.

## Scorecard

Evidence-informed judgment, not a benchmark or measured productivity gain.

| Factor | Points | Evidence |
|---|---:|---|
| Stack fit | 20/25 | Local execution and provider adapters suit existing coding-agent workflows, but another control surface adds overlap. |
| Leverage | 22/25 | Phone/web control and clear remote-environment boundaries can reduce operator friction. |
| Reuse readiness | 16/20 | MIT source, release packages, user/internal docs; useful operation needs authenticated providers and host setup. |
| Maturity/trust | 10/15 | Active development and auth tests; early product, nightly churn, powerful host-control surface, no runtime validation here. |
| Differentiation | 12/15 | Open cross-provider and multi-client boundary; less differentiated as a single-provider coding UI. |

## Verdict

Preserve as a design reference and watch the stable product. The pinned README advertises Claude Code, Codex, Cursor, Grok Build, OpenCode, and Google Antigravity across web, Electron desktop, and iOS/Android. This is not merely a Codex wrapper. The execution host owns provider processes, Git, files, terminals, credentials, and durable state; clients operate it through authenticated RPC. That locality is useful, but remote terminal access is a consequential host capability, not an isolated chat session. [Sources: [README](https://github.com/pingdotgg/t3code/blob/efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448/README.md), [architecture](https://github.com/pingdotgg/t3code/blob/efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448/docs/internals/overview.md)]

## Reusable intelligence

1. **Keep execution with the workspace-owning environment.** Clients must not substitute their local filesystem or credentials. Environment identity persists independently from endpoint changes; network routes do not decide execution ownership. Shared client-runtime logic prevents web/mobile reconnection behavior from diverging. [Sources: architecture above; [remote architecture](https://github.com/pingdotgg/t3code/blob/efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448/docs/internals/remote.md)]
2. **Authentication is not authorization.** The inspected scope map is typed against every RPC method, rejects unknown methods, and checks granted scopes before handler execution. Terminal operations require a dedicated scope. This is an implementation-backed pattern, not just a documentation claim. [Source: [RpcAuthorization.ts](https://github.com/pingdotgg/t3code/blob/efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448/apps/server/src/auth/RpcAuthorization.ts), especially lines 173–181 and 207–233]
3. **Normalize providers at adapters.** Architecture docs put provider-specific behavior behind normalized command/event interfaces rather than throughout orchestration and UI. This review did not exercise all six integrations. [Source: architecture, lines 40–42]
4. **Commit intent before effects; distinguish accepted from completed.** Architecture docs describe one transaction for events, projections, command receipts, and outbox effects, followed by an effect worker. An acknowledgment means committed intent, not finished provider work. Lost-provider effects require recovery rather than blind replay. This transaction/recovery behavior is documented, not independently fault-tested here. [Source: architecture, lines 53–71]
5. **Separate provider completion from follow-up settlement.** Checkpoint/diff work may finish after the provider turn. Hidden Git refs preserve workspace checkpoints without adding branch commits; rollback must coordinate conversation and filesystem state. [Source: architecture, lines 73–85]

## Evidence checked

Pinned shallow clone: `efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448`. Public immutable citations above identify the reviewed source; local research artifacts are not dependencies.

- README and `docs/internals/{overview,remote}.md`, `docs/user/remote-access.md`.
- `apps/server/src/auth/{EnvironmentAuthPolicy,RpcAuthorization}.ts` and their two test files.
- Selected first 260 lines of `orchestration-v2/RunExecutionService.ts`; selected terminal environment/spawn/lease sections in `terminal/Manager.ts`.
- Parent independently verified the pinned clone, README, architecture, RPC fail-closed middleware, and PTY spawn excerpt. Additional parent inspection included root `AGENTS.md` and permission-mode docs.
- GitHub API on October 4, 2026: **25,123 stars, 6,508 forks, MIT**, latest push `2026-10-04T22:06:13Z`. Latest stable API release checked: **v0.0.45, October 2, 2026**. Inspected main corresponds to nightly `v0.0.46-nightly.20261004.2657`; stable and nightly are not interchangeable.
- Adoption signal: pinned `AGENTS.md` claims over **400,000 users**. This is project-reported, not independently verified. Star/fork counts indicate attention, not verified usage or star-growth velocity. No claim of a verified GitHub Trending placement.
- Tests inspected: auth-policy selection, exact RPC method coverage, and denial before unauthorized handler execution. **Tests were not run.** No dependencies installed, upstream code executed, providers contacted, or installer run. No repomix generated: focused source reads were sufficient for this bounded reference verdict.

## Strengths

- Explicit environment ownership and multiple client surfaces, rather than a browser that silently mixes local and remote state.
- Concrete typed method-to-scope authorization and test coverage structures.
- Transaction/outbox and completion/settlement distinctions worth studying independently of UI adoption.
- MIT licensing and a substantial implementation; README openly warns that the product is early and users should expect bugs.

## Risks / caveats

- **Host-shell boundary:** `terminal/Manager.ts:2165–2203` invokes the PTY adapter with a chosen shell, session working directory, and server-derived environment. The reviewed environment builder copies most server environment variables. No OS-sandbox or approval wrapper was visible in this path. Provider-agent sandbox settings must not be assumed to constrain this independent terminal path. This is a bounded observation, not proof that the whole app lacks safeguards. [Source: [Manager.ts](https://github.com/pingdotgg/t3code/blob/efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448/apps/server/src/terminal/Manager.ts)]
- **Remote capability scope:** the inspected authorization map is method/scope-based; this review did not prove repository/thread ACLs or exhaustively audit token issuance, secrets storage, path validation, relay infrastructure, or revocation.
- **Pairing secrets:** user docs treat pairing URLs/codes as password-equivalent and distinguish revoking a pairing link from revoking an established device session. Private-network reachability is not authorization. [Source: [remote-access guide](https://github.com/pingdotgg/t3code/blob/efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448/docs/user/remote-access.md)]
- **Permission defaults matter:** user docs distinguish Full access from supervised/approval modes, place new threads in Full access unless configured otherwise, and note that existing threads retain their mode. Provider enforcement varies; UI mode names are not proof of a common sandbox. [Source: [permission modes](https://github.com/pingdotgg/t3code/blob/efecd3cf8bcec3d1891b5f5a27dc2f6d797c6448/docs/user/permission-modes.md)]
- **Supply chain and churn:** README recommends remote script piping and offers stable/nightly packages. Installers were not executed. Pin and inspect artifacts before any trial. No `SECURITY*` file was found in the inspected checkout; this does not establish absence of external security processes.

## Alternatives / related repos

- [siteboon/claudecodeui](siteboon--claudecodeui.md) — related mobile/web coding-agent control surface; compare licensing and host-execution boundaries before a trial.
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — general assistant/orchestrator category, not identical to a multi-provider coding UI. Preserve the distinction rather than treating a GUI as a complete runtime replacement.
- Provider-native coding clients are the baseline when one provider is sufficient. T3's value proposition is cross-provider/open control and explicit remote environments. This note makes no exhaustive or time-sensitive feature-parity claim about commercial peers.

## Evaluation boundary

This note records reusable evaluation evidence, not confidential operating policy, runtime installation or project state.

## Review candidates

1. **Scope-map completeness:** review whether a remote-control API needs a typed exhaustive capability map and denial-before-handler tests. Promote only after demonstrating a concrete existing gap.
2. **Intent versus completion receipts:** compare documented outbox/settlement semantics with an existing workflow's retry failures. Promote only when reproducible failure evidence identifies a target.
3. **Isolated UI trial:** consider only if cross-provider phone control is a real unmet need; require a disposable host/project, least-privilege pairing, explicit permissions, and no canonical credentials or vault exposure.

## Commitment disposition

Not promoted. No implementation issue, installation, runtime adoption, scheduled monitoring, or remote-access configuration was authorized by this ingest.
