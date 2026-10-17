---
title: sipeed/picoclaw
type: repo-intel
aliases: [picoclaw, PicoClaw, GitHub repo: sipeed/picoclaw]
source: https://github.com/sipeed/picoclaw
category: security-containment-agent-safety
topics: [github-repo, lightweight-agent-runtime, mcp, credential-redaction, tool-allowlist]
status: deep-analyzed
usefulness_score: 58
recommendation: distill-pattern
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: MIT
---

# sipeed/picoclaw

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `58/100` — useful lightweight Go agent-runtime reference, but not strong containment and not a Hermes install candidate.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Inspect and extract minimal MCP allowlist, credential encryption, and redaction patterns.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 16/25 | Agent/MCP/security config patterns are relevant. |
| Leverage | 15/25 | Useful primitives, but not a safety substrate. |
| Reuse readiness | 12/20 | Single-binary Go shape is attractive; huge integration surface. |
| Maturity/trust | 8/15 | Very active/popular but README warns early pre-v1 security issues. |
| Differentiation | 7/15 | Lightweight runtime ideas; weaker containment story. |

## Verdict

PicoClaw is worth pattern-mining for lightweight agent runtime ergonomics, not installing as security infrastructure. The interesting pieces are `.security.yml`, tool/MCP allowlists, sensitive-data filtering, credential encryption, and low-resource deployment. The README itself warns not to deploy to production before v1.0.

## Reference-stack relevance

- Shows how a compact Go agent runtime handles config, MCP, channels, and credentials.
- Useful counterpoint to heavier OpenShell/IronClaw containment approaches.
- Some primitives could improve SStack/Hermes skill safety docs.

## What it is

A lightweight personal-agent runtime in Go with MCP support, channels, web UI, cron/security gating mentions, tool allowlists, and credential handling.

## Evidence checked

- GitHub metadata on 2026-06-03: ~29.3k stars, pushed 2026-06-03.
- README, `go.mod`, license, root files from the upstream repository.
- Repomix pack: a temporary source pack of the public repository — 1,321 files / ~1.23M tokens; 9 suspicious files excluded; read selectively.
- Targeted evidence: `.security.yml`, sensitive data replacer, `enc://` credentials, AES-256-GCM/HKDF, `file://` containment checks, tool/MCP allowlist code, gateway binding warnings.

## Strengths

- Small/single-binary runtime model is attractive.
- Concrete credential/redaction/allowlist primitives exist.
- Native MCP and many integrations make it a broad design reference.

## Risks / caveats

- Early rapid development; README warns about unresolved security issues.
- Security is mostly config/redaction/allowlist, not strong isolation.
- Many integrations increase attack surface.
- Brand/hype/impersonation risk around high star count and scam warning.

## Integration ideas

- Extract a minimal Hermes `.security.yml`-style config vocabulary.
- Borrow credential redaction patterns only after reading tests.
- Do not expose web gateway or channels without stronger containment.

## Alternatives / related repos

- [NVIDIA/OpenShell](NVIDIA--OpenShell.md)
- [nearai/ironclaw](nearai--ironclaw.md)
- [BlockRunAI/ClawRouter](BlockRunAI--ClawRouter.md)

## Review guidance

- Review candidate: mine PicoClaw security config/redaction/MCP allowlist patterns.
