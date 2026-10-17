---
title: openclaw/openclaw
type: repo-intel
aliases:
  - openclaw
  - OpenClaw
  - GitHub repo: openclaw/openclaw
source: https://github.com/openclaw/openclaw
category: personal-ai-gateway
status: deep-analyzed
usefulness_score: 88
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-05-25
license: MIT
tags: [github-repo, openclaw, ai-agent, gateway, personal-ai, reference]
---

# openclaw/openclaw

> Reference-stack evaluation as reviewed 2026-05-25; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `88/100` — very high reference value for personal AI gateway architecture, channel breadth, schema-driven config, plugin manifests, pairing, and multi-device nodes.
- **Recommendation:** `distill-pattern` — do not migrate the reference stack to OpenClaw on this dated evidence; mine it for patterns that can improve Hermes/GBrain/second-brain workflows.
- **Usage observed 2026-05-25:** `reference-only`.
- **Review candidate:** Study OpenClaw's gateway protocol, config schema UI, plugin manifest planning, and pairing UX as design references for Hermes/PAI improvements.

## Scorecard

| Factor | Points | Evidence |
|---|---:|---|
| Stack fit | 21/25 | Strong conceptual fit for personal AI across channels/devices, but the reference stack assumes Hermes as the primary runtime. |
| Leverage | 23/25 | Best reusable value is design leverage: gateway protocol, device/node model, schema-driven config, plugin metadata, pairing/security defaults. |
| Reuse readiness | 16/20 | Install/update/daemon/Docker story is mature, but the monorepo is large and fast-moving; direct adoption would create migration cost. |
| Maturity/trust | 14/15 | MIT, active, same-day commits/releases, formal docs, package and Docker story. Volatility is the caveat. |
| Differentiation | 14/15 | Stronger than Hermes as a multi-device gateway/product reference; weaker than Hermes as the reference stack’s local operator/retrieval runtime. |

## Verdict

OpenClaw is impressive, but the right move is **pattern distillation, not migration**. It is a gateway-first, Node/TypeScript, multi-device personal assistant platform with a formal WebSocket protocol, app/node model, broad messaging integrations, schema-driven configuration, a polished update/daemon story, and a strong plugin manifest system. The reference stack favors Hermes as the operator cockpit. The leverage is to borrow OpenClaw's protocol/product lessons into Hermes/PAI where they matter.

## What it is

OpenClaw is a self-hosted personal AI assistant/gateway. It runs as a local daemon, connects to messaging channels and device nodes, exposes a local Control UI, and coordinates agents/plugins/skills through a Node/TypeScript monorepo.

## Evidence checked

- GitHub: https://github.com/openclaw/openclaw
- Local temporary clone: a disposable source checkout
- Inspected commit: `9ca52ce3d93071a0adc597e6c6808d141e58cee0`
- Latest inspected commit subject: `[codex] improve iOS realtime talk mode (#86355)`
- GitHub metadata checked live on 2026-05-25: MIT, TypeScript, not archived, homepage `https://openclaw.ai`, release `v2026.5.22`, package version `2026.5.25`.
- Key files inspected: `README.md`, `package.json`, `openclaw.mjs`, `pnpm-workspace.yaml`, `docs/wiki/concepts/architecture.md`, `docs/gateway/protocol.md`, `docs/gateway/configuration.md`, `docs/plugins/architecture.md`, `docs/wiki/tools/skills.md`, `docs/install/docker.md`, `docs/install/updating.md`, `src/gateway/server.ts`, `src/gateway/server.impl.ts`, `src/plugin-sdk/plugin-entry.ts`, `extensions/*/openclaw.plugin.json`, `apps/*`, `ui/src/ui/views/*`.
- Repo size signal: cloned git pack about 1.31 GiB; manifest scan found 125 extension manifests and 23 explicit channel plugins.

## Architecture map

### 1. Gateway-first control plane

OpenClaw centers on a long-lived Gateway. CLI, web UI, macOS/iOS/Android/headless nodes, and messaging surfaces connect to the gateway over WebSocket, defaulting to localhost port `18789`.

The protocol uses JSON text frames:

- first frame: `connect`
- then `req`, `res`, and `event` messages
- clients/nodes declare roles, scopes, caps, and commands
- handshake includes shared-secret auth, pairing, nonce signing, policy limits, feature discovery, and plugin surface URLs

This is the most valuable pattern to steal: a typed, explicit local control plane rather than ad-hoc platform handlers.

### 2. Messaging/channel integrations

README lists many channels: WhatsApp, Telegram, Slack, Discord, Google Chat, Signal, iMessage, IRC, Microsoft Teams, Matrix, Feishu, LINE, Mattermost, Nextcloud Talk, Nostr, Synology Chat, Tlon, Twitch, Zalo, Zalo Personal, WeChat, QQ, WebChat.

Manifest scan found 23 explicit channel plugins: `clickclack`, `discord`, `feishu`, `googlechat`, `imessage`, `irc`, `line`, `matrix`, `mattermost`, `msteams`, `nextcloud-talk`, `nostr`, `qa-channel`, `qqbot`, `signal`, `slack`, `synology-chat`, `telegram`, `tlon`, `twitch`, `whatsapp`, `zalo`, `zalouser`.

