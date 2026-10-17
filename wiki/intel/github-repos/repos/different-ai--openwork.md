---
title: different-ai/openwork
type: repo-intel
aliases: [openwork, GitHub repo: different-ai/openwork]
source: https://github.com/different-ai/openwork
category: agent-work-orchestration
topics: [github-repo, opencode, desktop-agent-control, cowork, permissions, web-ui]
status: deep-analyzed
usefulness_score: 82
recommendation: watch
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: other
---

# different-ai/openwork

> Opinionated reference-stack evaluation, reviewed 2026-06-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — valuable desktop/web control-plane reference, but license ambiguity and broad shell/session surface make it watch/sandbox-only.
- **Recommendation:** `watch`; distill permission/session UX patterns before adopting anything.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Compare its desktop/web/session/permission model against Discord + Hermes gateway + Kanban before considering a mobile/control-plane spike.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Similar to mobile/web agent-control needs, but powered by OpenCode not Hermes. |
| Leverage | 21/25 | Could inspire better long-task visibility and permission UX. |
| Reuse readiness | 12/20 | Large pnpm monorepo, desktop/web/server pieces, unclear license. |
| Maturity/trust | 13/15 | Active, lots of scripts/tests/docs; broad security surface. |
| Differentiation | 16/15 | Strong control-plane shape; capped to 15 in rubric. |

## Verdict

OpenWork is a good reference for “agent cowork/control plane” UX: sessions, permissions, event streams, desktop/web modes, and remote workers. It is not the first thing to adopt because the reference architecture uses Hermes with interaction/local tools, and exposing shell/agent sessions through a UI needs careful auth, Tailscale/local-only boundaries, and approval semantics.

## Reference-stack relevance

- Directly related to mobile/desktop visibility for long-running agent tasks.
- Permission prompts and execution timelines could improve Hermes UX.
- Shows how an OpenCode-backed agent control plane is structured.

## What it is

An open-source alternative to Claude Cowork powered by OpenCode. The repo is a large pnpm workspace with desktop app, web/local development scripts, API/inference services, packages, docs, examples, and permission/session tests.

## Evidence checked

- GitHub metadata on 2026-06-03: license reported as `other`, ~15.7k stars, pushed 2026-06-03.
- Root files: `.opencode`, apps, packages, `ee`, evals, docs, examples, PRDs, `SECURITY.md`, `AGENTS.md`.
- Package scripts: desktop/web dev modes, local API/inference services, Docker/dev sandbox, tests for sessions/permissions/fs-engine/e2e.
- Repomix pack: a temporary Repomix evidence pack — huge pack (~2.1M tokens); read selectively only.

## Strengths

- Strong session/control-plane UX surface for agent work.
- Explicit permission, session, fs-engine, and e2e test scripts.
- Composable desktop/web/headless shape is useful as a design reference.

## Risks / caveats

- License ambiguity needs review before reuse.
- Broad shell/agent/remote-worker surface is security-sensitive.
- Powered by OpenCode; adopting would add another runtime/control plane beside Hermes.

## Integration ideas

- Distill permission timeline and session visibility into Hermes gateway/Kanban UX ideas.
- Compare against Paperclip PWA/mobile pattern and Discord-first control.
- Only sandbox behind local/Tailscale boundaries on a throwaway repo.

## Alternatives / related repos

- [siteboon/claudecodeui](siteboon--claudecodeui.md)
- [paperclipai/paperclip](paperclipai--paperclip.md)
- [OpenHands/OpenHands](OpenHands--OpenHands.md)
- [agent0ai/agent-zero](agent0ai--agent-zero.md)

## Review candidates and context

- Non-binding candidate: decide whether a Hermes mobile/web control-plane spike is justified after simpler Discord/Kanban UX improvements.
