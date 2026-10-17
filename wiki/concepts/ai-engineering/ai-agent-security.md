---
title: AI Agent Security
author: Hermes Agent
created: 2026-06-03
updated: 2026-06-03
type: concept
tags: [ai, agents, security, prompt-injection, sandboxing]
status: active
---

# AI Agent Security

> Reference-stack lens: [AI engineering](index.md).

## Working synthesis

Tool-using AI agents collapse many trust zones into one natural-language context. That is powerful, but it also means untrusted text can become executable influence unless the system has real permission boundaries.

## Threat model

- Indirect prompt injection is an architectural hazard of tool-using LLM agents: trusted instructions, user intent, webpages, emails, code comments, dependency READMEs, transcripts, and prior messages all enter one natural-language context.
- Treat fetched web/email/code/transcript content as untrusted data, never as authority.
- Agents should not let retrieved text redefine goals, leak secrets, modify files, or override system/user instructions.
- Code-agent threat model should include malicious prompts hidden in comments, READMEs, package docs, issue text, and generated files.

## Controls that matter

- Classifier-only defenses, markdown sanitation, security reminders, and confirmation popups are not enough.
- Durable controls are sandboxing, least privilege, credential separation, diff review, path allow-lists, audit logs, and rollback.
- Personal AI workers that read untrusted web/code/email content should run with scoped credentials, limited filesystem access, and explicit review gates before push/send/delete/deploy.

## Related

- [Agentic Coding Systems](agentic-coding-systems.md)
- [Thin Harness, Fat Skills](thin-harness-fat-skills.md)
- [2026 05 30 the security nightmare of ai agents](https://www.youtube.com/watch?v=_3okhTwa7w4)

## Provenance

This is a curated synthesis of earlier source notes, not a fresh verification of every frontier or security claim. Retain the dated confidence/status above where present; use primary evidence before making deployment or capability claims.
