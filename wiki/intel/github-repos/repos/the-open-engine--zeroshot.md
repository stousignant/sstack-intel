---
title: the-open-engine/zeroshot
type: repo-intel
source: https://github.com/the-open-engine/zeroshot
category: agent-orchestration
status: deep-analyzed
usefulness_score: 81
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-09-23
license: MIT
---

# the-open-engine/zeroshot

> Reference-stack evaluation as reviewed 2026-09-23; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- Usefulness score: `81/100` — unusually concrete typed workflow, independent-verifier, durable-event, and fail-closed delivery semantics, offset by substantial overlap with Hermes/SStack, incomplete restart recovery, advisory local isolation, and extreme release churn.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-09-23:** `reference-only`.
- Confidence: high. README claims were checked against current source, tests, protocol fixtures, releases, and security/maintenance files.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Strong fit with the reference stack’s deterministic workflow, explicit authority, proof-contract, and provider-neutral worker direction; poor fit as another cockpit, task store, or knowledge layer. |
| Leverage | 21/25 | Graph verification, executor-reviewer separation, durable events, and exact delivery receipts could reduce bespoke orchestration work. |
| Reuse readiness | 15/20 | Native binaries, npm delivery, Docker target, Python SDK, versioned docs, generated schemas, and examples exist; integration and security review remain non-trivial. |
| Maturity / trust | 11/15 | MIT, active CI, protected main, immutable tags, checksummed artifacts, and extensive tests; offset by youth, concentrated maintenance, high breaking churn, and incomplete security automation. |
| Differentiation | 14/15 | The typed graph—not an agent prompt—owns transitions, bounds, repair, and delivery; exact-receipt settlement is stronger than ordinary multi-agent wrappers. |
| **Total** | **81/100** | High-value pattern source; premature active-stack adoption. |

## Verdict

Zeroshot is worth preserving as a high-signal coding-orchestration reference, not installing as a second active runtime. Its strongest contribution is a typed, statically admitted graph in which implementers, acceptance reviewers, code reviewers, repair workers, and delivery are separate bounded nodes. This maps directly to Hermes/SStack's desired evidence-supervised execution model. Hermes should remain the cockpit and final verifier; GitHub should remain commitment and delivery truth; SStack should own portable policy; Zeroshot is best treated as an optional future subruntime only if a bounded comparison proves that it reduces supervision or state reconstruction.

## What it is

Zeroshot is a Rust-based software-change orchestration engine. It materializes tasks into explicit typed graphs, binds graph nodes to Codex, Claude Code, or GitHub Copilot runtimes, stores ordered run events in SQLite, runs independent acceptance and code-verification branches, routes rejection into bounded repair, and optionally delivers accepted work through Git and GitHub policy gates.

The current native product is a hard cutover from the former Node.js runtime. The npm package is now a binary-delivery shim rather than the runtime itself.

## Verified architecture

### Authored graph owns control flow

- `zeroshot/src/native_v2_templates.rs` builds the default software-change graph from typed `Seq`, `Choice`, `Par`, `Loop`, `Step`, `Verifier`, `Succeed`, and `Fail` nodes.
- The implementation/review loop is bounded to ten iterations.
- Acceptance and code-review verifiers run as explicit parallel branches and join with `all`; both typed `accepted` signals are required before delivery or success.
- Rejection routes to a named repair worker rather than letting the implementing agent declare itself done.
- `zeroshot/src/native_v2_admission/validation.rs` checks bindings, node kinds, attempt limits, environment bounds, delivery-node count, and delivery contracts before execution.
- `docs/reference/cluster/graph.md` declares the public Rust protocol types authoritative and describes compilation into bounded `CompiledGraphIr`.
- `crates/openengine-cluster-server/tests/graph_verifier.rs` and the positive/negative fixtures under `protocol/openengine-cluster/v1/fixtures/` provide executable evidence that this is more than a README diagram.

### Executor and verifier separation

- Implementation, acceptance verification, code verification, review repair, and delivery repair use distinct worker references.
- Runtime plans can bind nodes to different harnesses, providers, models, effort levels, sessions, and connections.
- Verifier results are typed signals plus diagnostics; prose does not choose the next graph edge.
- “Independent” means separate graph roles and executions, not necessarily a different model/provider or hard local filesystem isolation.
- Local verifier read-only behavior is instruction guidance. Hosted verifiers receive disposable copies and distinct identities; `zeroshot/src/native_v2_capsule/tests/filesystem.rs` tests private verifier homes, separate UIDs, and denied writes to the writer workspace.

### Durable state, with an important limit

