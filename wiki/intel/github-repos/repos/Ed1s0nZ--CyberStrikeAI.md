---
title: Ed1s0nZ/CyberStrikeAI
type: repo-intel
aliases: [CyberStrikeAI, GitHub repo: Ed1s0nZ/CyberStrikeAI]
source: https://github.com/Ed1s0nZ/CyberStrikeAI
category: security-containment-agent-safety
topics: [github-repo, cybersecurity, offensive-security, mcp, hitl, audit-log]
status: deep-analyzed
usefulness_score: 42
recommendation: reference-only
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-03
license: Apache-2.0
---

# Ed1s0nZ/CyberStrikeAI

> Reference-stack evaluation as reviewed 2026-06-03. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `42/100` — dual-use/offensive platform with some defensive UX patterns; not suitable as Hermes infrastructure.
- **Recommendation:** `reference-only` for defensive HITL/audit/tool-allowlist patterns; explicitly reject C2/webshell/offensive prompt patterns.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Extract only audit, HITL approval, role restriction, and tool allowlist ideas; blacklist offensive orchestration patterns.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 8/25 | Mostly offensive security platform, not Hermes containment. |
| Leverage | 10/25 | Some audit/HITL patterns are useful. |
| Reuse readiness | 9/20 | Go app with many tools, but risky surface. |
| Maturity/trust | 8/15 | Active and substantial; prompts conflict with safe-agent posture. |
| Differentiation | 12/15 | Comprehensive security-testing orchestration, but misaligned. |

## Verdict

CyberStrikeAI is a hard no as a Hermes install candidate. It is a dual-use/offensive security platform with C2, webshell, implants, offensive roles, and prompt language that conflicts with conservative agent control. The only useful payload is defensive: audit logs, human approvals, tool allowlists, role restrictions, and maybe MCP auth patterns.

## Workload fit

- Shows what not to allow in general-purpose agent infrastructure.
- Defensive HITL/audit UX can be useful for security-sensitive actions.
- Good reminder that “AI security tool” often means offensive automation, not containment.

## What it is

An AI-native security testing platform in Go with 100+ security tool recipes, MCP, web UI, audit/history, roles, skills, multi-agent orchestration, and offensive security capabilities.

## Evidence checked

- GitHub metadata on 2026-06-03: ~4.1k stars, pushed 2026-06-03.
- README, license, root files under [upstream repository inspection](https://github.com/Ed1s0nZ/CyberStrikeAI).
- Repomix pack: a temporary Repomix inspection pack — 483 files / ~734k tokens; 1 suspicious file excluded; read selectively.
- Targeted evidence: MCP HTTP/stdio/SSE, web UI auth, generated password/token behavior, timeout/sandbox guards, audit/history, HITL approval, tool allowlists, offensive C2/webshell/implant/task/payload surfaces and aggressive prompts.

## Strengths

- Comprehensive security-tool orchestration and audit concepts.
- HITL approval and role restrictions are useful patterns.
- Apache-2.0 license and active codebase.

## Risks / caveats

- Explicit C2/webshell/offensive platform surface.
- Prompt language includes “do not wait for approval” style instructions.
- Sandbox appears to be mostly process/timeouts, not robust isolation.
- Can expose MCP and many system tools; misuse risk is high.

## Integration ideas

- Add “never import C2/webshell/offensive-agent patterns” as a containment design red flag.
- Borrow audit/HITL UI ideas only after stripping offensive semantics.

## Alternatives / related repos

- [scitix/siclaw](scitix--siclaw.md)
- [NVIDIA/OpenShell](NVIDIA--OpenShell.md)
- [nearai/ironclaw](nearai--ironclaw.md)

## Review candidates and context

- Candidate: capture defensive HITL/audit patterns and blacklist offensive CyberStrikeAI patterns for Hermes.
