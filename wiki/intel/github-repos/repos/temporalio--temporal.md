---
title: temporalio/temporal
type: repo-intel
aliases:
  - Temporal Server
  - GitHub repo: temporalio/temporal
source: https://github.com/temporalio/temporal
category: durable-execution
topics: [github-repo, durable-execution, workflow-engine, distributed-systems, event-sourcing, golang]
status: deep-analyzed
usefulness_score: 85
recommendation: defer
usage: sandboxed
score_confidence: high
last_reviewed: 2026-09-12
license: MIT
reviewed_commit: 9ab3a9f770da20df7d94bcc0030f28eec7b0b947
latest_release_reviewed: v1.32.0
---

# temporalio/temporal

> Reference-stack evaluation as reviewed 2026-09-12; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `85/100` — a mature, differentiated durable-execution core with strong failure semantics, offset by deterministic-programming constraints and substantial self-hosting/worker-lifecycle burden.
- **Recommendation:** `defer` production adoption pending a representative application-level pilot; retain as a strong sandbox candidate when work must survive process restarts, long waits, retries, and human input.
- **Confidence:** `high` for server architecture, maturity, license, and self-hosting burden; `medium` for application fit until a real workload is exercised.
- **Scope:** this verdict evaluates the open-source **Temporal Server repository**, not a language SDK, Temporal Cloud, Temporal CLI, or Pydantic AI’s integration layer.

## Scorecard

This is a context-sensitive reuse score, not a universal software-quality score.

| Factor | Points | Notes |
|---|---:|---|
| General fit | 23/25 | Strong fit for long-running, failure-sensitive orchestration; unnecessary for short, stateless jobs. |
| Leverage | 22/25 | Replaces custom retry, timer, recovery, signal, and workflow-state machinery; requires disciplined workflow/activity boundaries. |
| Reuse readiness | 12/20 | Excellent docs and local test paths, but production use adds SDK integration, workers, persistence, security, observability, schema, and upgrade work. |
| Maturity/trust | 15/15 | Active company-backed project, MIT license, frequent releases, broad CI, extensive tests, and a large contributor base. |
| Differentiation | 13/15 | Event-history replay, durable timers, signals/updates, and worker isolation form a coherent durable-execution model; alternatives need workload-level comparison. |
| **Total** | **85/100** | Strong candidate for bounded evaluation, not an automatic infrastructure default. |

## Verdict

Temporal Server is credible infrastructure for workflows whose value depends on resuming after worker/server interruption, waiting durably, coordinating external effects, and exposing a queryable execution history. Its core abstraction is not “persist an agent object” or “rerun an entire request”: the server records workflow history while application-owned Workers replay deterministic orchestration code and execute non-deterministic I/O as Activities.[3][20] That architecture is a strong match for long-running agents, approvals, scheduled research, and multi-step tool work **if** external side effects are made idempotent and workflow-code changes are versioned. It is a poor default for ephemeral prompts or low-value background tasks because the operational and programming-model costs can outweigh the recovery value. A production decision should therefore follow a failure-injection pilot with the intended SDK and agent framework rather than the server’s happy-path quickstart.

## Current metadata snapshot

**Verified — GitHub API and local clone, captured 2026-09-12:**

| Field | Value |
|---|---|
| Repository | `temporalio/temporal` |
| Description | `Temporal service` |
| Default branch | `main` |
| Reviewed commit | `9ab3a9f770da20df7d94bcc0030f28eec7b0b947` |
| Reviewed commit timestamp | 2026-09-11 17:18:20Z |
| Stars / forks / watchers | 22,991 / 1,897 / 123 |
| Open issues / open PRs | 570 / 392 |
| Primary language | Go |
| GitHub-reported repository size | 161,722 KB |
| Created / last pushed | 2019-10-16 / 2026-09-12 |
| Latest release | `v1.32.0`, published 2026-09-11[13] |
| Published releases returned by API | 172 |
| Contributor API records | 302, including anonymous records |
| Commits in sampled 90-day window | 595 (2026-06-15 through 2026-09-11) |
| GitHub license detection | MIT[12] |
| Archived / fork | no / no |