- `zeroshot/src/v2_run_ledger/sqlite.rs` stores admitted runs, snapshots, ordered events, idempotency keys, digests, and cursors in SQLite transactions.
- `zeroshot/src/v2_run_ledger/state.rs` rejects invalid state transitions such as post-terminal events, duplicate dispatch, completion of inactive nodes, and terminalization while executions remain active.
- `zeroshot/src/native_v2_observability/tests/replay.rs` tests bounded gap-free cursor replay and resumed terminal streams.
- This currently supports durable history, observation resume, and detaching while the controller remains alive. It is **not** Temporal-style restart recovery: `docs/concepts/targets.md` says restarted targets retain history but mark interrupted runs as lost.
- Workspace checkpoint recovery remains proposed in draft PR [#1142](https://github.com/the-open-engine/zeroshot/pull/1142), not shipped behavior as of this review.

### Provider integration

- `docs/concepts/runtimes-and-connections.md` documents supported harness/provider pairs and admission-time rejection of known-incompatible combinations.
- `zeroshot/src/native_v2_codex/command.rs` owns structured output, model/effort configuration, session resume, and OpenAI/OpenRouter/Bedrock/gateway modes.
- `zeroshot/src/native_v2_claude/command.rs` uses streaming JSON, JSON Schema, explicit model selection, and optional session resume.
- The Docker target pins Codex, Claude Code, GitHub Copilot, and GitHub CLI versions. GitHub CLI downloads are checksum-verified.
- This is deeper than merely shelling out: Zeroshot owns arguments, structured outputs, session identifiers, environment projection, cancellation, and provider-specific authentication constraints.

### Delivery is a first-class verified node

- Both acceptance and code verifiers must approve before delivery starts.
- Admission permits at most one graph-visible delivery node and validates its typed contract.
- `zeroshot/src/native_v2_delivery/github/policy.rs` evaluates PR identity, required checks, reviews, conflicts, merge policy, merge queue, freshness, and missing contexts.
- `zeroshot/src/native_v2_supervisor/tests/delivery_gate.rs` requires an exact durable delivery receipt and prevents success while a writer remains active or a later writer could invalidate the evidence.
- Stale, missing, or inline-only receipts fail as `delivery_unconfirmed`.
- CI or conflict failures route back through repair and review rather than bypassing verification.

## Reusable intelligence

1. **Make authored structure—not agent judgment—the control plane.** Workers may produce evidence, but only verified typed signals should advance the workflow.
2. **Separate implementer, acceptance verifier, code verifier, and repair authority.** A verifier should diagnose; it should not silently mutate the candidate it is judging.
3. **Give delivery the same evidence standard as implementation.** A PR URL or claimed push is not completion; require a durable exact receipt tied to the accepted candidate.
4. **Prevent last-writer races.** Successful settlement should be impossible while another writer is active or can invalidate the proof.
5. **Use bounded cursor replay and idempotent submissions.** Observation clients should reconnect without replaying an unbounded transcript or duplicating work.
6. **Describe trust boundaries honestly.** Local same-user execution, contained self-hosted execution, and hosted execution provide materially different guarantees.

## Fit with Hermes / SStack

| Concern | Hermes / SStack | Zeroshot | Disposition |
|---|---|---|---|
| Cockpit and governance | Hermes, Discord/mobile approval, SStack policy | CLI/UI/ACP profiles and run history | Keep Hermes; avoid a competing authority surface. |
| Worker lanes | Hermes tools, delegation, isolated sessions, Codex/Nyx lanes | Typed Codex/Claude/Copilot bindings | Distill adapter and evidence semantics. |
| Workflow definition | Skills, scripts, GitHub work orders, selective state machines | Typed statically verified graph | Strongest differentiated layer. |
| Verification | Independent-context discipline and proof bundles | First-class verifier signals and repair loops | Distill contract; do not overstate local isolation. |
| Durable state | GitHub work truth, explicit checkpoints, optional operational sidecars | SQLite events and cursor replay | Complementary attempt state, not crash-resilient durable execution yet. |
| Delivery | GitHub PR/CI/review under SStack policy | Graph-visible policy gate and exact receipt | Highest-value pattern to steal. |
| Knowledge | Second-brain, GBrain, SStack | No canonical knowledge layer | Zeroshot belongs below Hermes, never above it. |

Potential future placement:

```text
Hermes = cockpit, routing, final verification, knowledge operations
SStack = portable policy and workflow contracts
GitHub = commitment, PR, CI, and delivery truth
Zeroshot = optional bounded execution subruntime for a repeated software-change graph
Codex / Claude / Copilot = replaceable workers
```

## Maturity and maintenance

- Repository created: `2025-12-25`.
- Live metadata at review: 1,872 stars, 172 forks, Rust, MIT, not archived.
- Latest release: [v10.7.2](https://github.com/the-open-engine/zeroshot/releases/tag/v10.7.2), published `2026-09-22`, with platform archives and checksums.
- Recent CI and release runs were active; the inspected default branch had extensive Rust, Python, npm, UI, docs, target-image, protocol-fixture, and integration-test coverage.
- Contributor concentration remains material: the top three contributors accounted for roughly 93% of observed human-attributed contributions, and recent commits were more concentrated still.
- Stability risk is high: 31 canonical releases appeared in the preceding 31 days, spanning v6 through v10; v8 was an explicit hard Node-to-native cutover.

## Security and trust boundaries

### Strengths

- Runtime files name connections and required environment fields rather than embedding secret values in graphs or ledger events.
- Credential tests enforce restrictive file/directory permissions and reject broad permissions, symlinks, special files, and silent key-store downgrade.
- GitHub-delivery tests exercise clean environment projection and avoid putting tokens in command arguments or surfaced errors.
- Hosted verifier capsules test distinct identities and filesystem boundaries.

### Risks / caveats

- Local execution has the same-user trust boundary as invoking Codex, Claude, or Copilot directly and can access files or native credential stores allowed by the underlying harness.
- Local verifier non-mutation is advisory rather than a hard filesystem boundary.
- Hosted provider CLIs may use bypass-permission flags inside disposable capsules; containment therefore depends on the capsule, process, filesystem, and network boundary.
- The self-hosted direct target has no application authentication; documentation requires loopback/private-network binding or an authenticated reverse proxy.
- [upstream SECURITY.md](https://github.com/the-open-engine/zeroshot/blob/main/SECURITY.md) routes vulnerability reports to the public reporting mailbox `security@covibes.io`, an identity mismatch with The Open Engine branding that should be clarified before trust-sensitive adoption.
- No SBOM, CodeQL, OpenSSF Scorecard, Cargo audit/deny, SLSA, or provenance-policy files were found in the reviewed tree. GitHub denied access to private code-scanning and Dependabot-alert APIs, so absence of open alerts was not established.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — reference cockpit and orchestrator.
- [openai/symphony](openai--symphony.md) — compact proof-of-work and delivery-lifecycle reference.
- [coleam00/Archon](coleam00--Archon.md) — YAML workflow-engine and isolated-agent sidecar reference.
- [truefoundry/trueforge](truefoundry--trueforge.md) — sandbox/API/UI agent-runtime reference.
- [PrimeIntellect-ai/prime-agent](primeintellect-ai--prime-agent.md) — continual-harness and long-running autonomy reference.
- [Agent Workflows / Coding Harnesses Repo Comparison](../comparisons/agent-workflows-coding-harnesses.md).

## Evidence checked

- Repository, metadata, releases, contributors, workflows, and default-branch contents: https://github.com/the-open-engine/zeroshot
- README and versioned documentation.
- `docs/concepts/execution.md`
- `docs/concepts/runtimes-and-connections.md`
- `docs/concepts/targets.md`
- `docs/getting-started/first-run.md`
- `docs/reference/cluster/graph.md`
- `docker/zeroshot-target/README.md` and `docker/zeroshot-target/Dockerfile`
- `zeroshot/src/native_v2_templates.rs`
- `zeroshot/src/native_v2_admission/validation.rs`
- `zeroshot/src/v2_run_ledger/{sqlite.rs,state.rs}`
- `zeroshot/src/native_v2_{codex,claude,copilot}/`
- `zeroshot/src/native_v2_capsule/`
- `zeroshot/src/native_v2_delivery/`
- `zeroshot/src/native_v2_supervisor/`
- `zeroshot/src/native_v2_target/controller_authority/credentials/`
- Protocol fixtures and graph-verifier, admission, delivery, replay, capsule-filesystem, credential, and release-contract tests.
- `Cargo.toml`, `zeroshot/Cargo.toml`, `package.json`, CI/release workflows, Dependabot config, `CONTRIBUTING.md`, `SECURITY.md`, and `LICENSE`.
- No local installation or runtime smoke test was performed because the evidence supports pattern distillation rather than present adoption, and a meaningful run would consume provider subscriptions and touch a target repository.

## Evaluation boundary

- Opinionated reference-stack fit is retained here; it does not establish adoption.
- Evaluation only: no installation, sandbox execution or runtime adoption was established by this review.

## Review candidates

1. **Delivery-receipt gate** — compare Zeroshot's exact-receipt and last-writer rule with current SStack delegated closeout. Promote only if a real PR flow can report success against stale delivery evidence.
2. **Minimal typed workflow schema** — consider only `step`, `verifier`, `choice`, bounded `loop`, and terminal nodes. Promote only when a repeated Hermes/domain-specific workflow is demonstrably hard to audit or resume with skills/scripts.
3. **Verifier authority contract** — define fresh-session, alternate-model/provider, read-only-copy, and repair-prohibition choices. Promote only if a golden eval shows current same-context/workspace review missing material defects.
4. **Watch PR #1142** — reassess when restart recovery is merged, released, documented, and failure-injection tested outside maintainer claims.
5. **One-repository bakeoff** — Zeroshot beneath Hermes versus the current issue/worktree/verifier path. Promote only if it reduces supervision or state reconstruction without becoming another cockpit, task store, credential authority, or knowledge layer.

## Commitment disposition

Not promoted to GitHub Issues or Project 2. The review candidates remain non-binding because no current bottleneck or measured failure justifies integration work yet.
