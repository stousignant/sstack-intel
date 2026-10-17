---
title: danielmiessler/LifeOS
type: repo-intel
aliases:
  - LifeOS
  - Personal_AI_Infrastructure
  - PAI upstream
  - "GitHub repo: danielmiessler/LifeOS"
  - "GitHub repo: danielmiessler/Personal_AI_Infrastructure"
source: https://github.com/danielmiessler/LifeOS
category: personal-ai-infrastructure
topics: [github-repo, pai, lifeos, claude-code, intent-engineering]
status: deep-analyzed
usefulness_score: 97
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-08-03
checked_ref: v7.28.3@36c6f01e9c2c515aaaf475b868aca7f3ffdf9c43
license: MIT
---

# danielmiessler/LifeOS

> Opinionated reference-stack evaluation, reviewed 2026-08-03. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Correct scope

LifeOS is a Claude Code life-system framework. This evaluation considers a staged migration from PAI 5.x to LifeOS 7.28.3, not installation into Hermes. Hermes remains the separate reference cockpit/orchestrator; the optional upstream Hermes sidecar is not a prerequisite.

## Decision

- **Verdict:** LifeOS `7.28.3` is worth a staged canary evaluation under the reference-stack lens, not a live bootstrap.
- **Expected payoff:** less response ceremony/context load, deterministic evidence gates, system/user separation, continuity/freshness, role-based model routing, and supported launcher/doctor/update operations. These are expected benefits, not measured improvements.
- **Primary risk:** additive deployment can mix old skill heads and new support files, duplicate hook generations, and miss legacy user data.
- **Migration principle:** fresh system plane first; explicitly port reviewed identity, user data and portable overlays; never merge framework generations file-additively.

## Evidence checked — 2026-08-03

### Upstream

