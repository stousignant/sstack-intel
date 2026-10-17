---
title: scitix/siclaw
type: repo-intel
aliases: [siclaw, GitHub repo: scitix/siclaw]
source: https://github.com/scitix/siclaw
category: security-containment-agent-safety
topics: [github-repo, sre-agent, kubernetes, read-only-diagnostics, command-policy]
status: deep-analyzed
usefulness_score: 64
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: Apache-2.0
---

# scitix/siclaw

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `64/100` — useful read-only SRE/command-policy reference, but not a general Hermes security runtime.
- **Recommendation:** `distill-pattern` / `watch`.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Extract command registry, read-only allowlist, sensitive-path block, and output redaction tests for Hermes admin/SRE skills.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 17/25 | Relevant to local/K8s diagnostics, less to general agent sandboxing. |
| Leverage | 17/25 | Command-policy semantics are reusable. |
| Reuse readiness | 13/20 | Real app/scripts, but domain-specific. |
| Maturity/trust | 10/15 | Active, Apache-2.0, some rough docs and residual risks. |
| Differentiation | 9/15 | Read-only SRE agent pattern is useful but narrow. |

## Verdict

Siclaw is a good pattern source for safe infrastructure investigation: command allowlists, restricted bash, Kubernetes read-only verbs, output sanitization, AgentBox execution, and team workflows. It is closer to a domain-specific SRE copilot than a general-purpose Hermes sandbox.

## Reference-stack relevance

- Hermes sometimes touches local/admin/devops surfaces; command policy matters.
- Good pattern source for “read-only diagnostics first” skills.
- AgentBox and Portal/TUI pairing may inspire safer operator workflows.

## What it is

An AI-powered SRE/Kubernetes diagnostic platform with read-only infrastructure investigation, skills/runbooks, command validators, and a web/TUI collaboration flow.

## Evidence checked

- GitHub metadata on 2026-06-03: ~207 stars, pushed 2026-06-03.
- README, security policy, license, root files from the upstream repository.
- Repomix pack: a temporary source pack of the public repository — 587 files / ~455k tokens; no suspicious files detected.
- Targeted evidence: restricted bash, pod/node exec, command registry/validators/tests, kubectl restrictions, blocked writes/exec/redirections, sensitive path blocking, output/env sanitizer, AgentBox dropping root to `agentbox`.

## Strengths

- Practical read-only command-policy architecture.
- Explicit sanitizer and sensitive-path concerns.
- Useful domain-agent shape for Kubernetes/SRE diagnostics.

## Risks / caveats

- Node/process compromise can still read kubeconfig per acknowledged residual risks.
- Network exfiltration depends on external NetworkPolicy.
- Trusted skill scripts may bypass output sanitizer.
- Command allowlists are brittle and require maintenance.

## Integration ideas

- Build Hermes local-admin/devops skills around command registries and read-only modes.
- Add post-command secret redaction tests to risky skills.
- Prefer this as pattern source beside OpenShell/IronClaw containment.

## Alternatives / related repos

- [NVIDIA/OpenShell](NVIDIA--OpenShell.md)
- [nearai/ironclaw](nearai--ironclaw.md)
- [Agastya910/agentarmor](Agastya910--agentarmor.md)

## Review guidance

- Review candidate: distill read-only command policy and sanitizer patterns for Hermes admin/SRE workflows.
