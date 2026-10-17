---
title: Salomondiei08/oh-my-hermes
type: repo-intel
aliases:
  - oh-my-hermes
  - Oh My Hermes
  - GitHub repo: Salomondiei08/oh-my-hermes
source: https://github.com/Salomondiei08/oh-my-hermes
category: hermes-extension
status: deep-analyzed
usefulness_score: 78
recommendation: distill-pattern
usage: reference-only
score_confidence: high
last_reviewed: 2026-06-08
license: NOASSERTION
tags: [github-repo, hermes, skills, app-building, agent-workflows]
---

# Salomondiei08/oh-my-hermes

> Reference-stack evaluation as reviewed 2026-06-08. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `78/100` — strong Hermes positioning and app-building workflow patterns, but too young and too globally mutating to install wholesale into an active Hermes profile.
- **Recommendation:** `distill-pattern` — borrow the packaging, onboarding, app-lifecycle, and founder-facing CTO-loop ideas into SStack/Hermes skills rather than adopting this repo as a dependency.
- **Usage observed 2026-06-08:** `reference-only`.
- **Review candidate:** Use as a public reference for app-builder onboarding and install/verify UX; do not run its installer against the live default Hermes profile without a dedicated sandbox and skill-security review.

## Scorecard

| Factor | Points | Evidence |
|---|---:|---|
| Stack fit | 20/25 | Directly targets Hermes Agent, skills, workflows, app-building, GitHub, Vercel, Supabase, monitoring, and messaging loops. |
| Leverage | 19/25 | Good productized workflow layer for turning Hermes into an app-ops assistant; relevant to agent-infrastructure work but mostly overlaps existing SStack/Hermes capabilities. |
| Reuse readiness | 15/20 | One-command install copies 23 skills, 5 workflows, and 6 agents; sandbox install worked after creating a fake Hermes home, but the repo installs into global Hermes directories rather than an isolated profile/pack. |
| Maturity/trust | 9/15 | New repo, 482 stars / 43 forks, last push 2026-05-12, no GitHub license metadata and no `LICENSE` file despite an MIT badge; verification script exits `0` even when reporting failures. |
| Differentiation | 15/15 | The useful differentiator is packaging Hermes for a founder/app-builder lifecycle: onboarding → product brief → implementation engine choice → deploy → monitor → issue triage → approval-gated shipping. |
| **Total** | **78/100** | Pattern source, not direct dependency. |

## Verdict

Oh My Hermes is a sharp packaging reference for making Hermes legible as an app-building/operator product. The right move is **not** to install it wholesale where Hermes, shared SStack skills, GBrain, repo-intelligence workflows, GitHub Projects, and local conventions already cover the operating needs. Its value is in the product/UX layer: copy-paste install prompts for agents, an app lifecycle skill bundle, a CTO-loop story, project bootstrap conventions, and explicit engine-routing between Hermes, Claude Code, and Codex. Treat the repo as inspiration for SStack/Hermes packaging and public onboarding, with security review before any third-party skill import.

## Reference-stack relevance

- It demonstrates a product direction: Hermes as the operator layer, with skills/workflows as the productized procedure layer.
- It offers a concrete "Hermes for building and operating apps" narrative that could inform SStack/Hermes onboarding and docs.
- Its CTO-loop framing applies to proactive Hermes workflows that triage issues, implement, review, deploy, monitor, and require human approval before shipping.
- It is a useful outside reference for packaging agent workflows as installable skills/workflows rather than burying procedures in chat history.

## Reuse / inspiration potential

- **Direct reuse:** Not recommended in the active profile. The installer copies third-party skill files directly into the Hermes skills directory, workflows into the workflows directory, and agents into the agents directory.
- **Pattern to borrow:** Agent-friendly install protocol, app-builder skill taxonomy, lifecycle workflow docs, `AGENTS.md` app template, verification script, and founder-facing CTO-loop onboarding.
- **Stack area improved:** Hermes skill packaging, SStack public onboarding, app/project bootstrap conventions, operational workflow templates.
- **Autonomy leverage:** The useful idea is a repeatable issue-to-PR-to-approval loop with PM/dev/QA/security/ops roles and cron-driven checks.
- **Coordination leverage:** If distilled carefully, this kind of workflow layer could reduce coordination overhead on small app projects; careless adoption would add prompt-supply-chain risk.

## What it is

Oh My Hermes is an opinionated extension layer for Hermes Agent: 23 skills, 5 workflows, 6 agent role definitions, scripts, templates, and docs for building and operating apps with Hermes. It positions Hermes as the long-lived operator, with Claude Code and Codex as optional implementation engines and Vercel/Supabase/Sentry/Uptime Kuma as default app infrastructure.

## Evidence checked

