---
title: OpenHands/OpenHands
type: repo-intel
aliases:
  - OpenHands
  - GitHub repo: OpenHands/OpenHands
source: https://github.com/OpenHands/OpenHands
category: coding-agent-platform
topics: [github-repo, repo-intelligence, coding-agent, sdk, cli, local-gui, cloud]
status: deep-analyzed
usefulness_score: 84
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-28
license: MIT core; enterprise directory PolyForm Free Trial
---

# OpenHands/OpenHands

> Reference-stack evaluation as reviewed 2026-05-28. Scores and recommendations express opinionated fit, not universal quality; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `84/100` — one of the most mature open coding-agent platforms, but Hermes/Codex are the active local stack; use OpenHands as a benchmark/design reference, not a migration target.
- **Recommendation:** `distill-pattern` — study SDK/CLI/local-GUI/trajectory/sandbox patterns and evaluation infrastructure; do not switch runtimes now.
- **Usage observed 2026-05-28:** `not-used`.
- **Review candidate:** Keep as a benchmark for what a full coding-agent platform includes; only sandbox if a specific Hermes gap appears.

## Scorecard

| Factor | Score | Notes |
|---|---:|---|
| Stack fit | 19/25 | Relevant to coding agents, CLI, GUI, sandbox, and evaluation; less aligned because Hermes is already active runtime. |
| Leverage | 22/25 | Strong reference for mature autonomous coding product surfaces and evaluation. |
| Reuse readiness | 15/20 | Docs, Docker/local GUI/CLI/SDK, but large dependency and infra footprint. |
| Maturity/trust | 14/15 | Very active, huge community, MIT core, tests/config; enterprise subdir has separate license. |
| Differentiation | 14/15 | Full platform breadth: SDK, CLI, local GUI, cloud, enterprise, roadmap, benchmark story. |

## Verdict

OpenHands is too large to casually adopt, but too important to ignore. The right stance is “benchmark/reference”: compare Hermes/Codex workflows against OpenHands' primitives — sandbox isolation, trajectory saving/replay, browser runtime, local GUI, cloud collaboration, evaluation infrastructure, and agent SDK boundaries.

## Reference-stack relevance

- Helps calibrate what mature AI-driven development platforms consider table stakes.
- The trajectory/replay, budget, max-iteration, sandbox, and browser settings in config map directly to autonomous-agent safety.
- Its SDK/CLI split is a useful pattern for Hermes: core engine versus user-facing surfaces.

## What it is

OpenHands is an AI-driven development platform with a Software Agent SDK, CLI, local GUI, cloud product, and enterprise offering. The README says the SDK contains the agentic engine, the CLI is familiar to Claude Code/Codex users, and the local GUI provides REST API plus React SPA for laptop execution.

## Evidence checked

- GitHub metadata via `gh repo view` on 2026-05-28: 75,153 stars, 9,528 forks, Python primary language, pushed 2026-05-28, license metadata `Other` because enterprise directory has separate license.
- README: SDK, CLI, local GUI, cloud, enterprise, SWE-Bench 77.6 badge, MIT core / enterprise exception.
- `LICENSE`: MIT outside `enterprise/`; `enterprise/LICENSE`: PolyForm Free Trial with 30-day/year free-trial limit and no distribution.
- `pyproject.toml`: `openhands-ai`, Python >=3.12,<3.14, FastAPI, Docker, browsergym, FastMCP, LiteLLM, OpenHands SDK/server/tools, Playwright, Redis/SQLAlchemy, Kubernetes, tree-sitter language pack, etc.
- `config.template.toml`: workspace, trajectory save/replay, screenshots, browser enablement, max budget/iterations, runtime/docker, JWT, concurrency, condenser settings.

## Strengths

- Broadest mature coding-agent platform in this batch.
- Good safety/ops knobs: budget, iterations, trajectory, screenshots, replay, runtime isolation.
- Clear product separation between SDK, CLI, local GUI, cloud, and enterprise.
- Strong benchmark/eval story relative to smaller tools.

## Risks / caveats

- Large infra surface and dependency stack; not a quick sidecar.
- Enterprise directory has PolyForm Free Trial constraints; avoid mixing enterprise code into reusable work.
- Switching from Hermes/Codex would incur high migration cost and weaken fit with the established workflow and ownership boundaries.
- Hosted/cloud paths need privacy and permissions review.

## Integration ideas

- Distill trajectory save/replay into Hermes autonomous coding proof bundles.
- Compare OpenHands' config knobs against Hermes/Kanban run controls: budget, max iterations, workspace mount, browser, screenshots, condenser.
- Use OpenHands as an external benchmark when designing local GUI or coding-agent dashboards.

## Alternatives / related repos

- [NousResearch/hermes-agent](NousResearch--hermes-agent.md) — active local runtime.
- [openai/symphony](openai--symphony.md) — proof-of-work/run lifecycle spec.
- [openclaw/openclaw](openclaw--openclaw.md) — typed gateway/product architecture reference.
- [agent0ai/agent-zero](agent0ai--agent-zero.md) — Linux desktop/browser/canvas agent platform.

## Review candidates and context

- Any experiment is a non-binding review candidate; keep execution state in the established issue tracker.
