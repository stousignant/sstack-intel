---
title: morluto/rea
aliases: [REA, Reverse Engineer Anything]
type: repo-intel
source: https://github.com/morluto/rea
category: codebase-understanding
topics: [github-repo, reverse-engineering, evidence, mcp, static-analysis]
status: deep-analyzed
usefulness_score: 77
recommendation: watch
usage: reference-only
score_confidence: medium
last_reviewed: 2026-10-10
license: MIT
---

# morluto/rea

## Decision

- **Usefulness score: 77/100.** A differentiated local inspection utility with unusually explicit evidence semantics, but specialist demand and unsandboxed parsing/execution limit immediate adoption.
- **Recommendation: watch.** Consider a pinned, static-only disposable trial when a concrete application-understanding question exists; do not globally register the entire tool catalog merely because it is popular.
- **Confidence: medium.** Public documentation and selected implementation/test files inspected; no installation, upstream tests, live provider verification or reconstruction benchmarks run.
- **Reference-stack lens, 2026-10-10:** an existing agent cockpit, source-code search, browser access and canonical Markdown knowledge store; prioritize complementary capabilities over another runtime or persistent index. This is contextual fit, not universal product quality.
- **Usage at this review:** reference-only source assessment; this ingest did not install or activate REA.

## Scorecard

| Factor | Points | Assessment |
|---|---:|---|
| Reference-stack fit | 18/25 | Adds source-unavailable application/binary inspection, rather than duplicating a cockpit or knowledge store. Specialist rather than everyday development demand. |
| Leverage | 20/25 | Could shorten feature tracing, interoperability investigation and packaged-app diagnosis; benefit remains unmeasured. |
| Reuse readiness | 16/20 | CLI/MCP interfaces, documented static entry points and setup planning; advanced providers require external engines and target-specific host support. |
| Maturity/trust | 10/15 | MIT, active source, explicit security boundary and substantial test/verification documentation; broad rapidly changing surface and no locally exercised provider proof. |
| Differentiation | 13/15 | Evidence-linked cross-layer application investigation is meaningfully different from source-only repo maps. |
| **Total** | **77/100** | Useful specialist utility and evidence-contract reference; demand-led evaluation, not default activation. |

## Verdict

REA connects agents and terminal users to local reverse-engineering workflows across native binaries, JavaScript/Electron artifacts, .NET assemblies and browser/runtime observations. It is not a replacement agent or a second brain. Its most accessible initial lane is static JavaScript/Electron analysis, which the documentation says reads supplied artifacts without launching the application. Native decompilation delegates to Hopper, Ghidra or IDA. Prefer an explicit question and a legally authorized, non-sensitive target before any trial. Review-only capture is complete; adoption remains unproven.

## Reusable intelligence

