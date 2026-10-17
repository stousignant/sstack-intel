---
title: NVIDIA/OpenShell
type: repo-intel
aliases: [OpenShell, GitHub repo: NVIDIA/OpenShell]
source: https://github.com/NVIDIA/OpenShell
category: security-containment-agent-safety
topics: [github-repo, sandboxing, agent-runtime, egress-policy, credentials, containment]
status: deep-analyzed
usefulness_score: 92
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: Apache-2.0
---

# NVIDIA/OpenShell

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `92/100` — strongest containment reference in the batch: policy-enforced agent runtime, egress proxy, filesystem/process restrictions, credential injection, and inference routing.
- **Recommendation:** `adopt-now` for isolated evaluation; treat as alpha/reference architecture, not production default yet.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Run a contained local eval focused on filesystem boundaries, denied outbound HTTP, and credential stripping/injection.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 25/25 | Directly maps to safe Hermes autonomous execution. |
| Leverage | 24/25 | Could become the containment substrate for long-running agents. |
| Reuse readiness | 16/20 | Rich docs/runtime paths; bigger operational footprint. |
| Maturity/trust | 13/15 | NVIDIA-backed and active, but explicitly alpha. |
| Differentiation | 14/15 | Strong host-boundary + egress-policy model. |

## Verdict

OpenShell is the security-batch heavyweight. It is not “just a shell wrapper”; it is a serious agent containment architecture with local/VM/Kubernetes runtime paths, policy-driven network/filesystem constraints, credential boundary logic, and an agent-oriented CLI. If Hermes is going to run longer autonomous coding tasks, this is one of the first external systems worth sandboxing.

## Reference-stack relevance

- Provides a concrete answer to “how do we let agents work without trusting them with everything?”
- The egress proxy and credential-stripping model are directly relevant to Hermes tool safety.
- Good reference for policy authoring and sandbox lifecycle.

## What it is

An alpha sandbox/runtime for autonomous coding agents using container/VM/Kubernetes-style isolation, policy-enforced egress, credential handling, and inference routing.

## Evidence checked

- GitHub metadata on 2026-06-03: ~6.6k stars, pushed 2026-06-03, NVIDIA-owned.
- README, security policy, Python/Rust manifests, license, and root files under [upstream repository inspection](https://github.com/NVIDIA/OpenShell).
- Repomix pack: a temporary Repomix inspection pack — 755 files / ~1.84M tokens; 3 suspicious files excluded; read selectively.
- Targeted evidence: supervisor/unprivileged child, Landlock/seccomp/network namespace, mandatory CONNECT proxy, SSRF/private-IP checks, binary identity, credential stripping/injection, inference.local routing, VM/procguard/nftables tests, architecture docs, Helm/K8s/local paths.

## Strengths

- Host-boundary containment instead of pure prompt-level guardrails.
- Explicit alpha labeling is honest and useful.
- Strong policy/egress/credential architecture for autonomous agents.
- Active, substantial codebase with docs/tests.

## Risks / caveats

- Alpha; expect sharp edges and breaking changes.
- Operational footprint is non-trivial: Docker/Podman/MicroVM/K8s, Rust/Python/kernel dependencies.
- Telemetry defaults and runtime-specific behavior need review before real use.

## Integration ideas

- Evaluate OpenShell as a sandbox lane for Hermes/Codex/Claude coding tasks.
- Use its policy model as a reference even if adoption is too heavy.
- Map Hermes profiles to OpenShell policy bundles.

## Alternatives / related repos

- [nearai/ironclaw](nearai--ironclaw.md)
- [perplexityai/bumblebee](perplexityai--bumblebee.md)
- [sipeed/picoclaw](sipeed--picoclaw.md)

## Review candidates and context

- Candidate: run an isolated OpenShell containment evaluation for one Hermes-like agent task.
