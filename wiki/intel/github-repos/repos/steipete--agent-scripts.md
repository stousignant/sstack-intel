---
title: steipete/agent-scripts
type: repo-intel
aliases: [agent-scripts, GitHub repo: steipete/agent-scripts]
source: https://github.com/steipete/agent-scripts
category: agent-work-orchestration
topics: [github-repo, shared-skills, agent-instructions, portable-scripts, cross-harness, maintainer-orchestration]
status: deep-analyzed
usefulness_score: 90
recommendation: distill-pattern
usage: pattern-in-use
score_confidence: high
last_reviewed: 2026-06-13
license: MIT
---

# steipete/agent-scripts

> Reference-stack evaluation as reviewed 2026-06-13; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `90/100` — highly relevant as a real-world shared agent-rules/skills/scripts repo, now with explicit maintainer-orchestration semantics for an autonomous repo-maintenance loop.
- **Recommendation:** `distill-pattern`, especially pointer-style `AGENTS.MD`, skill validation, repo-owned skill symlinks, portable helpers, and the maintainer-orchestrator decision-ready queue protocol.
- **Usage observed 2026-06-13:** `pattern-in-use` — the shared-source/projected-harness pattern matches the reference architecture; autonomous queue triage, worker monitoring and decision-ready handoffs add useful detail.
- **Review candidate:** Compare its validation/pointer/symlink conventions and `maintainer-orchestrator` queue semantics against SStack shared skills / Hermes delegation lanes; patch only clear gaps.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 25/25 | Directly matches shared-skill and autonomous-maintainer workflows. |
| Leverage | 23/25 | Could reduce drift across Hermes/Codex/Claude/OpenCode instructions and sharpen owner-decision handoffs. |
| Reuse readiness | 18/20 | MIT, small scripts, clear README, dependency-light; personal/macOS paths require adaptation. |
| Maturity/trust | 13/15 | Personal production repo, active, validation hooks, recent push; still requires selective use. |
| Differentiation | 11/15 | Strong concrete operational pattern, but overlaps SStack/Hermes. |

## Verdict

This is not something to install wholesale. It is a useful proof that the SStack direction is correct: a canonical repo for shared hard rules, skills, hooks, helper scripts, and downstream pointer files, with repo-owned skills exposed by symlink rather than copied. The extra 2026-06-13 signal is the `maintainer-orchestrator` skill: it encodes the exact autonomous-maintainer loop from the tweet — scan queues, classify autonomous vs owner-needed work, delegate workers, poll every five minutes when authorized, drive PRs to tests/review/CI/mergeability, and ask the owner only for a concrete land/delete/access/product decision.

The value is pattern distillation into Hermes/SStack, not adopting this maintainer's personal repo as a new source of truth.

## Reference-stack relevance

- Relevant to sharing skills across Hermes, Claude Code, Codex, OpenCode, and other harnesses.
- Provides concrete conventions for pointer-style `AGENTS.MD`/`CLAUDE.md` and skill symlinks.
- Has a simple `scripts/validate-skills` pattern SStack can compare against.
- The `maintainer-orchestrator` skill is a strong reference for autonomous repo maintenance: queue triage, worker delegation, decision-ready PRs, owner-brief requirements, live-proof gates, CI/merge gates, and exact authorization boundaries.
- It validates a near-term Hermes design direction: let agents do the boring repo maintenance, but preserve hard human gates for product/security/access/destructive decisions.

## What it is

A personal canonical repo for shared agent instructions, skills, small helper scripts, hooks, and maintainer workflows. It exposes real skills via symlinks and asks downstream repos to point at the shared rule file instead of copying it.

Current README scope includes:

- `AGENTS.MD`: shared hard rules for Codex/Claude-style agents.
- `skills/`: reusable workflow skills, including repo-owned skills exposed by symlink.
- `scripts/`: dependency-light helpers used across projects.
- `hooks/`: local guardrails such as skill validation.

## Evidence checked

- GitHub metadata refreshed 2026-06-13: MIT license, 4,869 stars, 410 forks, `ai-agents` topic, default branch `main`, pushed 2026-06-12, not archived.
- README refreshed 2026-06-13: canonical `AGENTS.MD`, `skills/`, `scripts/`, `hooks/`, symlinked skills, validation, and downstream pointer pattern.
- Local shallow clone generated at a disposable source checkout on 2026-06-13 for targeted inspection.
- Previously generated repomix pack from 2026-06-03: a temporary source pack of the public repository — 129 files / ~119k tokens; no suspicious files detected.
- Inspected high-signal files: `README.md`, `AGENTS.MD`, `scripts/validate-skills`, `scripts/committer`, `docs/concurrency.md`, `docs/subagent.md`, `docs/slash-commands.md`, `skills/maintainer-orchestrator/SKILL.md`, `skills/clawsweeper-status/SKILL.md`, `skills/github-deep-review/SKILL.md`.

