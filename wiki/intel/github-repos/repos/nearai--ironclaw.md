---
title: nearai/ironclaw
type: repo-intel
aliases: [ironclaw, IronClaw, GitHub repo: nearai/ironclaw]
source: https://github.com/nearai/ironclaw
category: security-containment-agent-safety
topics: [github-repo, agent-os, wasm-sandbox, capabilities, secrets, prompt-injection]
status: deep-analyzed
usefulness_score: 90
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: MIT OR Apache-2.0
---

# nearai/ironclaw

> Reference-stack fit as reviewed 2026-06-03; see [methodology](../../awesome-harness-engineering/methodology.md). Usage observations below are dated, not live-state claims.

## Decision

- **Usefulness score:** `90/100` — excellent security architecture reference for WASM sandboxing, capabilities, egress limits, resource limits, approvals, secret leasing, and safety filters.
- **Recommendation:** `distill-pattern`; possible isolated lab eval, but too broad to adopt as Hermes runtime now.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Deep-read capability/network/safety/secrets contract tests and distill a Hermes host-boundary design.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Directly aligned with safe agent execution and privacy. |
| Leverage | 24/25 | Could define the right host-boundary model for Hermes. |
| Reuse readiness | 13/20 | Serious Rust stack, but heavy prerequisites and full OS scope. |
| Maturity/trust | 13/15 | Active, substantial tests/docs; architecture in transition. |
| Differentiation | 15/15 | Capability/WASM/secret-lease architecture is high-signal. |

## Verdict

IronClaw may be the best pure security-design reference in this batch. It is too big to graft into Hermes casually, but its architecture is exactly the right shape: host-mediated permissions, WASM sandbox, endpoint allowlists, resource limits, opaque secret handles, leak detection, approval flows, and tool-output wrapping.

## Workload fit

- Directly addresses the safety boundary for autonomous agents.
- More architecture-complete than library-level guardrails.
- Provides concrete vocabulary for Hermes containment design.

## What it is

An Agent OS focused on privacy, security, and extensibility, with Rust crates for safety, network, secrets, capabilities, approvals, resources, trust, and WASM execution.

## Evidence checked

- GitHub metadata on 2026-06-03: ~12.4k stars, pushed 2026-06-03.
- README, `Cargo.toml`, license evidence, root files under temporary upstream inspection material.
- Repomix pack: a temporary Repomix inspection pack — 1,862 files / ~5.14M tokens; 28 suspicious files excluded; read selectively.
- Targeted evidence: `ironclaw_safety`, `ironclaw_network`, `ironclaw_secrets`, `ironclaw_capabilities`, `ironclaw_approvals`, `ironclaw_resources`, `ironclaw_trust`; network private-target rejection, no caller Host header, redirect/body/timeouts, one-shot secret leases, prompt-injection and leak scanning, tool-output delimiter wrapping.

## Strengths

- Host-boundary and capability model are conceptually strong.
- WASM + permissions + secrets is a better safety story than prompt guardrails.
- Many relevant tests/docs/fuzz surfaces visible.

## Risks / caveats

- Heavy prerequisites: Rust, PostgreSQL, pgvector, NEAR AI auth, optional C toolchain.
- Engine v2 is opt-in, suggesting ongoing transition.
- Some enforcement lives at higher composition layers, not low-level crates alone.
- Competing full Agent OS could create runtime sprawl.

## Integration ideas

- Distill a Hermes design doc: host boundary, capability permits, tool-output sanitizer, one-shot secret leases.
- Compare to OpenShell before choosing an evaluation sandbox.
- Use as architecture north-star, not a default install.

## Alternatives / related repos

- [NVIDIA/OpenShell](NVIDIA--OpenShell.md)
- [Agastya910/agentarmor](Agastya910--agentarmor.md)
- [sipeed/picoclaw](sipeed--picoclaw.md)

## Review candidates and context

- Candidate: distill IronClaw capability/network/secrets/safety patterns into agent host-boundary design.
