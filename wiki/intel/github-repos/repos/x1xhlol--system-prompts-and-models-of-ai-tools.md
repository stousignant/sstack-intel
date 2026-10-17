---
title: x1xhlol/system-prompts-and-models-of-ai-tools
type: repo-intel
aliases: [system prompts and models of AI tools, GitHub repo: x1xhlol/system-prompts-and-models-of-ai-tools]
source: https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools
category: security-containment-agent-safety
topics: [github-repo, system-prompts, prompt-injection, red-team, leak-corpus, ai-agent-design]
status: deep-analyzed
usefulness_score: 54
recommendation: reference-only
usage: reference-only
score_confidence: medium
last_reviewed: 2026-06-03
license: GPL-3.0

---

# x1xhlol/system-prompts-and-models-of-ai-tools

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `54/100` — useful as sanitized defensive research, but legally/ethically/security messy as a leak corpus.
- **Recommendation:** `reference-only`; do not copy proprietary leaked prompts into Hermes.
- **Usage observed 2026-06-03:** `reference-only`.
- **Review candidate:** Build a sanitized pattern taxonomy from it, not a prompt-import pipeline.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 14/25 | Useful for prompt/security research, not operational infrastructure. |
| Leverage | 16/25 | Can improve red-team tests and design pattern awareness. |
| Reuse readiness | 7/20 | Corpus reuse is legally/ethically uncertain. |
| Maturity/trust | 7/15 | Huge stars; fidelity/staleness and provenance uncertain. |
| Differentiation | 10/15 | Broad prompt corpus is rare, but risky. |

## Verdict

This repo is useful the way malware samples are useful: study patterns defensively, do not operationalize the corpus. The value is understanding how major AI tools structure system prompts, tool instructions, secrecy, planning, and agent workflows. The trap is importing leaked/proprietary prompt text into Hermes and degrading the target assistant's instruction hygiene.

## Reference-stack relevance

- Helps design red-team tests for prompt leakage and instruction extraction.
- Shows patterns competitors use for tool contracts and safety language.
- Useful for SStack instruction hygiene, if distilled at the pattern level.

## What it is

A large collection of claimed system prompts, internal tool specs, and AI model/tool details from many AI coding and productivity products.

## Evidence checked

- GitHub metadata on 2026-06-03: ~138.7k stars, GPL-3.0 metadata, pushed 2026-05-23.
- [Upstream README/root files](https://github.com/x1xhlol/system-prompts-and-models-of-ai-tools) inspected.
- Repomix pack: a temporary source pack of the public repository — 104 files / ~462k tokens; no suspicious files detected.
- Targeted evidence: concrete prompt/tool artifacts for Claude Code, Cursor, Windsurf, open-source prompt dumps, GPT/Claude tooling JSON.

## Strengths

- Broad visibility into agent prompt conventions.
- Useful for defensive prompt-injection and extraction testing.
- Can inform high-level instruction-hygiene patterns.

## Risks / caveats

- Leak/provenance/IP ambiguity; GPL label may not apply to upstream proprietary prompts.
- Copying text could contaminate Hermes with competitor-specific or confidential material.
- Corpus may be stale, edited, incomplete, or inaccurate.

## Integration ideas

- Derive a sanitized “agent instruction pattern taxonomy” without quoting proprietary prompts.
- Use as adversarial examples for prompt-injection defense tests.
- Keep it out of canonical Hermes prompts/skills except as abstract lessons.

## Alternatives / related repos

- [Cranot/claude-code-guide](Cranot--claude-code-guide.md)
- [shanraisshan/claude-code-best-practice](shanraisshan--claude-code-best-practice.md)
- [microsoft/skills](microsoft--skills.md)

## Review guidance

- Review candidate: create a sanitized prompt-pattern taxonomy, explicitly excluding verbatim proprietary prompt imports.