## Tweet-claim calibration

The tweet's headline version is directionally right but compressed. The repo itself contains:

- **Verified from repo:** a `maintainer-orchestrator` skill that says to scan open issues/PRs/CI/releases, classify `Autonomous` vs `Needs owner`, delegate repository workers, monitor every five minutes when continuous orchestration is requested, prepare decision-ready PRs, run tests/live proof/autoreview/CI gates, and ask the owner only for exact decisions.
- **Verified from repo:** `clawsweeper-status` queries GitHub Actions/issue comments/events for active workflows, merged PRs, reviews, comments, and closed work.
- **Verified from repo:** `github-deep-review` encodes code-aware issue/PR review, root-cause analysis, proof, risk, and no-mutation-without-request rules.
- **Not fully verified from this repo alone:** an always-on cron/service that wakes every five minutes and automatically merges everything. The repo documents the operating contract and skills; the live deployment details likely live in Peter's external setup / ClawSweeper automation.

## Strengths

- Keeps shared instructions canonical instead of copy-pasted.
- Validates skill frontmatter and structure before commits.
- Treats helper scripts as portable, dependency-light building blocks.
- Uses symlinks to expose repo-owned skills without moving ownership.
- Encodes a mature owner-decision protocol: do autonomous work first, then ask for one exact decision with proof and recommendation.
- Separates triage, delegation, implementation, push, CI repair, merge/close, and release permissions.

## Risks / caveats

- Personal Mac-heavy workflows do not all transfer to a Linux/Hermes environment.
- Copying the whole skill corpus would create noise; only patterns matter.
- SStack already owns the canonical shared-skill problem, so this should not become a second source of truth.
- Maintainer automation is high-risk if authorization, live-proof, CI, and merge boundaries are weakened.
- The repo documents parts of the loop, but does not by itself prove the whole external auto-merge deployment described in the tweet.

## Skill distillation pass

