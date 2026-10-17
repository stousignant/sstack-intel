---
title: AI Dark Factory
created: 2026-06-02
updated: 2026-09-03
type: concept
tags: [ai, agents, autonomous-coding, governance, validation]
sources:
  - https://www.youtube.com/watch?v=6woc6ii-zoE
  - https://www.youtube.com/watch?v=DcLj_SO8JNk
status: active
---

# AI Dark Factory

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

An AI dark factory is an autonomous software-production loop where agents triage issues, implement changes, validate them, open PRs, merge/deploy, run regression, and convert failures into new work with minimal or no human intervention.

Treat this as an experimental architecture, not a production default. The point is not “agents run wild”; the point is governed autonomy.

“AI software factory” is the same concept under a different name. Cole Medin uses the two interchangeably and credits Dan Shapiro's five-levels-of-AI-coding-autonomy framing for the underlying ladder.

## Autonomy levels

The useful calibration is which level you are actually operating at, not whether you have “a dark factory”:

- **Level 3** — the coding agent writes all the code, but a human remains closely involved in planning and validation for every issue. This is the reliability-maximizing default for the reviewed Hermes/GBrain reference stack.
- **Level 5** — a planning document goes in and deployed code comes out. The human still steers direction but there is no per-change steering wheel, and no human reads the code before production.

Levels are a dial per workload, not a maturity score. The honest current boundary for L5 is prototyping and spiking product ideas, where cheap models make disposable exploratory code rational. Critical or complex paths stay at L3.

## Evidence standard

A successful factory run on a simple, non-critical application is not evidence of reliability. Cole shipped a live production app end-to-end without reading a line of its code and still discounted the result on exactly these grounds. Before claiming a factory works, name what would have to fail for the claim to be false: complexity, criticality, and blast radius of the test workload are the variables that matter, not whether the loop completed.

## Why build toward it even at L3

Removing yourself from the loop is a forcing function on harness quality. If you cannot catch the agent's small mistakes, the harness has to be genuinely reliable rather than reliable-with-a-human-patching-it. That pressure improves in-the-loop work too, which makes factory-building a legitimate harness-engineering exercise even for someone who never intends to run L5 on anything that matters.

## Required architecture

- Mission and factory-rules files defining purpose, allowed scope, forbidden scope, and quality gates.
- Issue-based intake with triage, labels, and priority.
- Isolated implementation environments, usually worktrees.
- Independent holdout validators that do not share implementer context.
- User-journey / E2E validation, not just self-written tests.
- Regression loops that create new issues from failures.
- Model routing so high-throughput loops do not burn frontier models on trivial nodes.

## Workload-conditional implication

In a Hermes/GBrain-based system, use dark-factory thinking to identify which repeated steps can be automated, then test them in constrained sandboxes such as non-critical documentation or repository maintenance. Autonomous merge/deploy authority is justified only after governance, capability boundaries, independent validation, and rollback are proven for the workload's risk.

## Related

- [Archon](https://github.com/coleam00/Archon)
- [Parallel Agentic Development](parallel-agentic-development.md)
- [Agentic Coding Systems](agentic-coding-systems.md)
- [Harness Engineering](harness-engineering.md)