- **GitHub metadata:** `Salomondiei08/oh-my-hermes`, created 2026-05-08, last pushed 2026-05-12, 482 stars, 43 forks, not archived, no license metadata from GitHub API.
- **README/docs:** `README.md`, `INSTALL_FOR_AGENTS.md`, `docs/architecture.md`, `docs/workflows.md`, `docs/improvements-to-hermes.md`.
- **Key files inspected:** `install.sh`, `scripts/bootstrap.sh`, `scripts/setup-cto.sh`, `scripts/verify.sh`, `skills/onboarding.md`, `skills/choose-engine.md`, repo tree.
- **Inspected upstream clone:** HEAD `0464c72 2026-05-12T19:18:28+09:00 docs: add 'use with an AI agent' copy-paste prompts section`.
- **Syntax check:** `bash -n install.sh`, `scripts/bootstrap.sh`, `scripts/setup-cto.sh`, and `scripts/verify.sh` all passed.
- **Sandbox install:** With a disposable home and a fake Hermes home, `bash install.sh` installed 23 skills, 5 workflows, and 6 agents.
- **Sandbox verify:** `scripts/verify.sh` reported `Passed: 43 Failed: 5` after install because CTO profiles were not created, but still exited `0`.

## Verified / plausible / source claims

- **Verified:** The repo is a file-based Hermes extension layer; install copies Markdown skills/workflows/agents into Hermes directories.
- **Verified:** The skills use YAML frontmatter and plain Markdown instruction bodies, e.g. `onboarding` and `choose-engine`.
- **Verified:** The repo has no committed `LICENSE` file and GitHub API returned `licenseInfo: null`, despite the README badge claiming MIT.
- **Verified:** `verify.sh` can print many `[MISSING]` entries and still exit `0`, so it is not a reliable CI-grade gate as written.
- **Plausible:** The app-lifecycle workflows are useful as human/agent operating procedures, but no end-to-end CTO loop was run against a real project in this review.
- **Source claim:** README claims Hermes becomes an autonomous CTO loop that triages issues hourly, implements fixes, runs review/security/QA, and asks for approval before merge/deploy.

## Strengths

- **Excellent product framing:** "Oh My Zsh for Hermes" is memorable and helps explain skills/workflows to users.
- **Agent-friendly installation copy:** `INSTALL_FOR_AGENTS.md` and README prompts make it easy for another agent to bootstrap the system.
- **Good lifecycle taxonomy:** Requirements clarification, product brief, design handoff, engine choice, implementation, deployment, database connection, monitoring, notification, and post-deploy follow-up.
- **Clear operator/engine split:** Hermes is the operator; Claude Code and Codex are optional coding engines rather than the whole product.
- **Project bootstrap basics:** `AGENTS.md`, `.env.example`, and health endpoint templates are the right kind of durable project substrate.
- **Useful Hermes-core feedback:** `docs/improvements-to-hermes.md` lists concrete Hermes product/documentation gaps such as app-builder onboarding, evented deployment lifecycle, health-check cron recipes, project memory types, and per-project skill scoping.

## Risks / caveats

- **Third-party skill supply-chain risk:** Installing this repo directly mutates the Hermes skills, workflows, and agents directories with executable agent instructions.
- **License ambiguity:** README badge says MIT, but GitHub API reports no license and the tree has no `LICENSE` file.
- **Young repo / limited evidence:** The repo is only about a month old at review time and has no package manifest, test suite, or release artifacts.
- **Verification is too weak:** `verify.sh` exits success even when it reports missing required files/profiles, which can mislead automation.
- **Global-profile assumptions:** The installer targets the default Hermes home directly, not a named Hermes profile or isolated skillpack namespace.
- **Credential handling deserves scrutiny:** The onboarding flow asks the user to paste a GitHub fine-grained token into chat so an agent can run `gh auth login`; do not copy that credential-in-chat pattern into an onboarding workflow; use a protected authentication surface instead.
- **Some claims are aspirational:** The hourly autonomous CTO loop is documented, but this review did not verify a real issue→PR→approval→deploy cycle.

## Integration ideas

- Distill its app-builder onboarding into SStack/Hermes docs: one clear path for "use Hermes to build/operate an app".
- Borrow the lifecycle taxonomy when creating project bootstrap skills, but keep canonical shared skills in SStack rather than importing the repo wholesale.
- Use the `docs/improvements-to-hermes.md` list as a source of Hermes upstream/product ideas, especially per-project skill scoping and deployment lifecycle events.
- If sandboxing later, install into a throwaway Hermes profile/home, run `hermes skills list`/skill validation, and static-scan the imported skills before any active-profile merge.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — the Hermes runtime this repo extends.
- [steipete/agent-scripts](steipete--agent-scripts.md) — stronger reference for a real-world shared agent-rules/skills/scripts repo with portable helpers.
- [microsoft/agentrc](microsoft--agentrc.md) — related project-readiness/context-engineering reference for agent-friendly repos.
- [automazeio/ccpm](automazeio--ccpm.md) — stronger long-running agent workflow substrate for PRD/epic/GitHub issue decomposition.

## Review candidates and context

- Keep as `distill-pattern`; do not install wholesale into the live Hermes profile.
- If this pattern becomes a priority, create a SStack-backed "Hermes app-builder starter pack" with isolated install, verifier exit-code discipline, and explicit third-party skill review.