The key distillation findings are retained below; upstream [maintainer-orchestrator](https://github.com/steipete/agent-scripts/tree/main/skills/maintainer-orchestrator) supplies the public source context.

**Bottom line:** no Hermes-native plugin found. The repo is strongly OpenClaw/Codex/Claude/Cursor-oriented and has several OpenClaw-native skills, but should feed SStack as pattern inspiration rather than become a live dependency.

Most useful artifacts:

| Area | Best upstream artifacts | Potential action |
|---|---|---|
| Hooks | `hooks/pre-commit` → `scripts/validate-skills` | Distill “validate skills at commit boundary” into SStack guardrails; upstream validator is Ruby and minimal. |
| Agent descriptors | `skills/*/agents/openai.yaml` | Copy the idea of a tiny machine-readable skill/agent routing layer: display name, short description, default prompt. |
| Maintainer automation | `maintainer-orchestrator`, `github-project-triage`, `github-deep-review`, `clawsweeper-status` | Highest-value pattern cluster: queue triage, autonomous-vs-owner classification, worker monitoring, decision-ready PRs, proof/CI gates, exact owner choices. |
| GitHub hygiene | `github-cache-hygiene`, `github-author-context`, `github-project-triage/scripts/github-activity.sh` | Patch SStack GitHub ops with cache-first reads, author trust context, URL-first cards, and final live read before writes. |
| Skill hygiene | `skill-cleaner` + script | Strong candidate for SStack/Hermes skill drift audits: duplicate skills, unused candidates, prompt-budget pressure, loaded roots. |
| Browser/MCP-adjacent | `browser-use`, `scripts/browser-tools.ts` | Useful fallback patterns: prefer real logged-in Chrome profile; `browser-tools.ts` is a standalone DevTools CLI, not a Hermes plugin. |
| OpenClaw bridge | `openclaw-relay`, `discord-clawd`, `agent-transcript` | Runtime review only if Hermes ↔ OpenClaw bridging is needed for a concrete workload; not a casual install. |

### June 13, 2026 inspection provenance and additional findings

The distillation was checked against upstream commit `a3026aea93b9bc572f7a238212c6e7f69bdb82ec` (MIT), whose latest inspected commit was `docs: suppress archived repositories in orchestration` on June 12, 2026. These findings are a historical source review, not a refreshed upstream evaluation or installation claim.

- **Validation limitation:** `scripts/validate-skills` is Ruby; the inspection host lacked Ruby, so the validator was read but not executed. It checks skill frontmatter, required fields and duplicate names. Only one Git hook was found: `hooks/pre-commit`.
- **Descriptor boundary:** `skills/*/agents/openai.yaml` supplies display names, short descriptions and default prompts, not full agent implementations.
- **Browser distinction:** `browser-use` prefers a callable Codex Chrome plugin, then `mcporter chrome-devtools`; `scripts/browser-tools.ts` is a standalone Chrome DevTools CLI advertised as requiring no MCP. Existing-profile browser access is distinct from an isolated browser session.
- **Additional review patterns:** `github-deep-review` combines root cause, provenance, best fix, proof, risk and refactor judgment. `github-author-context` supplies contributor context; trust can change review depth, not correctness. `github-cache-hygiene` favors bounded cache-first reads and fresh final reads before writes.
- **Operational scripts:** `scripts/committer` stages explicitly listed files and runs validation; `skills/clawsweeper-status/scripts/clawsweeper-status.sh` provides bounded automation-status evidence; `skills/github-project-triage/scripts/github-activity.sh` summarizes contributor activity; `skills/skill-cleaner/scripts/skill-cleaner.ts` examines duplicate, unused and prompt-budget-heavy skills.
- **Runtime and privacy boundaries:** `skills/openclaw-relay/scripts/openclaw_relay.py` is a local/SSH ACP relay into OpenClaw, not a Hermes plugin. `skills/agent-transcript/scripts/agent-transcript` finds and redacts transcripts for issue/PR provenance; adopting that pattern requires privacy review.
- **Other skill references:** `create-cli` covers arguments, help, output, errors, configuration and dry-run UX. `one-password` favors service accounts and targeted secret read/store/injection rather than broad enumeration. Mac/iOS and product/account-specific skills are not general-purpose imports.
- **Slash-command references:** `fixissue.md` covers end-to-end issue delivery; `landpr.md` / `acceptpr.md` cover PR landing gates; `sectriage.md` covers security-advisory triage; `pickup.md` / `handoff.md` cover session continuity; `raise.md` covers changelog version-section bumps. These are source patterns, not permission to execute them.

The June 13 pass installed no runtime hook, enabled no auto-merge, imported no skill corpus and made no SStack skill changes. Its proposals remained review candidates, not adopted operating doctrine.

Compatibility snapshot:

- **Hermes plugin:** none found.
- **Hermes skills:** partially portable after adaptation; do not import raw personal skills.
- **OpenClaw:** strong compatibility in `openclaw-relay`, `discord-clawd`, `agent-transcript`, `clawsweeper-status`, and OpenClaw account/deployment rules.
- **Codex/OpenAI agents:** `agents/openai.yaml` descriptors are directly relevant as a simple agent-discovery/projection pattern.
- **Claude/Cursor:** README documents shared skill/instruction symlink patterns and slash-command docs for `.claude/commands` / `.cursor/commands`.

## Integration ideas

- Add/verify SStack equivalents for pointer files, validation scripts, generated harness outputs, and repo-owned skill projection.
- Compare `scripts/committer` with the existing skill-validation-before-commit policy.
- Distill a cross-harness shared-skill README from this plus gstack.
- Mine `maintainer-orchestrator` for Hermes/GitHub Project operating-board semantics: autonomous item classification, worker contracts, decision briefs, polling rules, owner-only gates, live-proof requirements, and public model identifier audits.
- Consider a Hermes cron/Project lane later, but only with explicit authorization boundaries and review-gated PR flow; do not jump straight to auto-merge.
- Proposed first SStack patch batch, if approved: `maintainer-orchestrator`, `github-project-triage`, `github-deep-review`, `skill-cleaner`, and `browser-use` patterns into existing SStack owner skills.

## Alternatives / related repos

- [garrytan/gstack](garrytan--gstack.md)
- [microsoft/skills](microsoft--skills.md)
- [mattpocock/skills](mattpocock--skills.md)
- [addyosmani/agent-skills](addyosmani--agent-skills.md)
- [automazeio/ccpm](automazeio--ccpm.md)
- [coleam00/Archon](coleam00--Archon.md)

## Review guidance

- Review candidate: compare `agent-scripts` conventions against SStack shared-skill generation/projection.
- Candidate follow-up: extract a SStack/Hermes “autonomous repo maintainer lane” design note from `maintainer-orchestrator`, but keep it review-gated and Project-backed rather than auto-merge by default.
