---
title: Agent Skill Overlays and Upstream Drift
created: 2026-06-15
updated: 2026-09-07
type: concept
status: active
tags: [ai, agents, skills, hermes, skill-ownership, upstream-tracking, governance, sstack]
sources:
  - https://docs.anthropic.com/en/docs/claude-code/skills
  - https://agentskills.io/specification.md
  - https://agentskills.io/skill-creation/best-practices.md
  - https://agentskills.io/client-implementation/adding-skills-support.md
  - https://developers.openai.com/codex/concepts/customization
  - https://developers.openai.com/codex/config-basic
  - https://github.com/obra/superpowers
  - wiki/concepts/ai-engineering/coding-agent-skill-systems.md
  - wiki/concepts/ai-engineering/thin-harness-fat-skills.md
  - https://github.com/NousResearch/hermes-agent
confidence: high
last_reviewed: 2026-09-07
review_cadence: quarterly
---

# Agent Skill Overlays and Upstream Drift

> Reference-stack lens: [AI engineering](index.md).

## Core verdict

The current agent-skills ecosystem does **not** have a mature first-class standard for “inherit upstream skill X and override section Y.” The practical ecosystem answer is instead:

1. keep upstream/plugin skills pristine and updateable;
2. put local/project/team behavior in separate skill layers or instruction layers;
3. disable or hide upstream skills through host settings when necessary;
4. fork/vendor only when the local version is intentionally divergent;
5. preserve unavoidable direct edits as explicit patches, not invisible local mutations.

For the Hermes reference stack, this boundary is expressed as:

```text
upstream skill unchanged
+ explicitly owned companion/replacement overlay skill
+ explicit patch queue only when unavoidable
+ drift audit / guardrail
```

This is the missing discipline around [Coding Agent Skill Systems](coding-agent-skill-systems.md): agent skills are becoming portable, but overlay governance is still mostly an operator convention rather than a platform primitive.

## Why this matters

Agent skills are valuable because they package reusable procedures, domain heuristics, scripts, references, and verification loops into reviewable files. That also makes them easy to accidentally fork.

A locally edited upstream-looking skill creates a **shadow fork**: future agents cannot tell whether the file is pristine upstream content, operator-specific policy, a stale local experiment, or critical runtime behavior. Shadow forks block safe upgrades and turn skill maintenance into archaeology.

The durable question is not “how do I keep my modified copy?” It is:

> Which parts belong to upstream, which parts belong to the operator, and which deltas are small enough to carry as explicit patches?

## Ecosystem findings

### Agent Skills open standard

The Agent Skills standard defines the portable shape of a skill:

```text
skill-name/
├── SKILL.md
├── scripts/
├── references/
├── assets/
└── ...
```

`SKILL.md` requires YAML frontmatter with `name` and `description`; optional fields include `license`, `compatibility`, arbitrary `metadata`, and experimental `allowed-tools`. [Source: Agent Skills Specification, 2026-06-15]

Important consequence: the standard gives the owned skill repository a legitimate place to encode overlay metadata, for example:

```yaml
metadata:
  owner:
    overlay_type: companion
    overlay_for:
      - plugin-name:skill-name
      - upstream/repo/path
```

But the standard does **not** define merge semantics, dependency resolution, override order, patch application, or conflict handling. Overlay behavior must be implemented by the host runtime, repository policy, or external tooling.

### Claude Code skills

Claude Code’s skill docs support multiple locations:

| Scope | Path / mechanism | Meaning |
|---|---|---|
| Enterprise | managed settings | organization-wide |
| Personal | the user-level Claude skills directory (see the cited official documentation) | all user projects |
| Project | `.claude/skills/<skill-name>/SKILL.md` | one project |
| Plugin | `<plugin>/skills/<skill-name>/SKILL.md` | where plugin is enabled |

