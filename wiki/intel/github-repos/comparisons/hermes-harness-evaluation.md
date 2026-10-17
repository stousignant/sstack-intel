---
title: Evaluating the Configured Hermes Harness — Promptfoo, DeepEval, Harbor, and Native Evals
created: 2026-10-12
updated: 2026-10-16
type: comparison
status: active
tags: [hermes, harness-engineering, agent-evaluation, regression-testing, promptfoo, harbor, deepeval]
lifecycle: volatile
confidence: medium
last_reviewed: 2026-10-12
review_cadence: event-driven
sources:
  - https://hermes-agent.nousresearch.com/docs/developer-guide/prompt-assembly
  - https://www.promptfoo.dev/docs/providers/python/
  - https://raw.githubusercontent.com/harbor-framework/harbor/main/src/harbor/agents/installed/hermes.py
  - https://deepeval.com/docs/getting-started-agents
  - wiki/intel/github-repos/comparisons/evals-self-improvement-autoresearch.md
  - wiki/intel/github-repos/comparisons/dream-repair-self-improvement.md
  - wiki/intel/github-repos/comparisons/agent-eval-training.md
---

# Evaluating the Configured Hermes Harness

## Executive recommendation

**Use Promptfoo as a thin comparison layer around the actual Hermes CLI, not as a replacement agent.** Start with one collection-retrieval regression family, a fresh copied state per invocation, retained native evidence, and deterministic grading. If adopting Promptfoo is disproportionate for that first family, use the same subprocess/evidence contract in a focused native script; do not build an experiment platform.

**Harbor is configurable, but its shipped Hermes adapter does not currently accept native configuration.** Its supported custom-agent interface makes preservation possible without a framework fork. For a Hermes deployment using OAuth, preserving that route requires more than swapping its generated YAML: its execution method also forces model selection, API-key routing, the Hermes home, and approval bypass. Harbor is therefore a conditional choice for containerized task/verifier workloads, not the smallest default for this configured-harness regression.[^harbor][^base][^custom]

These are integration judgments, not measured performance or labor-market claims. Promptfoo's declarative cases, comparison reports, and explicit assertions provide useful work-transfer learning for AI adoption and acceptance testing. DeepEval offers stronger Python/RAG component-evaluation learning; Harbor offers benchmark/task-environment learning. Choose the capability to finish, not three frameworks to learn simultaneously.

This comparison is research, not an implementation or a bake-off. No evaluation framework was installed, no benchmark was run, and no harness settings were changed. Configuration equivalence remains untested.

## What must remain real?

The subject is the **configured execution path**, not merely the Hermes agent class. Hermes assembles identity, project context, skills, built-in memory/profile snapshots, external memory context, and runtime/platform hints. The CLI and gateway supply different surrounding context.[^assembly][^gateway]

A proposed run manifest should record the code revision; effective model/provider and auxiliary routes; reasoning and turn defaults; working directory/context-file scope; SOUL/shared-policy content hashes; skill roots/discovery settings; available MCP/retrieval routes; initial memory state; and every isolation deviation. Keep private contents and credentials out of published manifests. Do not mistake a stream `init` model field for proof of resolved authentication: the emitter can run before credential/agent initialization.[^stream]

Preserve normal skill discovery. Hermes supports `skills.external_dirs`; paths must exist in the evaluation environment. Copying selected skills into the writable local skills directory changes ownership and precedence, not just location. Do not preload the collection skill solely to make the test pass when normal discovery is part of the behavior under test.[^skills]

A CLI run tests CLI behavior. It does **not** establish Discord session-history injection, reply context, channel identity, gateway tool availability, or message delivery. A separate gateway-level test is needed if the defect depends on those factors; a source tag is not a Discord simulator.[^gateway]

## Comparable choices

| Candidate | Existing integration and fidelity | Main value | Cost/limitation and disposition |
|---|---|---|---|
| Promptfoo | Generic Python provider can launch the configured CLI; no dedicated maintained Hermes adapter identified in inspected docs/provider tree | Declarative regression/comparison and output assertions | Small subprocess/evidence glue plus isolated-state preparation; preferred first framework |
| DeepEval | Manual instrumentation and explicit test cases; no maintained Hermes integration identified in inspected integration tree | Python CI, agent metrics, RAG component diagnosis | Hermes trajectory/retrieval mapping still required; choose when that learning objective dominates |
| Harbor | Shipped Hermes installation, skills/MCP registration, session-to-ATIF conversion | Task environments, verifier artifacts, common trajectories | Built-in adapter changes configuration and routing; custom agent plus environment projection needed |
| Hermes-native | Existing task-specific eval code exercises different runtime layers | Minimal dependency footprint and direct evidence | Not one ready-made configured-harness evaluation product; reuse method, not an unconfigured runner |