1. **Evidence is a first-class typed result.** The domain contract includes content-derived identity, subject digest, provider, operation, caller parameters, raw and normalized results, confidence, authority, limitations, source locations and evidence links. Confidence distinguishes observed, derived and inferred; authority distinguishes shipped artifacts, controlled replay, historical references, external services and analyst inference. This prevents an attractive inference being silently presented as direct observation. [Evidence contract](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/src/domain/evidence.ts#L29-L118).
2. **Derived workflows preserve uncertainty.** JavaScript feature traces, semantic traces and version comparisons explicitly set inferred confidence and analyst-inference authority while forwarding limitations and evidence links. An adapter records derived evidence with its supported unknown atomically when present. [Workflow evidence](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/src/application/javascript/JavaScriptApplicationWorkflowEvidence.ts), [derived recording](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/src/server/recordDerivedEvidence.ts).
3. **Shared application workflows behind CLI and MCP.** The documented inward dependency structure separates entry points, composition, provider adapters, application services, contracts and pure domain logic. The one-shot composition file binds operations to a caller-selected environment. This is a reusable architectural pattern, not proof that every provider honors it. [Architecture](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/docs/architecture.mermaid), [direct composition](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/src/composition/directAnalysis.ts).
4. **Partial work stays useful under resource pressure.** The JavaScript worker parses and checkpoints static facts before semantic projection. Its explicit capacity checks retain static observations rather than claiming unavailable semantic completeness. [Worker implementation](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/src/composition/javascriptAnalysisWorkerProcess.ts#L18-L72).
5. **Catalog identity is distinct from provider availability.** The MCP contract documents a stable complete inventory, unavailable tools included, and separate live identity/availability reporting. Full versus compact schema presentation changes advertisement, not canonical validation. This has real context and provider-compatibility costs; a large always-attached catalog is not free. [MCP contracts](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/docs/mcp-contracts.md#identity-and-discovery).

## Strengths

- Public docs distinguish static reads from runtime interactions, and enumerate target/provider prerequisites rather than claiming all formats work everywhere.
- Source-inspected evidence fields and derived workflow constructors support provenance, uncertainty and follow-up investigation.
- Setup has an explicit discovery/planning representation. Selected tests assert no mutation before confirmation and no applied actions after declining; tests were inspected, not run. [Setup plan](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/src/application/SetupPlan.ts), [planning tests](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/src/application/Setup.planning.test.ts#L47-L110).
- MIT licensing lowers code-pattern reuse friction; permissions and licenses of investigated targets remain separate.

## Risks and exclusions

- **Not a sandbox.** The security policy explicitly says provider bridges cannot protect against malicious processes running as the same OS user. Untrusted-binary parsing inherits local provider permissions; Ghidra's private temporary project/resource controls do not turn it into a sandbox. [Security boundary](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/SECURITY.md#security-boundary).
- **Runtime observation is an action surface.** Launching/interacting with targets uses user permissions. Browser sessions, captures and proprietary artifacts can contain sensitive data; local collection does not establish what the caller's LLM later receives. Restrict both input and downstream inference scope.
- **Setup is not just adding a tool.** It can modify client registrations and install matching skill instructions; optional Hopper installation has additional host/package-manager effects. Do not run generic setup against a production profile for an evaluation.
- **Native engines are separate prerequisites.** Ghidra/Java and IDA are user-managed; deep analysis is not a self-contained zero-dependency capability. The manifest requires Node 22.19+ within 22.x, 24.11+ within 24.x, or 26+.
- **Source is not release proof.** The inspected manifest says `rea-agents` 6.3.0. That is the source manifest, not verification that every current-main feature is available in a published package. The README explicitly warns about release-versus-main differences.
- **Verification breadth is easy to overread.** Testing docs distinguish synthetic client/provider fixtures from live model/provider behavior. No advertised reconstruction example or compatibility lane was reproduced in this review.
- **Authorized targets only.** Feature understanding is not permission to bypass access controls, inspect third-party secrets or copy protected implementation. Target ownership, terms, jurisdiction and clean-room needs must be evaluated for the actual use case.

## Evidence checked

- Reviewed **2026-10-10**, source revision **`4999e4be2c1669d04417fcdea582052048adbb2d`**, fetched as a disposable read-only source checkout.
- GitHub metadata at initial retrieval: MIT, 71,531 stars, 14,987 forks, last push `2026-10-10T23:23:47Z`; popularity is volatile and was not used as quality proof.
- README, SECURITY.md, package.json, architecture diagram, MCP contracts and selected testing-guide sections.
- Implementation: `src/domain/evidence.ts`; `src/server/recordDerivedEvidence.ts`; `src/application/javascript/JavaScriptApplicationWorkflowEvidence.ts`; `src/composition/directAnalysis.ts`; `src/composition/javascriptAnalysisWorkerProcess.ts`; first setup discovery/planning section in `src/application/SetupPlan.ts`.
- Test sample: first planning, no-confirmation and declined-plan cases in `src/application/Setup.planning.test.ts`.
- **Not inspected comprehensively:** every provider, installer implementation, native bridges, full supply chain or all client adapters. No DeepWiki or Repomix pack was needed.
- **Runtime/test result:** not run. No dependency installation, model invocation, app launch, production configuration write or REA MCP registration.

## Related intelligence

- [oraios/serena](oraios--serena.md) — source-aware semantic retrieval/editing; a different capability from understanding shipped artifacts without source.
- [tt-a1i/archify](tt-a1i--archify.md) — architecture communication and artifact verification; complementary output, not a decompiler.

## Non-binding review candidates

1. **Static-only JavaScript/Electron trial.** Rationale: accessible entry point without a native decompiler. Review question: does a pinned package recover a known feature's modules/IPC edges from a disposable, non-sensitive fixture accurately enough to improve manual analysis? Promotion condition: explicit trial authority, pinned dependency/security review, isolated configuration and a known-answer result with preserved unknowns.
2. **Evidence-contract comparison.** Rationale: portable observed/derived/inferred semantics and evidence links. Review question: do existing analysis outputs lose those distinctions at an adapter boundary? Promotion condition: a demonstrated concrete gap and an authorized change in its existing owner; do not add a general evidence framework merely to mirror REA.

## Public provenance

[Repository](https://github.com/morluto/rea) · [Pinned README](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/README.md) · [Manifest](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/package.json) · [Security](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/SECURITY.md) · [Testing limits](https://github.com/morluto/rea/blob/4999e4be2c1669d04417fcdea582052048adbb2d/docs/testing.md).