- Repository: <https://github.com/danielmiessler/LifeOS>.
- Latest release: [`v7.28.3`](https://github.com/danielmiessler/LifeOS/releases/tag/v7.28.3), published 2026-08-01.
- Versions: LifeOS `7.28.3`, Algorithm `8.17.3`, Cortex/Memory `8.3.0`.
- Tag checked: `36c6f01e9c2c515aaaf475b868aca7f3ffdf9c43`; default-branch HEAD checked: `47df8eebf08d78a3ef5851ec2f9b751bae6558fb`.
- Sampled `INSTALL.md`, setup/update/migrate workflows, deploy/conflict tools, system prompt, Algorithm, hooks, skill library, USER schema, Doctor, Synapse, Cortex, Atlas, and release notes.
- `v5.0.0..v7.28.3` spans 2,438 changed files: this is not a rename-only upgrade.

### Baseline boundary

A migration needs a private inventory of existing framework versions, overlays, skills, hooks, user data, launcher behavior and health. Such measurements are not public upstream properties. The inspected upstream conflict detection, additive deployment and legacy-user-path limitations motivate the canary method below.

## What LifeOS 7.x offers the reference architecture

### 1. A radically smaller Algorithm without losing the ISA

Upstream Algorithm `8.17.3` is 98 lines; compare the incumbent prompt separately rather than assuming a particular local baseline.

LifeOS removes:

- NATIVE / ALGORITHM / MINIMAL mode classification;
- `/e1`–`/e5` effort-tier doctrine;
- hard thinking-capability counts and closed-enumeration compliance;
- mandatory phase-by-phase voice announcements;
- the seven-station response ceremony;
- mandatory Cato calls based solely on effort tier.

It preserves and strengthens the useful kernel:

- the principal's verbatim goal;
- an ISA before substantial building;
- atomic claims with falsifiers;
- anti-claims;
- modality-correct tool evidence;
- class sweeps for class-shaped defects;
- explicit ask-fidelity checks;
- independent second looks scaled to blast radius;
- durable resume from the ISA rather than transcript memory.

**Expected reference-stack effect:** less prompt tax and fewer chances to fail the framework cosmetically, while keeping useful agent evidence discipline.

### 2. One adaptive response format

LifeOS offers one response shape whose answer length adapts to the task, reducing mode-selection machinery.

**Expected reference-stack effect:** fewer mode misclassifications, less banner/phase noise, and more natural peer conversation without losing CHANGE/VERIFY evidence when the agent actually mutates something.

### 3. Deterministic enforcement at the right moments

The new hook plane includes `AlgorithmNudge`, ISA close/fold/stale-write gates, `VerificationGate`, `StopGates`, `KnowledgeWriteGuard`, memory-health surfaces, model-rung guard, skill-routing reminders, and system-change reporting.

When an incumbent relies on model-followed prose or old phase/tier vocabulary, deterministic gates can reduce reliance on prompt recall.

**Expected reference-stack effect:** less reliance on the agent remembering hundreds of lines, and more reliable blocking exactly where unsupported completion or stale state can occur.

### 4. Role-based model routing

LifeOS stores carrier facts in a model registry and writes durable doctrine in roles/rungs: primary judgment at the strongest rung, scoped execution downshifted when appropriate, Forge/Max elected by impact.

**Expected reference-stack effect:** fewer stale model names and better use of Claude Code's current native routing. Preserve the chosen coding-worker routing as an explicit reviewed overlay rather than inheriting upstream provider assumptions.

### 5. Better continuity and context freshness

Cortex adds hot context, typed knowledge, write-time schema advice, memory review/health, and context-freshness signals. TELOS moves toward one reviewed source plus generated derivatives rather than many loosely refreshed startup files.

**Expected reference-stack effect:** better awareness of stale goals/context and fewer silent malformed knowledge writes. Existing memory needs preservation and selective migration; blindly copying the whole runtime tree would carry years of obsolete state and old schemas forward.

### 6. A real system/user boundary

LifeOS makes `LIFEOS/` the replaceable framework plane and links `USER/` to a separate private configuration home. This aligns with a portable upstream-versus-personal-overlay separation.

**Expected reference-stack effect:** future upstream updates become safer—provided the existing overlay owner deliberately maps the new user-data paths rather than retaining legacy destinations.

### 7. Supported launcher, doctor, and update lifecycle

LifeOS has:

- a dedicated launcher that always appends `LIFEOS_SYSTEM_PROMPT.md`;
- capability states `live`, `broken`, `declined`, and `stale`;
- exact fix commands;
- dry-run-first installers;
- backup-before-write config operations;
- a release-aware 7.x update workflow.

**Expected reference-stack effect:** no more ambiguity over whether the constitutional prompt loaded, and easier diagnosis of browser, Codex, voice, or cloud capability gaps.

### 8. Optional new subsystems

Synapse, Atlas, ThreatModel, Ledger, and Upgrades are useful additions, but they are not the main reason to evaluate the framework. Start with Core, hooks, skills, identity/TELOS, Algorithm, and Cortex. Add optional systems only after the core canary is stable.

## Migration blockers found

1. **The 7.x Update workflow is not a PAI 5→LifeOS 7 migrator.** It assumes an existing `LIFEOS/VERSION` install and re-overlays 7.x system files.
2. **Direct core deployment would be Frankenstein-prone.** Exact-name skill directories are merged additively and existing files are not overwritten; old v5 skill heads could remain while v7 support files are added.
3. **Old user data is invisible to setup detection.** `ScanConflicts` sees `LIFEOS/USER`, not the legacy PAI user-data directory.
4. **The shipped Migrate skill is not safe as the sole schema migrator.** Its docs/tools still route split files such as `TELOS/GOALS.md`, while current LifeOS doctrine calls `TELOS/TELOS.md` canonical. Use it only after target-path testing or migrate deterministically ourselves.
5. **Hook union is not reconciliation.** `InstallHooks` preserves foreign hooks and adds LifeOS hooks. Running both full generations would duplicate security, lifecycle, context, voice, memory, and completion behavior.
6. **Overlay paths must move deliberately.** Agent instructions, settings, user data, shared skills and custom hooks need explicit old/new destination mapping.
7. **Linux optional-component reality differs from upstream's primary macOS path.** Pulse/launchd jobs are not drop-in Linux components; core Claude Code hooks are supported, but optional services need separate verification.

## Recommended migration shape

### Phase 0 — preserve and inventory

- Snapshot the default per-user Claude configuration directory, SStack links, settings semantics, PAI `USER/`, memory classes, skills, hooks, agents, launch command, and incumbent Claude Code smoke prompts.
- Preserve the incumbent launcher and framework as rollback truth.
- Define a small behavior eval: trivial answer, TELOS question, architecture judgment, multi-file coding task, PR review, stale-ISA resumption, SStack skill routing, and compaction recovery.

### Phase 1 — isolated LifeOS canary

- Install LifeOS into an isolated Claude config root and isolated USER config home using explicit dry-run/apply tools—not the live bootstrap.
- Prove the canary launcher loads the LifeOS constitutional prompt.
- Start from fresh v7 system skills and hooks. Do not copy v5 framework directories into them.
- Run Doctor and direct hook probes before involving real work.

### Phase 2 — deterministic user-data migration

- Map agent identity, principal identity, project context, operational rules, TELOS, and selected memory into the v7 schema with read-back diffs.
- Preserve the old PAI tree as an archive; promote only durable knowledge and active state.
- Re-project approved `sstack-*` shared skills into the canary.
- Port custom learning hooks only after comparing them against Cortex memory review and avoiding duplicate semantics.
- Reconcile named agents: retain only those that still earn a distinct job, rather than carrying obsolete roles forward.

### Phase 3 — comparative framework trial

- Run the same eval prompts through the incumbent PAI framework and LifeOS.
- Compare startup/context cost, completion time, answer naturalness, skill routing, tool evidence, false hook nudges, resume quality, and human preference.
- Require zero destructive/live-path mutations from the canary.

### Phase 4 — reviewed cutover

- Update SStack's Claude package and path ownership to the LifeOS layout.
- Replace—not union—the old framework hook/skill plane.
- Wire `pai` and/or `lifeos` to the new launcher while preserving subscription-safe authentication and the protected personal lane.
- Keep a one-command directory/launcher rollback until several real sessions pass.

## Recommendation matrix

| Candidate | Reference-stack recommendation | Why |
|---|---|---|
| LifeOS Core | Canary, then likely adopt | Evaluate the core mission before optional services. |
| Algorithm 8.17.3 | High-priority adoption in canary | Retains ISA/evidence while reducing ceremony and mode/tier brittleness. |
| Unified response format | Adopt unless the eval shows regression | Simpler presentation must not regress personality or mutation evidence. |
| Hook/close-gate plane | Replace by semantics, do not union | Duplicate generations can conflict. |
| Cortex | Adopt core in canary; migrate memory selectively | Health/freshness/schema feedback does not justify copying stale runtime state. |
| Role-based model doctrine | Preserve explicit local routing policy | Less model-name rot without inheriting provider assumptions. |
| USER separation | Deliberate source-owner path migration | Separates replaceable upstream system and reviewed personal data. |
| Pulse on Linux | Defer from first canary | Optional service deployment is not required to prove the core. |
| Synapse / Atlas / Hermes sidecar | Defer | Not prerequisites for the core evaluation. |

## Explicit non-goals

- No Hermes runtime/plugin changes as part of the framework evaluation.
- No direct bootstrap into the incumbent Claude configuration directory.
- No additive merge of PAI 5 and LifeOS 7 skills/hooks.
- No wholesale migration of logs, caches, failed-work transcripts, or stale runtime state.
- No replacement of SStack as the owner of deployment-specific portable overlays.

## Refresh trigger

Refresh after an isolated canary exists, after upstream fixes/clarifies PAI 5 migration and unified-TELOS migration paths, or on the next major LifeOS release.

## Related

- [LifeOS upstream framework](https://github.com/danielmiessler/LifeOS) — source architecture, release and migration guidance.
- [Hermes Agent](NousResearch--hermes-agent.md) — separate reference cockpit/orchestrator, not a LifeOS migration target.