Documentation/source supports the mechanisms above; relative setup and maintenance burden is a judgment. The absence search covered current default-branch trees and relevant provider/integration documentation, not every community repository.[^python][^deep-agent][^harbor][^native]

## Promptfoo: the smallest framework route

A top-level Python `call_api(prompt, options, context)` can launch a fresh Hermes process. Python workers persist across calls, so never retain a Hermes session, mutable home, or arm state in worker globals. Return final text as `output`, native usage when available, and trace/evidence metadata; report startup failures rather than inventing empty successful answers.[^python]

The installed CLI help and current upstream stream implementation support this proposed command shape:

```bash
hermes chat --query-file CASE_FILE --oneshot --format stream-json
```

Run it against the deliberately prepared evaluation home/workspace. Leave model/provider and turn limits at the intended configured defaults, unless those are explicitly the experimental variables. Do not add `--safe-mode`, `--ignore-rules`, or `--ignore-user-config`: these remove the behavior being measured. Pass arguments without a shell. This command was checked via help/source, not executed against a model.[^stream]

The subprocess keeps provider resolution inside Hermes, but a fresh home can break OAuth scope: an authorized authentication-compatible smoke check remains prerequisite, not assumed. Align the Python worker timeout with permitted run duration and clean up child processes on failure; the documented five-minute worker default is not a fidelity guarantee.[^provider][^python]

Parse `system/init`, `tool_use`, `tool_result`, and terminal `result`; preserve exit status and stderr separately. Tool-result stream payloads are capped at 5,000 characters, so retain exact-session exports or adapter receipts when full collection/pagination evidence matters. Do not export unrelated sessions.[^stream]

Two grading routes are available:

- **First evaluation:** a narrow JavaScript assertion reads retained Hermes evidence through `context.providerResponse.metadata`/`context.metadata`, alongside final-output checks. One collection predicate is enough; no generic grading engine.[^js]
- **Later, if useful:** map Hermes tool events to compatible child spans and reuse `trajectory:tool-used`, `trajectory:tool-args-match`, `trajectory:tool-sequence`, and `trajectory:step-count`. These require trace data; a Python provider-level span does not expose internal tools. Promptfoo supplies an OTLP receiver, but this mapping remains proposed, not a verified Hermes integration. Do not introduce a separate tracing service for the first test.[^trajectory][^tracing]

The `exec:` provider is simpler for final-text-only checks, but stdout JSON remains output text rather than a structured ProviderResponse. Prefer Python when carrying usage and evidence metadata.[^exec]

For a future authorized run, use `--no-cache`, explicit repetitions, and initially serial execution; a fresh result is not guaranteed merely by returning `cached: false`. Disable sharing, telemetry, and update checks for private runs. Those settings do not stop Hermes/provider/MCP network traffic or LLM-judge egress.[^cli][^telemetry]

## Harbor: precise configuration-fidelity answer

**Observed at Harbor `4778ceba98314a3b0fe119249f7ac84fc0af08b7`:** the adapter's capability declaration omits `native_config`; that capability defaults false. `BaseInstalledAgent` rejects a non-null `config` when the capability is false. The base's generic configuration support is therefore not an available Hermes configuration override.[^capabilities][^base]

The inspected adapter writes its own configuration at each run, disables personal memory/profile, changes delegation/checkpoints, fixes its execution home, and selects an explicit model/API-key route. Current tests corroborate that it no longer imposes the historical default turn cap; leaving the option unset preserves **Hermes built-in defaults**, not an operator configuration the adapter never loaded.[^harbor][^harbor-tests]

| Adjustment | What works / remaining gap |
|---|---|
| `version` | Installer receives a branch/ref selection; also inspect/pin the installer itself, which is fetched from upstream main |
| Toolsets and turn option | Supported knobs, not complete configuration import; no arbitrary cap should be added |
| Skills/MCP inputs | Existing registration machinery; does not recreate external-root ownership, all Hermes MCP settings, or prove connectivity |
| Agent environment variables | Supported injection; cannot override execution values explicitly supplied by this adapter |
| Preseeded home/config | Generated YAML is overwritten; projecting files alone does not solve configuration preservation |
| Native `config` | Rejected by the shipped Hermes capability gate |

These observations are supported by adapter, base, option, and registration tests; they do not establish a successful customized run.[^harbor][^base][^harbor-tests][^harbor-mcp]