Channel model includes DM policies (`pairing`, `allowlist`, `open`, `disabled`), group mention gating, visible-reply policy, and per-channel config under `channels.<provider>`.

### 3. Plugin/extension model

OpenClaw plugins are manifest-first. Static manifests describe capabilities, providers, channels, hooks, services, HTTP routes, CLI commands, and schemas before runtime loading.

Layers:

1. Manifest/discovery from configured paths, workspace roots, global plugin roots, bundled plugins.
2. Enablement/validation/blocking/exclusive slot planning.
3. Runtime loading in-process for native plugins, JS packages, and local TS fallback through Jiti.
4. Surface consumption by tools, channels, providers, hooks, routes, CLI commands, services.

Manifest scan found 60 provider IDs across 125 plugin manifests, including OpenAI, Anthropic, Google, Ollama, OpenRouter, Bedrock, XAI, Mistral, Qwen, DeepSeek, Groq, LM Studio, LiteLLM, vLLM, and SGLang.

### 4. Skills model

OpenClaw uses AgentSkills-compatible `SKILL.md` folders and a multi-root precedence model:

1. `<workspace>/skills`
2. `<workspace>/.agents/skills`
3. `~/.agents/skills`
4. `~/.openclaw/skills`
5. bundled skills
6. `skills.load.extraDirs`

It supports per-agent skill allowlists, plugin-shipped skills, ClawHub installs, Git/local installs, and optional archive uploads. Third-party skills are treated as untrusted content/code and docs recommend scanners/sandboxing.

### 5. Config/runtime layout

- Config: `~/.openclaw/openclaw.json` in JSON5.
- Override path: `OPENCLAW_CONFIG_PATH`.
- Workspace: `~/.openclaw/workspace` by default.
- Injected prompt files: `AGENTS.md`, `SOUL.md`, `TOOLS.md`.
- Config is strictly schema-validated; unknown or bad values can stop gateway startup.
- `openclaw doctor --fix` repairs/migrates common problems.
- Control UI renders config from live schemas.

### 6. Apps/nodes/UI

OpenClaw includes a Vite/TypeScript Control UI, Swift shared OpenClawKit, and app/node surfaces for macOS/iOS/Android/headless agents. Nodes can expose camera, canvas, screen, location, voice commands, and other device capabilities.

## Strengths

- **Gateway protocol discipline:** explicit WS protocol, roles, scopes, pairing, features, command caps, and schema model.
- **Productized channel story:** many channels, onboarding, daemon install, update channels, Docker images, Control UI.
- **Schema-driven config UX:** strict schema validation plus UI/config lookup is better for normal humans than editing YAML/JSON blindly.
- **Plugin metadata planning:** manifests enable discovery and validation before arbitrary code loads.
- **Device/node strategy:** mobile/mac/headless nodes are first-class, not bolted-on messaging adapters.
- **Security-aware channel defaults:** pairing/allowlist/group gating are good defaults for an assistant exposed to chat platforms.

## Risks / caveats

- **Huge fast-moving monorepo:** clone pack around 1.31 GiB, 125 extension manifests, same-day releases/commits; this is power plus volatility.
- **Many integrations can mean uneven depth:** 23+ channels and 60 provider IDs are hard to keep equally healthy.
- **Strict config can brick startup:** mitigated by `doctor`, but schema errors are sharp edges.
- **In-process plugins:** native plugins load into the host process; third-party plugin trust is real code-execution risk.
- **Modern Node requirement:** Node 22.19+ minimum / Node 24 recommended.
- **Direct migration cost is not justified right now:** the reference stack already assumes a capable Hermes cockpit and Markdown-vault retrieval.

## Patterns for the reference stack

1. **Typed gateway protocol and role/scopes model.** Hermes gateway could benefit from a clearer internal protocol boundary for clients/nodes/platforms.
2. **Schema-driven config UI.** Hermes has powerful config but discoverability is still CLI/doc-heavy.
3. **Manifest-first plugin planning.** More static metadata before runtime loading could make Hermes plugin startup safer and more inspectable.
4. **Pairing UX for unknown senders.** OpenClaw's DM pairing defaults are a strong personal-agent security pattern.
5. **Device nodes as a product concept.** For future mobile/local device work, OpenClaw is the reference.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — preferred runtime under this reference-stack evaluation.
- [hesamsheikh/awesome-openclaw-usecases](hesamsheikh--awesome-openclaw-usecases.md) — idea catalog around OpenClaw use cases.
- [abhi1693/openclaw-mission-control](abhi1693--openclaw-mission-control.md) — related OpenClaw ecosystem note.

## Review guidance

- Use [hermes vs openclaw](../comparisons/hermes-vs-openclaw.md) before making migration decisions.
- If designing Hermes/PAI gateway improvements, read OpenClaw `docs/gateway/protocol.md`, `docs/gateway/configuration.md`, and `docs/plugins/architecture.md` first.
- Treat third-party OpenClaw plugins/skills as untrusted until individually audited.
