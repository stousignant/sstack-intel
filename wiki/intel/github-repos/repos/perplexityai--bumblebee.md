---
title: perplexityai/bumblebee
type: repo-intel
aliases: [bumblebee, GitHub repo: perplexityai/bumblebee]
source: https://github.com/perplexityai/bumblebee
category: security-containment-agent-safety
topics: [github-repo, supply-chain-security, package-inventory, developer-endpoint-scanner, mcp-security]
status: deep-analyzed
usefulness_score: 88
recommendation: adopt-now
usage: not-used
score_confidence: high
last_reviewed: 2026-06-03
license: Apache-2.0
---

# perplexityai/bumblebee

> Reference-stack evaluation as reviewed 2026-06-03; usage is a dated observation, not a live-state claim. See [methodology](../../awesome-harness-engineering/methodology.md).

## Decision

- **Usefulness score:** `88/100` — direct fit for local developer endpoint inventory and rapid supply-chain exposure checks across packages, MCP configs, editor extensions, and agent skills.
- **Recommendation:** `adopt-now` for a bounded local sandbox; treat it as exposure inventory, not a full SBOM/vulnerability scanner.
- **Usage observed 2026-06-03:** `not-used`.
- **Review candidate:** Prototype a read-only scan on one project/root with a tiny Hermes-specific exposure catalog.

## Scorecard

| Factor | Points | Notes |
|---|---:|---|
| Stack fit | 24/25 | Directly protects Hermes/dev-agent endpoints and local packages. |
| Leverage | 23/25 | Fast “am I exposed?” checks are high-value for autonomous agent machines. |
| Reuse readiness | 18/20 | Single Go binary, clear scan profiles, no package-manager execution. |
| Maturity/trust | 13/15 | Strong testing/CI signals; new tool, exact-match scanner limits. |
| Differentiation | 14/15 | Developer-endpoint inventory across MCP/editor/skills is unusually aligned. |

## Verdict

Bumblebee is the most practical immediate tool in the security batch. It is read-only and focused: discover installed package/tool/extension/MCP/skill metadata and match it against known exposure catalogs. It is the cheap safety check to run before broadening agent access.

## Reference-stack relevance

- Gives Hermes a defensive “what packages/extensions/agent configs are present?” inventory surface.
- Covers agent-relevant endpoints such as MCP configs and skills, not just npm/PyPI packages.
- Could become a low-risk periodic scanner for compromised dependency advisories.

## What it is

A read-only developer endpoint scanner for on-disk package, extension, and developer-tool metadata, built to check exposure to known software supply-chain compromises.

## Evidence checked

- GitHub metadata on 2026-06-03: ~4.2k stars, pushed 2026-06-02, topics include `package-inventory` and `supply-chain-security`.
- README and root files from the upstream repository.
- Repomix pack: a temporary source pack of the public repository — 90 files / ~172k tokens; 2 suspicious files excluded by repomix.
- Targeted code evidence: scanner packages for npm/pnpm/yarn/bun/PyPI/Go/Homebrew/MCP/editor/browser/skills, selftest fixtures, stable IDs, profile/diagnostics paths, CI checks.

## Strengths

- Explicit read-only model; no package managers executed.
- NDJSON output and stable IDs are automation-friendly.
- Scans agent-adjacent endpoints like MCP configs and skills.
- CI signals include tests/race/vet/govulncheck per inspected evidence.

## Risks / caveats

- Exact name/version exposure matching; not behavioral malware detection.
- MCP parsing is not complete for every config shape.
- Home-directory scans need privacy/TCC/FDA awareness.

## Integration ideas

- Add a Hermes/SStack “developer endpoint exposure scan” recipe.
- Feed findings into second-brain/GBrain as a short security report, not raw inventory dumps.
- Start with one explicitly selected disposable project root and a tiny catalog before broader scans.

## Alternatives / related repos

- [NVIDIA/OpenShell](NVIDIA--OpenShell.md)
- [nearai/ironclaw](nearai--ironclaw.md)
- [Agastya910/agentarmor](Agastya910--agentarmor.md)

## Review guidance

- Review candidate: sandbox Bumblebee read-only scan with a Hermes-specific exposure catalog.