Counts are volatile snapshots and are not quality measures. The repository is clearly active: the latest stable release was one day old at review time, and the sampled commit/release history is substantial.[1][13]

## Product and repository boundaries

### What this repository is

**Verified:** `temporalio/temporal` contains the Go source for the Temporal **server/service**. Its README explicitly redirects Workflow, Activity, and application Worker implementation to supported language SDKs.[2]

### What it is not

- **Language SDKs:** application code uses separate SDK repositories/packages. For a Python application, `temporalio/sdk-python` is the relevant client/Worker runtime, not this Go server repository.[22]
- **Temporal CLI:** `temporal server start-dev` is delivered through the separate `temporalio/cli` project. It is the recommended low-friction local server, but it is not evidence that this server repository is a single-binary production deployment.[2][14][23]
- **Temporal Cloud:** Cloud is the managed hosting option for the Temporal Service. This repository is the open-source server core; Cloud’s control plane, service operation, commercial security posture, and service guarantees must be evaluated separately.[3][14]
- **Web UI:** production binary deployment also involves the separate Temporal UI Server; the core release is not the entire operator experience.[17]
- **Pydantic AI integration:** native Pydantic AI durability is implemented and documented in `pydantic/pydantic-ai`, not here. It composes Pydantic agent runs with Temporal’s Python SDK and server.[21]

This separation matters: adopting the server does not automatically supply an agent framework, SDK Worker, UI, secure production topology, or managed operations.

## Architecture

### Execution split

**Verified:** Temporal divides the system into application-owned processes and the Temporal cluster. Application code starts/interacts with workflows through an SDK client. Application-owned Worker processes poll task queues and execute Workflow and Activity code. User code does not run inside the Temporal Server.[3]

This yields a useful security and scaling boundary: model credentials, tool credentials, filesystem access, and agent code stay in Worker infrastructure. It also creates another service class that must be deployed, observed, versioned, and scaled.

### Durable state model

**Verified:** the server uses event sourcing. Each Workflow Execution has an append-oriented Event History from which required workflow state can be recreated by replay. Workflow code must be deterministic and side-effect-free except through SDK-provided replay-safe mechanisms; Activities contain non-deterministic I/O and should be idempotent when retried.[3][20]

**Verified:** the History Service persists both Event History and a summarized Mutable State. Mutable State avoids reconstructing the full execution state on every request, while the event sequence remains sufficient to recover workflow state.[4]

**Inferred:** Temporal’s value for agent systems comes from making the orchestration decisions durable—not from making an LLM call intrinsically deterministic. Model calls, tool calls, MCP communication, database I/O, and filesystem effects belong in Activities or an equivalent integration wrapper. Their outputs can then become recorded inputs to deterministic workflow progress.[20][21]

### Server roles

The server exposes four principal internal service roles:[3]

1. **Frontend Service — verified:** external gRPC/API boundary for clients and Workers. It routes requests, applies configured authentication/authorization hooks, rate limits, and exposes health APIs.
2. **History Service — verified:** owns Workflow Execution state by shard; handles client/Worker state transitions, appends history, updates Mutable State, creates timer/transfer/visibility/replication work, and coordinates persistence.[4]
3. **Matching Service — verified:** owns partitioned Task Queues and matches Workflow/Activity tasks with polling application Workers. Task Queue partition ownership can move, and backlog metadata is persisted.[5]
4. **Internal Worker Service — verified:** runs cluster-internal background work such as replication, archival, scanners, and parent-close processing. This is not the same thing as an application Worker.

### State-transition and delivery pattern

**Verified:** History state transitions derive events, update Mutable State, and create internal tasks. Mutable State and History Tasks are written transactionally. Transfer tasks are processed until the corresponding Workflow or Activity task is created in Matching; the architecture document explicitly identifies this as a transactional-outbox pattern.[4]

**Inferred consequence:** server-side durability does not eliminate duplicate execution at the boundary with external systems. If an Activity performs an external mutation and its completion acknowledgement is lost, retry safety still depends on an idempotency key, check-before-act logic, or an explicitly non-retryable policy. Temporal makes retry state explicit; it cannot make an arbitrary third-party API exactly-once.

### Sharding and membership