When skills share the same name across non-plugin levels, Claude Code says enterprise overrides personal, and personal overrides project. Plugin skills use a `plugin-name:skill-name` namespace, so they cannot conflict with the other levels. [Source: Claude Code Skills docs, 2026-06-15]

Claude also has `skillOverrides` in settings for skills whose `SKILL.md` should not be edited, such as shared project skills or MCP-provided skills. Values include `on`, `name-only`, `user-invocable-only`, and `off`. [Source: Claude Code Skills docs, 2026-06-15]

Interpretation: Claude supports **visibility and precedence**, not true skill inheritance. The intended safe customization path is to create local skills or adjust visibility, not mutate shared/upstream skill files.

### Codex customization

Codex frames customization as complementary layers: `AGENTS.md` for persistent project guidance, memories for learned context, skills for reusable workflows and domain expertise, MCP for external systems, and subagents for delegation. [Source: Codex Customization docs, 2026-06-15]

Codex docs state that local skill folders are for authoring and iteration; plugins are the installable distribution unit. If a plugin already exists for a workflow, install it first; package your own workflow as a plugin when distributing across teams. [Source: Codex Customization docs, 2026-06-15]

Codex config has precedence layers — CLI overrides, project config, profiles, user config, system config, built-ins — but this is configuration layering, not skill-content merging. [Source: Codex Config Basics, 2026-06-15]

Interpretation: Codex validates the split between always-on instructions, local skills, and plugin distribution. It does not solve upstream-skill overlays directly.

### Superpowers and multi-harness skillpacks

`obra/superpowers` is a real-world skillpack distributed across Claude Code, Codex, Cursor, Gemini, OpenCode, and other harnesses. It ships a root `skills/` directory plus harness-specific plugin metadata such as `.claude-plugin/plugin.json`, `.codex-plugin/plugin.json`, and `.cursor-plugin/plugin.json`. [Source: `obra/superpowers`, 2026-06-15]

The repo shape treats skills as portable upstream artifacts and plugins as distribution surfaces. It does not expose a user-local overlay protocol for customizing upstream skills in place.

For a skill repository that maintains host-specific overlays, external skillpacks like Superpowers are usually pattern sources or pristine dependencies. Environment-specific changes belong in separately owned skills, not as edits inside the upstream skillpack.

## Reference-stack operating model

### Lane A — Upstream pristine

Bundled or upstream skill content should stay resettable and updateable. Examples:

```text
harness-bundled skills
installed upstream-looking skills
external plugin/skillpack checkouts
```

Do not preserve durable environment-specific behavior only by editing these files. If a file looks upstream-owned, maintainers should be able to restore it from upstream without losing local operating policy.

### Lane B — owned companion overlays

environment-specific procedures, local paths, review standards, reference-stack routing, GBrain/second-brain behavior, and Hermes cockpit policy should live in owned skills:

```text
shared-policy-repository/skills/shared/<owned-skill>
shared-policy-repository/skills/<harness>/<owned-skill>
```

Use this metadata pattern:

```yaml
metadata:
  owner:
    overlay_type: companion
    overlay_for:
      - upstream-skill-or-plugin:skill-name
    reason: "What local behavior this preserves and why it should not be upstream-edited."
```

A companion overlay should say “when using upstream X in this environment, additionally follow Y.” It should not duplicate the whole upstream skill.

### Lane C — owned replacements

If an upstream skill is wrong-fit and a deployment needs a local version instead, do not silently shadow it. Disable or hide the upstream skill where the host supports that, and declare the local replacement explicitly:

```yaml
metadata:
  owner:
    overlay_type: replacement
    replaces:
      - plugin-name:skill-name
    reason: "Why the upstream behavior is not safe or aligned for this deployment."
```

Replacement should be rare. Most useful upstream ideas should become companion overlays or distilled shared skills.

### Lane D — Explicit patch queue

Tiny unavoidable direct edits to bundled/upstream skills should be recorded as patch records, not invisible hand edits.

Recommended path:

