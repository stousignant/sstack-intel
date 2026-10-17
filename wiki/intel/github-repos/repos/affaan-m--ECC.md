---
title: affaan-m/ECC
type: repo-intel
source: https://github.com/affaan-m/ECC
category: agent-harness-os
status: deep-analyzed
usefulness_score: 76
recommendation: distill-pattern
usage: not-used
score_confidence: medium
last_reviewed: 2026-09-23
license: MIT
---

# affaan-m/ECC

> Opinionated reference-stack evaluation, reviewed 2026-09-23. Scores and recommendations are fit judgments, not universal quality; usage is a dated observation. See [methodology](../../awesome-harness-engineering/methodology.md).

Formerly `affaan-m/everything-claude-code`; the old URL redirects to this repository. This is a source evaluation, not an installed-tool record. The earlier review was on 2026-06-03; the September refresh inspected upstream at [`bf70150`](https://github.com/affaan-m/ECC/commit/bf70150eb2df8070024e5bdf08e4aa08959e2735).

## Decision

- **Usefulness:** `76/100` — strong, concrete cross-harness and evidence-boundary examples; low direct-install fit for an existing harness stack.
- **Recommendation:** `distill-pattern`; no wholesale installation or import of instructions, hooks, MCP, or memory.
- **Usage:** `not-used`; confidence `medium` because this was source inspection, not an installed-runtime or full security test.

## Scorecard

| Factor | Points | Reason |
|---|---:|---|
| Stack fit | 20/25 | Portable source plus explicit adapter limits; Hermes support is not at Claude parity. |
| Leverage | 21/25 | Coordination receipts, replay/eval boundaries, and source provenance are useful patterns. |
| Reuse readiness | 12/20 | Documentation and tests exist, but the install and authority surface is broad. |
| Maturity/trust | 13/15 | Active, MIT, security fixes and tests; fast changes and installer/hook risk remain. |
| Differentiation | 10/15 | Concrete conformance fixtures, but much of the workflow overlaps existing agent practice. |
| **Total** | **76/100** | Pattern source, not a replacement runtime. |

## Verdict

ECC is now more than a collection of prompts: its shared skills, adapters, installer, memory CLI/MCP, coordination examples, and eval receipts have real implementation surfaces. The best reuse is **small, source-reviewed patterns**. A wholesale install would duplicate existing instruction and memory ownership and grant a fast-moving package access to configuration, hooks, and tool execution. Its own [cross-harness architecture](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/docs/architecture/cross-harness.md) says Hermes skill sync is still maturing; do not infer Claude feature parity from the platform list.

## Reusable intelligence

1. **Portable source, thin adapter:** keep workflow skills distinct from harness-specific hooks, event shapes, and command routing. The architecture labels actual capability differences rather than pretending all harnesses enforce the same rule. This is a design reference, not a reason to replace a working distribution. [Source](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/docs/architecture/cross-harness.md).
2. **Coordination inventory is not authorization:** the [read-only example](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/examples/coordination-inventory/README.md) distinguishes declared tasks/paths, sessions, heartbeat freshness, and leases. Its synthetic overlap heuristics do not prove live ownership or conflict reduction; use actual checkout and authority readback before mutations.
3. **Recalled context remains unreviewed:** the [CLI/MCP conformance fixture](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/examples/unified-memory/README.md) checks source-content matching, hostile client overrides, scope consent, and unchanged sources. Matching a host catalog does not prove identity, statement truth, or live Hermes integration. Useful for memory-boundary tests, not as a second truth store.
4. **Eval receipts without permission laundering:** the [capsule/replay/effect-class design](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/docs/architecture/eval-harness-frameworks.md) offers tamper checks and verifier-readable receipts. Candidate execution remains disabled pending verified OS containment; declared effect classes do not authorize side effects.

## Evidence checked

- GitHub metadata on 2026-09-23: MIT; 266,017 stars, 39,751 forks; last push 2026-09-22. These are snapshot popularity/maintenance signals, not quality evidence. [Repository](https://github.com/affaan-m/ECC).
- [`README.md`](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/README.md), [`package.json`](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/package.json), the architecture and examples above, [security policy](https://github.com/affaan-m/ECC/blob/bf70150eb2df8070024e5bdf08e4aa08959e2735/SECURITY.md), and the [latest GitHub release](https://github.com/affaan-m/ECC/releases/tag/v2.2.1).
- Current source manifest declares `ecc-universal` version `2.2.2`; latest GitHub release returned `v2.2.1` (published 2026-09-08). Do not conflate source/package version with a GitHub release or claim registry integrity from this check.
- September security and ownership fixes include [worker/MCP/hook hardening](https://github.com/affaan-m/ECC/commit/27667bc7463affd3c45ff57f8d25e54a71d4fcf5), [Codex config preservation](https://github.com/affaan-m/ECC/commit/c0ee74778925a24a844357095d6722d476a41600), and [home-install `.agents` scope](https://github.com/affaan-m/ECC/commit/da214d73b70fa9494a4ccc0784159fd29924116f). These are evidence of attention to failure modes, not a comprehensive security attestation.
- No install, tests, repomix pack, or execution of upstream code in this refresh.

## Risks / exclusions

- Prompt/instruction supply chain plus hooks, MCP, installer ownership, shell/worker execution and multi-harness config writes deserve independent review before any use. The upstream README warns against unofficial packages and stacking install modes.
- The hosted Pro/GitHub App is a separate service and privacy/authority decision; MIT source licensing alone says nothing about private-repo service access.
- Coordination inventory uses authored synthetic examples, not held-out effectiveness evidence. Memory conformance checks integrity relative to a catalog, not truth. Eval receipt integrity does not demonstrate improved task outcomes or safe execution.
- Historical OpenClaw adaptation proposals are not current Hermes operating guidance; a proposed implementation is not evidence of adoption.

## Alternatives / related repos

- [Evals / self-improvement / autoresearch comparison](../comparisons/evals-self-improvement-autoresearch.md)
- [karpathy/autoresearch](karpathy--autoresearch.md)
- [microsoft/agent-lightning](microsoft--agent-lightning.md)

## Operating boundary

Current runtime and knowledge ownership belong to their existing private stack surfaces, not to this source note. Compare any proposed ECC-derived behavior against those owners before implementation.

## Review candidates

1. If coordination evidence is missing in a real multi-agent failure, compare the read-only inventory fields (declared path, lease, heartbeat) against the existing work-state contract; promote only a demonstrable gap.
2. If a real eval or memory provenance failure recurs, adapt one capsule/receipt or CLI/MCP conformance fixture behind a narrow golden test, not the whole framework.

## Commitment disposition

No new issue or Project item promoted by this refresh. Candidates above are non-binding and require a concrete observed gap and acceptance criteria.
