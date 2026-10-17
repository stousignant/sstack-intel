---
title: Security / Containment / Agent Safety Repo Comparison
created: 2026-06-03
updated: 2026-06-03
type: comparison
tags: [github-repos, security, containment, agent-safety, supply-chain, routers]
status: active
lifecycle: volatile
confidence: medium
last_reviewed: 2026-06-08
review_cadence: quarterly
sources:
  - wiki/intel/github-repos/repos/Agastya910--agentarmor.md
  - wiki/intel/github-repos/repos/BlockRunAI--ClawRouter.md
  - wiki/intel/github-repos/repos/Ed1s0nZ--CyberStrikeAI.md
  - wiki/intel/github-repos/repos/NVIDIA--OpenShell.md
  - wiki/intel/github-repos/repos/decolua--9router.md
  - wiki/intel/github-repos/repos/nearai--ironclaw.md
  - wiki/intel/github-repos/repos/perplexityai--bumblebee.md
  - wiki/intel/github-repos/repos/scitix--siclaw.md
  - wiki/intel/github-repos/repos/sipeed--picoclaw.md
  - wiki/intel/github-repos/repos/x1xhlol--system-prompts-and-models-of-ai-tools.md
---

# Security / Containment / Agent Safety Repo Comparison

Dated reference-stack comparison: capability fit, overlap, and integration cost are judged for the workloads summarized below; recorded scores and verdicts retain their dated scope, not universal product rankings. See the [evaluation methodology](../../awesome-harness-engineering/methodology.md).

## Executive recommendation

- **Sandbox now:** [NVIDIA/OpenShell](../repos/NVIDIA--OpenShell.md) and [perplexityai/bumblebee](../repos/perplexityai--bumblebee.md). OpenShell is the best real containment candidate; Bumblebee is the fastest practical supply-chain exposure scanner.
- **Distill now:** [nearai/ironclaw](../repos/nearai--ironclaw.md). Its capability/WASM/secrets/network/safety architecture should shape Hermes containment design.
- **Pattern-only:** [scitix/siclaw](../repos/scitix--siclaw.md), [sipeed/picoclaw](../repos/sipeed--picoclaw.md), [Agastya910/agentarmor](../repos/Agastya910--agentarmor.md). Useful primitives, not trust boundaries.
- **Reference/negative examples:** [Ed1s0nZ/CyberStrikeAI](../repos/Ed1s0nZ--CyberStrikeAI.md), [x1xhlol/system-prompts-and-models-of-ai-tools](../repos/x1xhlol--system-prompts-and-models-of-ai-tools.md), [BlockRunAI/ClawRouter](../repos/BlockRunAI--ClawRouter.md), [decolua/9router](../repos/decolua--9router.md). Keep useful lessons; do not import risky semantics or credentials.

## Decision matrix

| Repo | Fit | Maturity | Install cost | License | Safety posture | Verdict |
|---|---:|---:|---:|---|---|---|
| [NVIDIA/OpenShell](../repos/NVIDIA--OpenShell.md) | 25 | 13 | High | Apache-2.0 | Host/runtime containment | Sandbox now; best containment candidate, but alpha. |
| [nearai/ironclaw](../repos/nearai--ironclaw.md) | 24 | 13 | High | MIT OR Apache-2.0 | WASM/capability architecture | Distill design; possible lab eval only. |
| [perplexityai/bumblebee](../repos/perplexityai--bumblebee.md) | 24 | 13 | Low | Apache-2.0 | Read-only exposure inventory | Sandbox now; easiest practical win. |
| [BlockRunAI/ClawRouter](../repos/BlockRunAI--ClawRouter.md) | 19 | 10 | Medium | MIT | Router/proxy + payments | Watch; audit with unfunded wallet only. |
| [scitix/siclaw](../repos/scitix--siclaw.md) | 17 | 10 | Medium | Apache-2.0 | Read-only command policy | Distill admin/SRE patterns. |
| [sipeed/picoclaw](../repos/sipeed--picoclaw.md) | 16 | 8 | Medium | MIT | Config/redaction/allowlist | Distill lightweight config patterns. |
| [Agastya910/agentarmor](../repos/Agastya910--agentarmor.md) | 17 | 7 | Medium | Apache-2.0 | Heuristic guardrail library | Distill; do not adopt wholesale. |
| [x1xhlol/system-prompts-and-models-of-ai-tools](../repos/x1xhlol--system-prompts-and-models-of-ai-tools.md) | 14 | 7 | Low | GPL-3.0 metadata | Prompt leak corpus | Sanitized defensive taxonomy only. |
| [decolua/9router](../repos/decolua--9router.md) | 13 | 7 | Medium | MIT | OAuth/proxy/router risk | Negative example; avoid real credentials. |
| [Ed1s0nZ/CyberStrikeAI](../repos/Ed1s0nZ--CyberStrikeAI.md) | 8 | 8 | Medium | Apache-2.0 | Offensive dual-use platform | Reference only; blacklist C2/webshell semantics. |

## Category map

This batch revealed four distinct safety categories:

1. **Actual containment substrates** — OpenShell and IronClaw. These think at the host boundary: files, processes, network, credentials, capabilities, WASM, and policy.
2. **Exposure / inventory scanners** — Bumblebee. This is not a sandbox, but it is a very practical “what is installed/exposed?” defensive tool.
3. **Guardrails and command policies** — AgentArmor, Siclaw, PicoClaw. Useful patterns, but mostly wrappers, config, allowlists, redaction, and read-only command logic rather than hard isolation.
4. **Risky router/offensive/prompt corpora** — ClawRouter, 9router, CyberStrikeAI, system-prompt leaks. These are valuable mostly because they expose trust-boundary failures and anti-patterns.

## Reference-stack recommendation

The next safety move should be boring and concrete:

1. Run **Bumblebee** on a copied/non-sensitive root with a tiny Hermes-specific exposure catalog.
2. Run **OpenShell** in a throwaway repo to see whether it can contain a Hermes-like agent task.
3. Distill **IronClaw** into a Hermes host-boundary design note.

Do not start by wiring model routers into real Hermes traffic. Routers/proxies are a credential and prompt-exfiltration surface; treat ClawRouter and 9router as audit subjects, not convenience upgrades.

## Open questions

- Can OpenShell run the actual Hermes/Codex/Claude lanes under evaluation without too much friction?
- What is the minimum Hermes policy bundle: allowed mounts, denied egress, credential injection, output redaction, and proof-of-work capture?
- Can Bumblebee's catalog format cover portable skills and Hermes skills and MCP configs cleanly?
- Which IronClaw primitives are worth implementing in Hermes directly versus keeping as design inspiration?