**Verified:** Workflow Executions are assigned to a fixed number of History Shards. The shard count is established at cluster creation and cannot be changed in place. Service instances own shard subsets through membership coordination; History uses generation fencing (`RangeID`) and persisted queue checkpoints.[4][15]

**Operational implication — inferred from verified design:** under-sizing shards is difficult to reverse. Capacity planning is an architectural decision, not just an autoscaler setting.

### Persistence and visibility

**Verified:** the repository contains persistence implementations/configuration for Cassandra, MySQL, PostgreSQL, and SQLite. SQLite is appropriate for embedded/local test paths; sustained production deployments require a managed production datastore and schema lifecycle.[4][6][17]

**Verified:** Visibility—the list/filter/search index for Workflow Executions—has a separate compatibility matrix. Current options include supported MySQL, PostgreSQL, SQLite, Elasticsearch, and OpenSearch versions; Cassandra is not a current Advanced Visibility store.[17]

**Inferred:** a small deployment can consolidate primary persistence and Visibility in PostgreSQL, reducing topology, but production suitability still depends on tested workload/query volume. Elasticsearch/OpenSearch adds cost and capability rather than being universally required.

## Determinism and deployment semantics

**Verified:** replay requires Workflow code to emit the same command sequence for the same recorded history. Direct time, randomness, network, model, database, and filesystem operations cannot safely steer Workflow control flow unless routed through replay-safe SDK primitives or Activities.[20]

**Verified:** some ordinary-looking code changes—reordering an Activity and Timer, changing command-producing calls, or changing a Workflow/Activity type or ID—can cause nondeterminism for already-running executions. Temporal supports Worker Versioning and patching; its documentation recommends replay testing representative histories before deployment.[19][20]

**Risk for agent systems — inferred:** agent orchestration code evolves frequently. Prompts and model choices can usually change inside Activities, but changes that alter the Workflow command graph need explicit compatibility discipline. Long-running conversations or human-in-the-loop workflows increase the time window during which old histories must remain replayable.

## Pydantic AI relevance, kept separate

**Verified:** Pydantic AI documents native Temporal support in its own repository. Its integration places agent coordination in a Temporal Workflow while routing model requests, I/O-capable tool calls, and MCP communication through Activities. A run is durable only when invoked inside a Temporal Workflow on a Worker; merely attaching the durability capability does not make an ordinary `agent.run()` durable.[21]

**Verified limitations from that integration’s documentation:** async APIs are required in Workflow code; Worker-side activity registration must be known when the Worker starts; and model-stream events may be buffered/replayed rather than delivered as a transparent live stream, depending on the chosen event handler.[21]

**Boundary conclusion:** Pydantic AI support is positive ecosystem evidence, not an implementation feature of `temporalio/temporal`. It must be versioned and tested as a three-part stack: Pydantic AI integration + Temporal Python SDK/Worker + Temporal Service.

## Strengths

- **Failure semantics are architectural, not bolted on — verified.** Event History, replay, durable timers, task queues, retries, signals/updates, and persisted workflow state are parts of one execution model.[3][4]
- **Application code and secrets remain outside the server — verified.** Workers poll the service and execute user Workflow/Activity code in user-controlled infrastructure.[3]
- **Extensive implementation evidence — verified.** The reviewed tree contains 2,950 Go files, including 951 `_test.go` files. Repository docs distinguish unit, integration, and functional suites.[6][7]
- **Broad CI matrix — verified.** The main test workflow covers unit tests, leak checks, integration tests, and functional/NDC/XDC paths across Cassandra, SQLite, MySQL, PostgreSQL, Elasticsearch, and OpenSearch configurations; main-branch pushes run the full database matrix.[8]
- **Security tooling exists in CI — verified.** Pull requests run `govulncheck`; recent visible workflow runs also included SAST. This is useful evidence of process, not proof of zero vulnerabilities.[9]
- **Strong maintenance signals — verified.** The API snapshot showed 595 commits over the sampled 90-day window, 302 contributor records, and a current stable release.[1][13]
- **Permissive core license — verified.** The server is MIT-licensed, permitting use, modification, distribution, sublicensing, and sale subject to notice preservation and warranty disclaimer.[12]
- **Local embedded testability — verified.** The repository now exposes `temporaltest.NewServer`, which launches an ephemeral loopback test server and can start SDK Workers in-process; the bounded smoke test below exercised it successfully.