**Supported route, no fork:** supply an importable custom installed agent using Harbor's documented `module.path:ClassName` interface. Reuse installation/export/ATIF machinery where practical; replace configuration/execution ownership rather than monkey-patching Harbor. A config-generation override might suffice for a simple API-key benchmark, but the inspected `run` routing is not transparent to a Hermes deployment configured with `openai-codex`. That provider is absent from its native map and follows the OpenRouter-key path; Hermes itself uses a separate Codex Responses/authentication path.[^custom][^factory][^provider]

The integration still needs a reviewed configuration projection, identity files, normally discovered skill roots, isolated memory/session state, compatible authentication, reachable MCP dependencies, and an evidence grader. Preserve auxiliary routing too. Harbor's Hermes MCP serializer emits only command/args or URL; per-server environment, headers, and tool filters are not serialized there. Container-local paths and localhost endpoints also need explicit reachability verification.[^harbor] This was not prototyped; its size cannot honestly be called trivial. If it grows into maintaining a parallel execution method and credential plumbing, stop and use the direct subprocess route.

Harbor's advantage is real task containment and verifier organization. Network policies support public, no-network, and allowlist modes with backend-specific support; setup and agent phases can differ. A container with broad mounts, credentials, and public egress is not automatically safe. A separate Hermes home isolates application state, not host filesystem or network authority.[^network]

**What would change the recommendation:** a small custom integration proving the required configuration and OAuth/MCP routes unchanged, with useful container/verifier isolation that offsets maintenance. Native Hermes config support added upstream would remove one gap, not automatically resolve routing or state projection.

## DeepEval and native evaluations

DeepEval's official agent guide supports manual `@observe` instrumentation and framework integrations. Wrapping a subprocess gives an outer span, not automatic visibility into Hermes tool/retriever calls. Alternatively, map retained events into explicit test-case tool calls and actual retrieved content; its test-case schema has these fields. RAG metrics can distinguish retrieval from answer faithfulness, but supplied `retrieval_context` must be what the run actually fetched, not the expected collection pasted into a case.[^deep-agent][^deep-schema][^deep-rag]

Prefer deterministic checks for collection membership, pagination, and source access. Add a calibrated model judge only for materially ambiguous recommendation quality, with separately approved privacy/cost. Do not follow the guide's cloud-login step by default. Cloud upload, telemetry, and judge routing still need review; no fully local DeepEval execution was established. DeepEval is an alternative, not necessary alongside Promptfoo.

Hermes-native examples are valuable but not interchangeable:

- `session_search_schema` uses a minimal OpenRouter loop and seeded database, not the full configured harness.
- `readtool` uses real `AIAgent`, but its runner skips context and memory, selects toolsets, and caps iterations. Its fixture/oracle method is reusable; its launch settings are not faithful here.
- `browser_use` demonstrates isolated per-cell homes and workload-specific oracles; `toolperf_abeval` expects a configured home and retains per-run metadata/trajectories. Both remain campaign-specific code.[^native][^readtool][^browser][^toolperf]

