---
title: "siteboon/claudecodeui"
type: repo-intel
source: https://github.com/siteboon/claudecodeui
category: coding-tools
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: AGPL-3.0
---

# siteboon/claudecodeui

> Reference-stack evaluation as reviewed 2026-05-30; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision
- Usefulness score: `[('Stack fit', 20, 25, 'Strong mobile agent-control fit, but Claude/Cursor/Codex-centered rather than Hermes-native.'), ('Leverage', 22, 25, 'Could unlock mobile repo work and remote monitoring.'), ('Reuse readiness', 17, 20, 'Simple npm path and active releases, but safe deployment needs care.'), ('Maturity/trust', 12, 15, 'Active/high-star, but young and shell-exposing.'), ('Differentiation', 11, 15, 'Best mobile/web UI in this batch; less unique as runtime.')]/100` — CloudCLI / Claude Code UI is the strongest mobile/web agent-control surface in this batch, but its shell-capable web UI, agent CLIs, plugin install paths, optional cloud offering, and AGPL licensing make it unsuitable as a default.
- Recommendation: `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- Review candidate: Do not expose CloudCLI to real projects. If mobile agent control becomes urgent, sandbox it on a throwaway repo over Tailscale/localhost and compare it against Hermes Discord + Paperclip-style PWA patterns.

## Scorecard
| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 20/25 | Strong mobile agent-control fit, but Claude/Cursor/Codex-centered rather than Hermes-native. |
| Leverage | 22/25 | Could unlock mobile repo work and remote monitoring. |
| Reuse readiness | 17/20 | Simple npm path and active releases, but safe deployment needs care. |
| Maturity/trust | 12/15 | Active/high-star, but young and shell-exposing. |
| Differentiation | 11/15 | Best mobile/web UI in this batch; less unique as runtime. |

## Verdict

CloudCLI / Claude Code UI is the strongest mobile/web agent-control surface in this batch, but it is not a clean default because it mixes a shell-capable web UI, agent CLIs, plugin install paths, optional cloud offering, and AGPL licensing. Treat it as a UX and mobile-access pattern source first; sandbox only behind explicit network and project boundaries.

## Workload fit
- Mobile agent access is useful when chat-based control is too limited for repository work; this project remains a multi-agent UI reference rather than a Hermes replacement.
- Support for Claude Code, Cursor CLI, Codex, and Gemini offers broad UI coverage; no Hermes-native client is documented.
- The plugin tab model and responsive shell/chat/files UI are worth stealing for future Hermes/PAI control surfaces.

## What it is

A TypeScript React/Express web UI and npm CLI (`@cloudcli-ai/cloudcli`) for running coding agents from desktop/mobile browsers, with self-hosted and managed-cloud paths plus experimental Docker sandbox support.

## Evidence checked
- GitHub metadata via `gh repo view` on 2026-05-30: stars `11501`, forks `1562`, primary language `TypeScript`, archived `False`, fork `False`.
- Maintenance signal: pushed `2026-05-30T12:50:45Z`, updated `2026-05-30T22:29:24Z`, latest release `v1.32.0` `2026-05-13T12:02:29Z`.
- License: `AGPL-3.0` from GitHub/license file.
- README: `https://raw.githubusercontent.com/siteboon/claudecodeui/main/README.md`.
- Top-level manifests/docs inspected locally from the upstream repository: README, package/pyproject when present, license, security file when present, top-level contents.
- Repository topics: claude, claude-api, claude-code, gui, ui, anthropic, anthropic-ai, anthropic-claude, react, claudecode, mobile-first, claude-code-ui.

## Strengths
- Very active: pushed 2026-05-30; latest release v1.32.0 on 2026-05-13; ~11.5k stars / 1.6k forks at review time.
- Concrete quickstart: `npx @cloudcli-ai/cloudcli` or global npm install; package exposes a `cloudcli` binary.
- Broad agent support: README lists Claude Code, Cursor CLI, Codex, and Gemini CLI.
- Mobile-first UX is real product surface, not just a CLI wrapper.
- Security docs mention tool enablement and Docker sandbox mode, though they need local verification before trust.

## Risks / caveats
- AGPL-3.0: okay to study/sandbox, but avoid embedding code into private proprietary/portable SStack surfaces without license review.
- A browser-exposed shell + coding agent UI is a sharp tool; LAN/remote exposure requires auth, Tailscale/localhost, and throwaway-repo testing first.
- Cloud offering creates possible data-boundary confusion; keep local-first/private data requirements explicit when evaluating deployment.
- Plugin installation from git repos expands supply-chain risk.

## Integration ideas
- Distill mobile project picker + agent chat/files/terminal UX into Hermes design notes.
- Compare CloudCLI self-hosted mobile access with Paperclip PWA-style local web access before building anything custom.
- If sandboxed, start on a disposable scratch workspace or a non-sensitive clone and disable unnecessary tools and plugins.

## Alternatives / related repos
- [Claude Code Ecosystem Comparison](../comparisons/claude-code-ecosystem.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)
- [oraios/serena](oraios--serena.md)
- [microsoft/skills](microsoft--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)

## Review guidance
- Candidates above are evaluation guidance, not executable commitments or runtime adoption.

## Score breakdown

| Dimension | Score | Max | Note |
|---|---:|---:|---|
| Stack fit | 20 | 25 | Strong mobile agent-control fit, but Claude/Cursor/Codex-centered rather than Hermes-native. |
| Leverage | 22 | 25 | Could unlock mobile repo work and remote monitoring. |
| Reuse readiness | 17 | 20 | Simple npm path and active releases, but safe deployment needs care. |
| Maturity/trust | 12 | 15 | Active/high-star, but young and shell-exposing. |
| Differentiation | 11 | 15 | Best mobile/web UI in this batch; less unique as runtime. |
