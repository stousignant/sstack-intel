---
title: aiming-lab/AutoResearchClaw
type: repo-intel
aliases:
  - AutoResearchClaw
  - GitHub repo: aiming-lab/AutoResearchClaw
source: https://github.com/aiming-lab/AutoResearchClaw
category: autonomous-research
topics: [github-repo, repo-intelligence, agent-evaluation, agent-training]
status: deep-analyzed
usefulness_score: 82
recommendation: distill-pattern
usage: not-used
score_confidence: high
last_reviewed: 2026-05-30
license: MIT
---

# aiming-lab/AutoResearchClaw

> Opinionated reference-stack evaluation, reviewed 2026-05-30. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `82/100` — Strong research-pipeline and HITL/checkpoint pattern source, but “one command, one paper” is too broad and risky as a default research workflow.
- **Recommendation:** `distill-pattern`.
- **Usage observed 2026-05-30:** `not-used`.
- **Review candidate:** Distill pipeline stages, citation verification, HITL gates, and generated-paper artifacts into research/briefing skills; do not run autonomous paper generation in the canonical vault.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 21/25 | Fits Hermes/GBrain/local-agent questions, but direct runtime fit varies by repo. |
| Leverage | 22/25 | Useful for evals, self-improvement, research automation, or sandbox safety. |
| Reuse readiness | 15/20 | Docs/install/licensing are present, but most require sandboxing before use. |
| Maturity/trust | 12/15 | Live metadata: 13015 stars, 1517 forks, pushed 2026-05-29T02:52:20Z, license MIT. |
| Differentiation | 12/15 | Distinctive compared with current Hermes stack as an eval/training/safety pattern source. |

## Verdict

Strong research-pipeline and HITL/checkpoint pattern source, but “one command, one paper” is too broad and risky as a default research workflow. The useful move is not to install this globally. Where Hermes/GBrain already provide the operating and knowledge layers, extract the eval/training/sandbox pattern and run bounded sandboxes only with copied, non-sensitive data.

## Reference-stack relevance

- This batch sits directly on the question of making Hermes more measurable and self-improving: benchmark tasks, trajectory capture, training loops, HITL research workflows, and safer agent sandboxes.
- It can turn “agent improvement” from vibes into artifacts: task suites, hidden graders, traces, verification reports, and explicit keep/revert criteria.
- The practical value compounds only when evals establish a gap before adding another canonical runtime or memory store.

## What it is

AutoResearchClaw is a Python CLI/pipeline that turns a research topic into paper artifacts: literature, experiments, citation verification, peer review, LaTeX, and deliverables, with full-auto and co-pilot modes.

## Live metadata checked

- Source: <https://github.com/aiming-lab/AutoResearchClaw>
- Description: Fully autonomous & self-evolving research from idea to paper. Chat an Idea. Get a Paper. 🦞
- Stars / forks: 13015 / 1517
- Primary language: Python
- License: MIT
- Latest release: v0.5.0 / 2026-05-20T04:39:43Z
- Last pushed: 2026-05-29T02:52:20Z
- Topics: autonomous-research, citation-verification, llm-agents, multi-agent-debate, openclaw, paper-generation, scientific-discovery, self-evolving, metaclaw

## Evidence checked

- GitHub metadata via `gh repo view aiming-lab/AutoResearchClaw` on 2026-05-30.
- README from [upstream README](https://github.com/aiming-lab/AutoResearchClaw).
- License and manifest files where present under a disposable source-inspection workspace.
- Top-level contents from GitHub API snapshot in `contents.json`.

## Strengths

- README documents concrete outputs such as `paper_draft.md`, `paper.tex`, `references.bib`, `verification_report.json`, `reviews.md`, and deliverables.
- HITL modes and release notes around checkpoint/step-by-step/co-pilot map well to Hermes approval boundaries.
- Small core Python package surface in `pyproject.toml`, MIT license, tests directory, docs, and active releases.

## Risks / caveats

- Autonomous research-paper generation is high hallucination/liability territory; output needs human review and citation verification before being trusted.
- Setup claims include Docker/LaTeX/OpenCode-style agent dependencies; integration cost is non-trivial.
- The repo’s strongest value is workflow design, not handing Hermes a “publishable science” button.

## Integration ideas

- Borrow the artifact contract for serious research: draft, sources, verification report, reviews, reproducibility bundle.
- Turn “gate-only/checkpoint/step-by-step” into a general Hermes approval-mode vocabulary for high-stakes workflows.

## Alternatives / related repos

- [microsoft/agent-lightning](microsoft--agent-lightning.md)
- [InternLM/WildClawBench](InternLM--WildClawBench.md)
- [aiming-lab/AutoResearchClaw](aiming-lab--AutoResearchClaw.md)
- [Gen-Verse/OpenClaw-RL](Gen-Verse--OpenClaw-RL.md)
- [NVIDIA/NemoClaw](NVIDIA--NemoClaw.md)
- [karpathy/autoresearch](karpathy--autoresearch.md)
- [garrytan/gbrain](garrytan--gbrain.md)
- [NousResearch/hermes-agent](NousResearch--hermes-agent.md)

## Review candidates and context

- Patch research/academic/briefing workflows later with HITL modes and citation-verification artifacts if missing.
- Non-binding guidance; executable state belongs to the established issue tracker.