The open [issue #96704](https://github.com/NousResearch/hermes-agent/issues/96704) proposes skill-efficacy evaluation; its claims are dated proposal evidence, not proof of a shipped general efficacy platform.

## Smallest real evaluation

**Illustrative request:** “Which repository in the provided collection would best help me learn harness engineering, and why?” Use a synthetic or explicitly authorized collection; this is not a disclosure of account membership or an observed incident. Do not supply collection membership or descriptions in the prompt: packing all evidence into the prompt tests synthesis rather than source discovery. This is a proposed regression case, not a reported failure; establish the baseline before proposing a correction.

Use two distinct evidence lanes:

1. **Controlled retrieval/grounding fixture:** expose a sanitized collection through a discoverable tool/file route, with several plausible distractors and relevant evidence available only through retrieval. This tests whether Hermes seeks and uses the named source. A fixture alone does not prove GitHub adapter wiring.
2. **Separately authorized live wiring check:** inspect the named GitHub collection through the actual available route, recording collection identity, completeness/pagination, membership, and evidence returned. Current read-only research did not access account credentials or run this check.

Grade successful source inspection before recommendation, supported collection membership, accurate reasons, honest uncertainty, and no prohibited mutations. Accept legitimate alternative routes—GitHub CLI, API, browser, or an attributable synchronized collection with sufficient freshness. A `terminal` call alone proves nothing; inspect its command/result. Conversely, do not require a fixed tool name when another route produces equivalent evidence. A cached vault note without demonstrated collection identity/freshness is insufficient for a live-wiring claim.

Keep one original case, an unseen variation changing collection/distractors or task emphasis, and a negative control with no named collection. Include an unavailable/empty-source variation to detect fabricated access. Separately test the grader with deliberately unsupported answers and traces: instrument failure must not masquerade as agent failure or success.

After authorization, run baseline first, then compare a targeted instruction/skill correction with identical model, tools, fixtures, initial state, and defaults. Repeat fresh trials under an agreed spend bound and retain every outcome. Three repeats are a useful initial noise check, not statistical proof. Keep holdout evidence inaccessible to the agent and do not train on its failures. If baseline already passes, report that and avoid manufacturing improvement.

Preserve memory **reads** with reset copied snapshots; writes may land only in disposable state. External memory-provider ingestion can escape a copied home: require supported read-only/test-namespace controls or explicitly disclose a memory-disabled arm as a fidelity deviation. Never symlink writable test state to production. The same boundary applies to remote MCP writes and self-improvement hooks. Hermes documents automatic memory writes and warns against sharing one home between agents.[^memory]

The first deliverable should be cases, one thin execution adapter, a narrow grader, and a redacted baseline/candidate table with native evidence. No scheduler, optimizer, service, dashboard deployment, or framework fork is required.

## Brief screen and rejection reasons

- **Inspect AI:** credible agent/sandbox bridge, but redirects model calls through Inspect. Generation parameters are dropped by default (`forward_generation_config=True` is adjustable); other request policies and Responses state handling still differ. Preservation of a configured Codex OAuth route was not demonstrated. A plain subprocess integration is possible in principle but supplies no decisive advantage here.[^inspect]
- **Phoenix:** useful self-hosted observability/evaluation, but adds an instrumented service/store before the regression needs one. Current license is Elastic License 2.0, not Apache/MIT; telemetry is enabled by default with an opt-out. Self-hosted storage does not make remote inference local.[^phoenix]
- **Braintrust:** useful managed experiment collaboration, but documented self-hosting is Enterprise data-plane hosting with a Braintrust-managed control plane. The Apache-2.0 Python SDK license does not make the entire platform locally self-hostable. Not the minimal private first evaluation.[^braintrust]

## Evidence, freshness, and connections

Research checked official docs, opened default-branch source, Harbor unit-test source, public GitHub metadata, installed CLI help, and relevant curated vault pages on **2026-10-12**. Tests were inspected, not run. Default-branch snapshots: Hermes `b23600860f82bd66d345c0a1baefd0f264605955`; Harbor `4778ceba98314a3b0fe119249f7ac84fc0af08b7`; Promptfoo `129cdb7ca768de316f0cb86cebc60b0db457b132`; DeepEval `016946f6d770f8bc4e2f63f665140aea527d6641`. CLI help was separately inspected, not treated as proof of an identical upstream/runtime build. Recheck the actual executable and upstream refs before implementation.

Confidence is high for directly inspected contracts; medium for comparative fit; unknown for execution compatibility. Live configuration contents/authentication were not inspected. Generic extraction was unavailable and some direct HTML fetches failed; web opening and raw-source retrieval supplied the cited primary evidence. No community how-to was accepted as adapter proof.

Existing broader [evals/autoresearch](evals-self-improvement-autoresearch.md), [dream/repair](dream-repair-self-improvement.md), and [agent evaluation/training](agent-eval-training.md) comparisons remain complementary. No exact focused page was found through source-scoped GBrain search and broader curated-file searches. This page does not replace their unique optimizer/training or workflow content. [Repo intelligence index](../index.md) owns navigation, not a duplicated execution queue.

## Primary sources

The research worker opened/read these sources for the cited claims. The parent independently confirmed all 40 unique external URLs were reachable and checked the pinned Harbor adapter, native-config gate, capability defaults, and custom-agent interface. This is source verification, not an execution-compatibility test. Links to `main` are mutable and scoped by the snapshot refs above.

[^assembly]: [Hermes prompt assembly](https://hermes-agent.nousresearch.com/docs/developer-guide/prompt-assembly).
[^gateway]: [Hermes gateway internals](https://hermes-agent.nousresearch.com/docs/developer-guide/gateway-internals).
[^skills]: [Hermes skill discovery implementation](https://raw.githubusercontent.com/NousResearch/hermes-agent/main/agent/skill_utils.py).
[^stream]: [Hermes structured stream implementation](https://raw.githubusercontent.com/NousResearch/hermes-agent/main/hermes_cli/stream_json.py), corroborated by installed `hermes chat --help`.
[^python]: [Promptfoo Python provider](https://www.promptfoo.dev/docs/providers/python/); [worker implementation](https://raw.githubusercontent.com/promptfoo/promptfoo/main/src/providers/pythonCompletion.ts).
[^js]: [Promptfoo JavaScript assertions](https://www.promptfoo.dev/docs/configuration/expected-outputs/javascript/).
[^trajectory]: [Promptfoo deterministic/trajectory assertions](https://www.promptfoo.dev/docs/configuration/expected-outputs/deterministic/).
[^tracing]: [Promptfoo tracing guide](https://www.promptfoo.dev/docs/tracing/); [complete OpenAI Agents Python example](https://www.promptfoo.dev/docs/guides/evaluate-openai-agents-python/) provides comparison/usage patterns, not a Hermes runtime adapter.
[^exec]: [Promptfoo custom scripts](https://www.promptfoo.dev/docs/providers/custom-script/); [stdout implementation](https://raw.githubusercontent.com/promptfoo/promptfoo/main/src/providers/scriptCompletion.ts).
[^cli]: [Promptfoo CLI](https://www.promptfoo.dev/docs/usage/command-line/).
[^telemetry]: [Promptfoo telemetry/update controls](https://www.promptfoo.dev/docs/configuration/telemetry/).
[^harbor]: [Harbor Hermes adapter](https://raw.githubusercontent.com/harbor-framework/harbor/main/src/harbor/agents/installed/hermes.py).
[^base]: [Harbor installed-agent configuration and environment precedence](https://raw.githubusercontent.com/harbor-framework/harbor/main/src/harbor/agents/installed/base.py).
[^capabilities]: [Harbor capability defaults](https://raw.githubusercontent.com/harbor-framework/harbor/main/src/harbor/agents/capabilities.py).
[^custom]: [Harbor custom-agent guide source](https://raw.githubusercontent.com/harbor-framework/harbor/main/docs-mintlify/agents/custom-agents.mdx).
[^factory]: [Harbor import-path factory](https://raw.githubusercontent.com/harbor-framework/harbor/main/src/harbor/agents/factory.py).
[^harbor-tests]: [Harbor Hermes CLI tests](https://raw.githubusercontent.com/harbor-framework/harbor/main/tests/unit/agents/installed/test_hermes_cli.py).
[^harbor-mcp]: [Harbor Hermes MCP tests](https://raw.githubusercontent.com/harbor-framework/harbor/main/tests/unit/agents/installed/test_hermes_mcp.py).
[^provider]: [Hermes provider runtime, including Codex](https://hermes-agent.nousresearch.com/docs/developer-guide/provider-runtime).
[^network]: [Harbor network-policy guide source](https://raw.githubusercontent.com/harbor-framework/harbor/main/docs-mintlify/tasks/network-policies.mdx).
[^deep-agent]: [DeepEval agent quickstart](https://deepeval.com/docs/getting-started-agents).
[^deep-schema]: [DeepEval test-case/tool schema](https://raw.githubusercontent.com/confident-ai/deepeval/main/deepeval/test_case/llm_test_case.py).
[^deep-rag]: [DeepEval RAG quickstart](https://deepeval.com/docs/getting-started-rag).
[^native]: [Hermes session-search runner](https://raw.githubusercontent.com/NousResearch/hermes-agent/main/evals/session_search_schema/runner.py); [current eval directory inventory](https://api.github.com/repos/NousResearch/hermes-agent/contents/evals).
[^readtool]: [Hermes readtool runner](https://raw.githubusercontent.com/NousResearch/hermes-agent/main/evals/readtool/runner.py) and [methodology](https://raw.githubusercontent.com/NousResearch/hermes-agent/main/evals/readtool/README.md).
[^browser]: [Hermes browser-use evaluation](https://raw.githubusercontent.com/NousResearch/hermes-agent/main/evals/browser_use/README.md).
[^toolperf]: [Hermes tool-performance runner](https://raw.githubusercontent.com/NousResearch/hermes-agent/main/evals/toolperf_abeval/ab_eval.py).
[^memory]: [Hermes memory snapshots and write behavior](https://hermes-agent.nousresearch.com/docs/user-guide/features/memory).
[^inspect]: [Inspect agent bridge](https://inspect.aisi.org.uk/agent-bridge.html).
[^phoenix]: [Phoenix self-hosting](https://arize.com/docs/phoenix/self-hosting), [current license](https://raw.githubusercontent.com/arize-ai/phoenix/main/LICENSE), and [README telemetry disclosure](https://raw.githubusercontent.com/arize-ai/phoenix/main/README.md).
[^braintrust]: [Braintrust self-hosting boundary](https://www.braintrust.dev/docs/admin/self-hosting); [Python SDK license](https://raw.githubusercontent.com/braintrustdata/braintrust-sdk-python/main/LICENSE).