## Risks and caveats

### Operational burden

- **High self-hosting burden — verified.** Temporal’s own production checklist names scalability, global hosting, availability, control plane, latency, security, upgrades, support, and cost as challenge areas, and calls the server complex to run and scale.[15]
- **Fixed shard count — verified.** Increasing capacity after under-sharding requires a rebuild/migration to a new service rather than an in-place setting change.[4][15]
- **Multiple owned components — verified.** Production requires server services, persistence, Visibility, application Worker fleets, schema tooling, network/security configuration, metrics/alerts, and commonly a separate UI. Multi-cluster replication and archival are additional systems, not free properties.[14][17]
- **Upgrade choreography — verified.** The documented path calls for sequential minor-version upgrades, compatible schema upgrades first, and observation between steps; non-consecutive compatibility is not guaranteed.[18]
- **Release churn — verified.** The latest release includes behavior/configuration changes in Visibility and compatibility notes, illustrating that active maintenance includes migration work, not only bug fixes.[13]

### Security posture

- **Security features are opt-in — verified.** Self-hosted Temporal supports internode/frontend mTLS, client certificate validation, JWT claim mapping, and pluggable authorization.[16]
- **Fail-open default — verified.** With an empty authorizer configuration, server code returns a no-op authorizer; startup warns but still permits it unless future behavior changes. Official docs state that this allows every API request and is unsafe for untrusted networks.[10][11][16]
- **No complete product RBAC/audit layer out of the box — verified.** The production checklist says self-hosted Temporal does not provide out-of-box RBAC or audit logging and suggests implementing these in a control plane. The built-in/default authorizer supports role checks, but identity mapping, policy integration, and operator auditability remain deployment responsibilities.[15][16]
- **Repository policy gap — verified with caveat.** GitHub reported no repository security-policy URL and the community profile had no `SECURITY.md`; the public repository-advisory endpoint returned zero advisories. This does **not** prove the absence of vulnerabilities or a missing organization-level reporting channel.
- **Payload confidentiality is not automatic — verified.** Transport encryption protects connections, while sensitive Workflow/Activity payloads require SDK Data Converters/Payload Codecs and careful Codec Server security. Histories, inputs, outputs, and errors should be treated as persisted application data.[16]
- **CI scope is incomplete evidence — inferred.** `govulncheck` runs on pull requests, but unavailable Dependabot/code-scanning alert APIs could not be assessed with public/read-only permissions. Do not infer a clean dependency backlog from inaccessible alerts.

### Programming-model burden

- **Deterministic Workflow code is a real constraint — verified.** Unsafe I/O, time, randomness, concurrency, and command-order changes can break replay.[20]
- **Activities are retryable, not magically exactly-once — inferred from the retry/outbox design.** External mutations need explicit idempotency and compensation design.
- **Long histories and payload retention create data/latency pressure — inferred.** Durable state is persisted; workflows that append unbounded conversational/tool detail need Continue-As-New, payload discipline, retention, and archival policies.
- **Worker deployment becomes part of correctness — verified.** Version compatibility and replay testing are necessary when Workflow code changes while executions remain active.[19][20]
- **Infrastructure can exceed personal-workload needs — inferred.** For low-volume personal automation, a database-backed job queue plus explicit checkpoints may be cheaper unless long waits, signals, crash recovery, and auditability are central requirements.

## Operational burden by deployment mode

| Mode | What it proves/provides | What the operator owns |
|---|---|---|
| CLI development server | Fast complete local service and UI with no external dependency.[14][23] | Disposable local state; not production topology or HA. |
| Embedded `temporaltest` server | Repeatable application tests against a real in-process server path. | Test lifecycle and fixtures; not external persistence or production networking. |
| Self-hosted single cluster | Full control over data plane and topology. | Server roles, DB/Visibility, schemas, auth, TLS, metrics, backups, capacity, Workers, upgrades, incidents. |
| Self-hosted multi-cluster | Cross-cluster replication/failover capabilities. | All single-cluster work plus replication topology, failover semantics, tokens/TLS, and regional operations. |
| Temporal Cloud | Managed Temporal Service. | Application Workers, workflow compatibility, payload security, costs, quotas, and vendor/service evaluation; Cloud-specific terms are outside this repo. |

