---
title: Agastya910/agentarmor
type: repo-intel
aliases: [agentarmor, GitHub repo: Agastya910/agentarmor]
source: https://github.com/Agastya910/agentarmor
category: security-containment-agent-safety
topics: [github-repo, agent-security, prompt-injection, guardrails, tool-policy]
status: deep-analyzed
usefulness_score: 55
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: Apache-2.0
---

# Agastya910/agentarmor

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `55/100` — useful security-pattern decomposition, but alpha maturity and heuristic guardrails make it unsafe to adopt wholesale.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Extract canary, output-secret-scanner, network policy, and per-tool budget patterns into Hermes design notes.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 17/25 | Covers Hermes-relevant agent-security surfaces. |
| Leverage | 15/25 | Good patterns; full package adoption would add uncertain enforcement. |
| Reuse readiness | 11/20 | Python package exists, but heavy dependency surface. |
| Maturity/trust | 7/15 | README says production-grade, metadata says alpha; small project signal. |
| Differentiation | 5/15 | Concepts are useful but many are standard guardrail heuristics. |

## Verdict

AgentArmor is worth mining, not trusting. It is a broad “8-layer” agent-security framework with canaries, goal locking, network policy, output sanitization, budgets, and inter-agent auth. The problem is confidence: several mechanisms are heuristic and only work if every tool call routes through the wrapper.

## Reference-stack relevance

- Offers a checklist for Hermes agent safety layers.
- Canary and output-redaction ideas map cleanly to long-running agent tasks.
- Useful contrast against heavier containment systems like OpenShell/IronClaw.

## What it is

A Python agent-security library that attempts to protect agent sessions across prompt injection, tool calls, context assembly, output leakage, network policy, and inter-agent communication.

## Evidence checked

- GitHub metadata on 2026-06-03: ~88 stars, pushed 2026-05-18.
- README, `pyproject.toml`, license, and root files under [upstream repository inspection](https://github.com/Agastya910/agentarmor).
- Repomix pack: a temporary Repomix inspection pack — 95 files / ~76k tokens; no suspicious files detected.
- Targeted evidence: `CanaryVault`, `GoalLock`, context assembly, token stripping, DNS/private-IP network policy, token buckets, output sanitizer, HMAC/replay/delegation logic.

## Strengths

- Concrete code exists behind several claimed layers.
- Good conceptual inventory of agent security concerns.
- Apache-2.0 license reduces pattern-reuse friction.

## Risks / caveats

- Alpha maturity despite strong README claims.
- Guardrails are heuristic and bypass-prone if not enforced at the host boundary.
- Heavy dependencies are an awkward fit for a security library.

## Integration ideas

- Translate patterns into Hermes-native enforcement points, not a direct dependency.
- Add a canary leak test and output secret scanner to long-running agent verification.
- Compare against OpenShell/IronClaw host-boundary containment before adopting any library-level guardrail.

## Alternatives / related repos

- [perplexityai/bumblebee](perplexityai--bumblebee.md)
- [NVIDIA/OpenShell](NVIDIA--OpenShell.md)
- [nearai/ironclaw](nearai--ironclaw.md)

## Review candidates and context

- Candidate: distill Hermes-native canary/budget/output-scanner patterns from AgentArmor.