```text
shared-policy-repository/patches/<harness>-skills/
  registry.yaml
  <upstream-skill>.patch
```

Patch records should include:

- upstream URL/path and baseline commit/tag/date;
- why the patch exists;
- exact diff or reapply instruction;
- verification command;
- retirement condition.

If a patch grows beyond a small localized delta, extract it into an overlay or fork the skillpack deliberately.

### Lane E — Deliberate fork/vendor

A fork is appropriate only when a project intentionally owns a modified skillpack variant and wants to rebase/cherry-pick local commits over upstream. This is heavier than overlays and should have explicit provenance, update procedure, and conflict-resolution policy.

## Decision matrix

| Situation | Default action | Why |
|---|---|---|
| Upstream skill is useful as-is | install/use it pristine | preserves update path |
| Need operator-specific local behavior | create or update `<owned-prefix>-*` companion overlay | keeps local policy portable and visible |
| Upstream skill should not be used | disable/hide upstream skill and create explicit replacement | avoids name-shadowing ambiguity |
| Need one tiny direct delta | register a patch under `patches/hermes-skills/` | makes the mutation replayable and reviewable |
| Need many semantic changes | fork/vendor deliberately | admits that we now own a divergent variant |
| Just like an upstream idea | distill method into existing owned skill | avoids importing another operating system |
| Need current project conventions | put in repo instructions such as `AGENTS.md` / project context | avoids overloading global skills |
| Need deterministic mechanics | write script/hook/validator | skills are guidance, not hard enforcement |

## Drift audit requirements

A managed skill layer should fail or warn on undocumented drift:

```text
modified upstream-looking skill
without either:
  - matching sstack overlay/replacement metadata, or
  - active/needs-review patch registry entry
```

The acceptance state is:

1. upstream skills come from upstream;
2. owned skills come from owned skill repository;
3. direct local deltas are explicit patch records;
4. generated/runtime skill files are disposable;
5. drift reports can explain every local hunk as extracted, patched, restored, discarded, or intentionally forked.

## Practical update workflow

When refreshing upstream skills or skillpacks:

1. Snapshot current installed/runtime skill files.
2. Compare installed content to upstream/current target release.
3. Classify each delta:
   - `owned-overlay`
   - `owned-replacement`
   - `hermes-skill-patch`
   - `restore-from-upstream`
   - `discard-stale`
   - `fork/vendor`
4. Extract reusable local behavior into shared skills before resetting upstream-looking files.
5. Record patch records for unavoidable direct edits.
6. Update/reinstall upstream.
7. Reapply/review patches.
8. Run drift audit and skill validators.
9. Verify the relevant skill resolves/loads in the actual runtime.
10. Commit only the logical owned skill repository/vault changes; do not commit runtime caches, backups, or unmodified upstream copies.

## Reference-stack doctrine

For the reference stack, “thin harness, fat skills” does not mean “every skill file grows forever.” It means the **right** skill layer owns the right doctrine:

- upstream skillpacks own generic reusable methods;
- owned skill repository owns Reference-stack/GBrain/second-brain-specific operating policy;
- second-brain pages own durable architecture, rationale, and source-backed concepts;
- scripts/hooks own deterministic enforcement;
- GitHub Issues/Projects own executable work state; owned specification bridge may prepare reviewed work orders. Retired planning systems are history, not active routing.

The strongest pattern is **distillation over mutation**: inspect upstream skills, copy the useful technique into an existing owned skill repository owner skill with provenance, and leave the upstream package updateable.

## Related

- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Thin Harness, Fat Skills](thin-harness-fat-skills.md)
- [Meta-Meta-Prompting](meta-meta-prompting.md)
- [Harness Engineering](harness-engineering.md)
- [Hermes Agent](https://github.com/NousResearch/hermes-agent)
- [agent skills ecosystem](../../intel/github-repos/comparisons/agent-skills-ecosystem.md)