## Bounded smoke test

### Executed

**Verified locally against reviewed commit `9ab3a9f…`:** executed in a disposable `golang:1.27` container with `CGO_ENABLED=0`, a read-only source mount and isolated Go caches. The test command was:

```bash
go test -v ./temporaltest -run '^TestNewServer$' -count=1
```

Result: `PASS`; package `go.temporal.io/server/temporaltest`; 0.640 seconds after dependency/build caches were populated. The test started an ephemeral server, registered an SDK Worker, executed a Workflow plus Activity, returned `Hello world`, and stopped the Worker.

A separate source-level package test also passed:

```bash
go test ./common/backoff
```

Result: `ok go.temporal.io/server/common/backoff 20.736s`.

### What this proves

- The reviewed source resolves and compiles under its declared Go 1.27 toolchain for the exercised dependency graph.
- The embedded server can initialize in a clean container, communicate with a Go SDK Worker, schedule an Activity, and complete a Workflow on the happy path.
- The repository’s test helper is viable for bounded integration tests without an external database.

### What this does not prove

- Crash recovery or durability across process/database restart—the exercised server was explicitly ephemeral.
- PostgreSQL/MySQL/Cassandra/Visibility behavior, schema upgrades, backups, or production throughput.
- High availability, shard sizing, multi-cluster failover, or network partitions.
- mTLS, JWT claim mapping, authorization, auditability, or payload encryption.
- Python SDK compatibility, Pydantic AI integration, model/tool retries, streaming, or application-specific replay safety.
- Exactly-once external side effects or correct compensation behavior.
- A production-ready deployment.

### Recommended application pilot

**Inferred recommendation:** use a disposable development server plus the intended SDK/agent framework and a fake model/tool layer. The pilot should:

1. Run one deterministic orchestration that invokes model/tool calls as Activities and waits for a signal/approval.
2. Kill and restart the application Worker during a timer and during a deliberately failing Activity.
3. Verify resume behavior from Event History and verify that an idempotency key prevents duplicate external mutation.
4. Change Workflow code incompatibly and confirm replay tests catch nondeterminism before deployment.[19]
5. Inspect payloads/history to identify secrets, large model responses, and retention requirements.
6. Exercise cancellation, timeout, retry exhaustion, human rejection, and compensation—not just success.
7. Record operational measurements: idle memory, database growth, event count/history size, startup/recovery latency, and upgrade steps.

Passing this would support “Temporal fits this workflow and SDK.” It would still not prove production HA or justify self-hosting instead of Temporal Cloud.

## Reusable design patterns

- **Durable coordinator / effectful executor split:** keep orchestration replayable; isolate external I/O behind Activities.[3][20]
- **Persist decisions, not process memory:** reconstruct coordinator state from recorded events rather than serializing a live runtime object.[3][4]
- **Transactional outbox for work dispatch:** persist state transition plus intent-to-dispatch atomically, then retry dispatch asynchronously.[4]
- **Worker pull model:** Workers poll named Task Queues, preserving network boundaries and letting execution capacity scale separately from service state.[3][5]
- **Replay compatibility as a deployment gate:** test new coordinator code against old real histories before rollout.[19]
- **Idempotency at every external effect:** use workflow/run/activity identifiers as stable mutation keys; assume acknowledgement loss can cause retry.
- **Signals/updates for human-in-the-loop:** model long waits and approvals as durable workflow interactions rather than blocked HTTP requests.
- **Separate service truth from searchable visibility:** treat execution persistence and operational search as different storage concerns.

## Alternatives / comparison frame

No cross-repo benchmark was run. A fair follow-up should compare Temporal with DBOS, Restate, Prefect, and a simpler queue/checkpoint architecture on the same failure-injection fixture. Evaluate:

- deterministic replay versus durable promises/state machines/checkpoints;
- worker and server topology;
- Python/agent-framework integration maturity;
- exactly-once claims versus actual idempotency contract;
- human-signal and long-timer semantics;
- local development fidelity;
- observability/history debugging;
- upgrade and self-hosting burden;
- managed-service availability and lock-in;
- payload/privacy model and licensing.

