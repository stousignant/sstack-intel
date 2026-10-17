---
title: NVIDIA/NemoClaw
type: repo-intel
aliases:
  - NemoClaw
  - GitHub repo: NVIDIA/NemoClaw
source: https://github.com/NVIDIA/NemoClaw
category: agent-sandboxing
topics: [github-repo, repo-intelligence, agent-evaluation, agent-training]
status: deep-analyzed
usefulness_score: 86
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: Apache-2.0
---

# NVIDIA/NemoClaw

> Reference-stack evaluation as reviewed 2026-05-30. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `86/100` — Best sandbox/security reference in this batch, explicitly mentions Hermes support, but it depends on the broader OpenShell/NVIDIA stack and should not replace Hermes’ current local runtime.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Inspect docs/security controls and compare against Hermes tool boundaries; sandbox only if OpenShell becomes an active containment candidate.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 23/25 | Fits Hermes/GBrain/local-agent questions, but direct runtime fit varies by repo. |
| Leverage | 22/25 | Useful for evals, self-improvement, research automation, or sandbox safety. |
| Reuse readiness | 15/20 | Docs/install/licensing are present, but most require sandboxing before use. |
| Maturity/trust | 13/15 | Live metadata: 20728 stars, 2758 forks, pushed 2026-05-30T22:35:46Z, license Apache-2.0. |
| Differentiation | 13/15 | Distinctive compared with current Hermes stack as an eval/training/safety pattern source. |

## Verdict

Best sandbox/security reference in this batch, explicitly mentions Hermes support, but it depends on the broader OpenShell/NVIDIA stack and should not replace Hermes’ current local runtime. The useful move is not to install this globally. Keep Hermes/GBrain as the active operating layer, extract the eval/training/sandbox pattern, and only run bounded sandboxes with copied/non-sensitive data.

## Workload fit

- This batch sits directly on the question of making Hermes more measurable and self-improving: benchmark tasks, trajectory capture, training loops, HITL research workflows, and safer agent sandboxes.
- It can turn “agent improvement” from vibes into artifacts: task suites, hidden graders, traces, verification reports, and explicit keep/revert criteria.
- Its practical value is strongest when evaluation artifacts establish a concrete gap before adding another runtime or memory store.

## What it is

NemoClaw is an NVIDIA reference stack for running agents such as OpenClaw and Hermes inside OpenShell sandboxes with managed inference and hardening guidance.

## Live metadata checked

- Source: <https://github.com/NVIDIA/NemoClaw>
- Description: Run agents like Hermes and OpenClaw more securely inside NVIDIA OpenShell with managed inference
- Stars / forks: 20728 / 2758
- Primary language: TypeScript
- License: Apache-2.0
- Latest release: none observed
- Last pushed: 2026-05-30T22:35:46Z
- Topics: none listed

## Evidence checked

- GitHub metadata via `gh repo view NVIDIA/NemoClaw` on 2026-05-30.
- README from [upstream README](https://github.com/NVIDIA/NemoClaw).
- License and manifest files where present under [upstream repository inspection](https://github.com/NVIDIA/NemoClaw).
- Top-level contents from GitHub API snapshot in `contents.json`.

## Strengths

- README explicitly lists Hermes quickstart via `NEMOCLAW_AGENT=hermes` / `nemohermes`, making it more relevant than generic sandbox repos.
- Apache-2.0, active repo, security policy, Dockerfiles, CLI package metadata, docs, schemas, and hardening docs signal serious operational design.
- Useful safety surface: sandbox hardening, capability drops/process limits, auth/inference controls, installer/CLI ergonomics.

## Risks / caveats

- Vendor/platform gravity: NVIDIA/OpenShell assumptions may add a large new substrate around an already-working Hermes stack.
- Repo appears docs/CLI/install heavy; actual security guarantees require reading hardening docs and testing isolation, not trusting badges.
- Agent sandboxing can become security theater if host mounts, secrets, and network egress are not audited.

## Integration ideas

- Use as a checklist source for Hermes local-tool hardening: process limits, mounts, capabilities, network/secret boundaries, and security reporting docs.
- Compare against existing Hermes terminal/file/process permission model and any future containerized worker lane.

## Alternatives / related repos

- [microsoft/agent-lightning](microsoft--agent-lightning.md)
- [InternLM/WildClawBench](InternLM--WildClawBench.md)
- [aiming-lab/AutoResearchClaw](aiming-lab--AutoResearchClaw.md)
- [Gen-Verse/OpenClaw-RL](Gen-Verse--OpenClaw-RL.md)
- [NVIDIA/NemoClaw](NVIDIA--NemoClaw.md)
- [karpathy/autoresearch](karpathy--autoresearch.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)

## Review candidates and context

- Create a sandbox posture checklist only if Hermes starts running more autonomous long-lived agents.
- Guidance: these recommendations are non-binding; execution state belongs in the established issue tracker.