## Evidence checked

### Repository and source

- README and boundary statement.[2]
- Architecture overview, History Service, Matching Service, and workflow lifecycle.[3][4][5]
- Server CLI entrypoint and auth wiring.[11]
- Authorization implementation and defaults.[10]
- Persistence/config templates for supported datastores, TLS, metrics, and authorization.
- `temporaltest` embedded server and its end-to-end test.
- Test guidance and CI workflows.[7][8][9]
- MIT license.[12]
- Release `v1.32.0` notes.[13]

### Live metadata/API

- `gh repo view`, REST repository/community profile, releases, contributors, commits, tags, Actions runs, and repository security advisories.
- Dependabot and code-scanning alert endpoints returned HTTP 403 for this non-admin token; no claim is made about their status.
- Local shallow clone: a disposable source checkout.
- Metadata/API observations are summarized here; local capture files are not required dependencies.

### Documentation

- Self-hosted guide and production checklist.[14][15]
- Deployment, security, and upgrade guidance.[16][17][18]
- Monitoring and Visibility guidance (retrieved as part of the official self-hosted documentation set).
- Workflow determinism/versioning and safe deployments.[19][20]
- Pydantic AI Temporal integration, explicitly treated as external ecosystem evidence.[21]

### Hype calibration

- **Verified:** architecture, source paths, license, current metadata, CI definitions, release state, security defaults, test counts, and bounded smoke results.
- **Inferred:** suitability for long-running agent workloads, operational fit for a personal stack, duplicate-effect implications, and recommended pilot design.
- **Not verified:** production scale/SLA, managed Cloud guarantees, full vulnerability backlog, comparative performance, application-specific SDK behavior, and application-specific agent-stack integration.

## Evaluation boundary

- None persisted. Application-specific adoption state belongs in the private runtime/architecture surface, not this reusable repo note.

## Review candidates

- **Rank 1 — representative failure-injection pilot.** Rationale: closes the largest fit uncertainty. Review question: does recovery and event-history visibility justify deterministic workflow constraints? Promotion condition: a real long-running or approval-heavy workload is selected.
- **Rank 2 — managed versus self-hosted decision.** Rationale: self-hosting dominates burden. Review question: are privacy/control requirements strong enough to justify owning persistence, security, upgrades, and on-call? Promotion condition: pilot passes and production use is contemplated.
- **Rank 3 — alternatives bake-off.** Rationale: usefulness is high but differentiation has not been measured against DBOS/Restate/Prefect/simple checkpoints. Review question: which system meets the same crash/retry/HITL fixture with the least lifetime cost? Promotion condition: there is intent to choose a backend.

## Commitment disposition

- Not promoted. This report supplies evidence only; no production adoption or canonical-repo modification was authorized.

## Sources

[1] https://github.com/temporalio/temporal
[2] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/README.md
[3] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/docs/architecture/README.md
[4] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/docs/architecture/history-service.md
[5] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/docs/architecture/matching-service.md
[6] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/CONTRIBUTING.md
[7] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/docs/development/testing.md
[8] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/.github/workflows/run-tests.yml
[9] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/.github/workflows/govulncheck.yml
[10] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/common/authorization/authorizer.go
[11] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/cmd/server/main.go
[12] https://github.com/temporalio/temporal/blob/9ab3a9f770da20df7d94bcc0030f28eec7b0b947/LICENSE
[13] https://github.com/temporalio/temporal/releases/tag/v1.32.0
[14] https://docs.temporal.io/self-hosted-guide
[15] https://docs.temporal.io/self-hosted-guide/production-checklist
[16] https://docs.temporal.io/self-hosted-guide/security
[17] https://docs.temporal.io/self-hosted-guide/deployment
[18] https://docs.temporal.io/self-hosted-guide/upgrade-server
[19] https://docs.temporal.io/develop/safe-deployments
[20] https://docs.temporal.io/workflow-definition
[21] https://github.com/pydantic/pydantic-ai/blob/main/docs/durable_execution/temporal.md
[22] https://github.com/temporalio/sdk-python
[23] https://github.com/temporalio/cli
