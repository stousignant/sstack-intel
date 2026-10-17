---
title: Skill Graphs
created: 2026-09-16
updated: 2026-09-19
type: concept
tags: [ai, agents, skills, context-engineering, knowledge-graphs]
sources:
  - https://x.com/akshay_pachaar/status/2024848778415755327
  - wiki/intel/github-repos/repos/agenticnotetaking--arscontexta.md
status: active
---

# Skill Graphs

> Reference-stack lens: [AI engineering](index.md).

## Definition

A **skill graph** is a progressively disclosed network of procedural or knowledge modules whose relationships help an agent select, order, execute, validate, or govern the minimum sufficient capabilities for a task.

The term is only architecturally meaningful when the graph adds more than hyperlinks. A mature operational skill graph needs:

- a compact root catalog or router for initial discovery;
- independently useful nodes with discriminating descriptions;
- contextual or typed edges;
- bounded traversal rules;
- validation for links, cycles, reachability, and incompatible assumptions;
- explicit authority and provenance behavior across edges;
- trajectory-level evals showing that the selected path improves task success.

Without those properties, “skill graph” is usually a useful metaphor for a linked Markdown knowledge base—not a distinct runtime primitive.

## Why the idea is attractive

The motivating post proposes recursively applying progressive disclosure: scan metadata, enter through a map, then follow contextual wikilinks only as far as the current problem requires.[1] This can make a large, non-linear domain navigable without loading it wholesale.

The underlying parts are established:

- The Agent Skills specification already defines a root `SKILL.md` plus on-demand `references/`, `scripts/`, and `assets/`.[2]
- Ars Contexta uses Markdown/YAML nodes, wikilink edges, Maps of Content, schema validation, graph diagnostics, and optional semantic search.[3][4]
- Ars Contexta explicitly frames curated notes as skill-like capabilities because they are loaded when relevant.[5]
- GraphRAG similarly distinguishes graph-structured retrieval from baseline vector retrieval, but it builds entity/relationship graphs and community summaries rather than procedural skill composition.[10]

The novelty is therefore not “Markdown can link to Markdown.” It is the **operational semantics, governance, and evaluation of those links**.

## Five graphs that must not be conflated

1. **Hyperlink/knowledge graph** — author-created links among explanatory notes and reference material.
2. **Library/retrieval graph** — relationships used to select a small, dependency-complete set of skills.
3. **Task/execution graph** — instantiated actions, preconditions, effects, data flow, gates, and recovery for one task.
4. **Learning/evolution graph** — relationships inferred or updated from trajectories and feedback.
5. **Package/supply-chain graph** — install-time dependencies, versions, publishers, hashes, and transitive risk.

An untyped `related` link is adequate for exploration but unsafe as an execution dependency. `A relates to B`, `A requires B`, `A produces input for B`, `A conflicts with B`, and `A must be verified by B` need different semantics.

A graph **inside one skill** is also different from a graph **between skills**. The former progressively discloses references or structures one workflow; the latter changes discovery, composition, authority, and lifecycle across separately maintained capability packages.

## Research landscape as of September 2026

The research has moved beyond the original wikilink framing. Four technical approaches are emerging.

### Dependency-aware retrieval

**Graph-of-Skills (GoS)** constructs a typed graph over skill packages and expands semantic/lexical seeds with reverse-aware Personalized PageRank so downstream matches recover prerequisites.[15] It is an inference-time retrieval graph: it chooses a bounded bundle but does not execute a workflow.

**SkillDAG** exposes typed neighbors and conflicts through an agent-callable interface and allows evidence-backed, reversible graph edits.[16] This makes the graph a stateful retrieval substrate rather than a fixed ranking pipeline, but it also creates a new graph-drift problem.

**SkillTrace** adds a query hierarchy above candidate matching and skill dependencies, explicitly treating complete composition—not independent top-k relevance—as the retrieval target.[17]

### Task-specific execution graphs

**GraSP** compiles retrieved skills into a task-specific typed DAG with state, data, and order edges, verifies pre/postconditions, and repairs only affected descendants after failure.[18] Its graph is an execution plan, not a persistent library map.

**Agent Instruction Protocol (AIP)** represents the internals of one skill as a schema-validated directed execution graph whose nodes are scripts or natural-language steps connected by typed inputs and outputs.[20] It improves structure and auditability inside a skill without defining portable skill-to-skill dependencies.

### Self-evolving graphs

**SkillGraph** uses prerequisite, enhancement, and co-occurrence edges, retrieves an ordered subgraph, and updates the library from trajectories and reinforcement-learning feedback.[19] This is the strongest form of the idea—and the riskiest operationally—because retrieval structure, learned policy, and library maintenance co-evolve.

### Install and governance graphs

Open-source tools are also exploring non-runtime graph layers:

- `context4ai/agent-graph` binds a skill to a typed action/gate workflow with legal outcome-dependent transitions.[29]
- Rune models a “skill mesh” of validated calls, reciprocal call edges, and asynchronous signals; routing remains model-mediated rather than scheduler-enforced.[30]
- `skilltree` resolves transitive cross-repository dependencies, semver constraints, cycles, topological installation, and lockfiles.[31]
- `sklock` validates local `requires` and containment edges, computes transitive hashes, and emits dependency locks and reverse graphs.[32]
- `quaylabshq/skill-graph` validates a lean root index plus linked category/reference nodes inside one skill; it is best understood as structured progressive disclosure, not a runtime dependency engine.[33]

These projects demonstrate that “skill graph” is becoming an umbrella term for at least four products: knowledge architecture, retrieval, workflow execution, and package management. Architecture discussions should always name which one is meant.

## What the evidence currently supports

### Focused skill sets beat indiscriminate loading

SkillsBench reports that curated skills raised mean pass rate from 33.9% to 50.5% across its paired evaluation, but 13 of 87 tasks regressed. Tasks using two or three skills gained more than tasks using four or more, supporting selective bundles rather than exhaustive context.[13]

SkillRet separately assembles 17,810 public skills and 4,997 evaluation queries. Its central finding is that off-the-shelf retrieval remains far from solved; task-specific training helps because useful skill signals are sparse inside long, noisy requests.[14]

The practical conclusion is not “use graphs everywhere.” It is: **once a library is large, retrieval quality becomes a first-class subsystem, and the target should be a small sufficient closure rather than a pile of individually similar documents.**

### Graph structure can recover missing prerequisites

GoS reports improvements over full loading and vector retrieval across SkillsBench and ALFWorld, including a peak 25.55% reward increase and 56.72% token reduction relative to full loading in one reported setting.[15] Its most decision-relevant result is narrower: reverse-aware traversal outperformed forward-only traversal because edge direction determines whether a selected downstream skill brings in its prerequisites.

SkillDAG and SkillTrace report further gains from typed neighborhood inspection, query decomposition, conflicts, and dependency propagation.[16][17] GraSP reports gains from compiling the selected set into a verified causal DAG rather than giving the model a flat list.[18]

### Structure alone is not proof

The direct graph evidence remains mostly recent preprints. Several methods reuse SkillsBench and ALFWorld, have limited independent replication, combine multiple innovations, or infer edges from model output. Reported gains therefore support bounded experiments, not a universal architectural mandate.

Important controls include:

- a strong flat hybrid retriever;
- full loading under the same context budget;
- a manually curated shallow router;
- an oracle skill set;
- graph traversal with direction removed or reversed;
- graph construction and retrieval cost;
- repeated runs and held-out domains.

A graph that beats a weak vector baseline but not a careful shallow router has not justified its complexity.

## Current standards and platform reality

The open Agent Skills standard defines a skill directory, discovery metadata, instructions, and optional resources. It does **not** define portable skill-to-skill imports, prerequisites, dependencies, conflicts, version constraints, or graph traversal.[2][12]

Current platforms converge on flat discovery plus model- or user-selected activation:

- **Anthropic/Claude:** multiple skills can be available or invoked together, but composition is model-mediated; no declared dependency graph is documented.[21]
- **OpenAI/Codex:** skills follow the open format. Product-specific `agents/openai.yaml` can declare MCP tool dependencies, not dependencies on other skills.[22]
- **GitHub Copilot:** skills are independently selected from descriptions or explicitly invoked; supporting resources are local to the selected skill.[23]
- **Gemini CLI:** `activate_skill(name)` loads one selected skill and its resource listing; multiple active skills still result from separate activation decisions.[24]

Custom metadata such as `related_skills` can support a private resolver, but other clients may ignore it. A portable `SKILL.md` must therefore remain useful when all graph-specific metadata is stripped.

This yields a compatibility rule:

> Treat graph metadata as an optional orchestration layer around standards-compliant skills, not as hidden behavior required for basic correctness.

## The default architecture

Use three levels, escalating only when evidence justifies the added routing burden.

### Level 1 — Cohesive root skill

Use one concise `SKILL.md` when the workflow is short, sequential, frequently changed, or safety-critical. Keep mandatory invariants, approvals, rollback, and verification together.

### Level 2 — Shallow router plus direct references

Use a root `SKILL.md` as the stable contract and link directly to focused references, scripts, and templates. This already provides progressive disclosure and is the best default for most Hermes/shared skills.

### Level 3 — Bounded operational graph

Use a typed graph only when:

- the domain is genuinely large and non-linear;
- different tasks need sparse, substantially different subsets;
- prerequisites or conflicts cannot be recovered reliably by flat retrieval;
- modules are reused across multiple workflows;
- a shallow index has produced repeated routing failures;
- graph validation, security review, and path-level evals are funded.

Even at Level 3, preserve a stable root contract. The graph should refine task execution, not silently redefine authority or intent.

## Main failure modes

### Root discovery still gates everything

Compatible clients generally expose only a skill's name and description during discovery; arbitrary leaf metadata is not globally discoverable by default.[2][12] A graph can improve navigation after activation, but it does not fix a root description that fails to trigger.

### Every hop adds another failure opportunity

The Skill-Use benchmark found that reliable triggering and procedure compliance remain unsolved even for ordinary skills.[8] Graph traversal adds first-hop selection, prerequisite coverage, stopping decisions, edge interpretation, and node integration.

### Traversal can cost more than it saves

Dynamic discovery has value only when avoided context outweighs search latency and intermediate results; Anthropic states this trade-off explicitly for tool search.[9] The same rule applies to reference and skill graphs.

### Fragmentation can separate invariants from actions

Over-decomposition can strand safety checks, exceptions, rollback instructions, or verification away from the procedure they govern. Operational work should bias toward coherence; exploratory knowledge can tolerate looser composition.

### Maps and links drift

A link may still resolve while its description, direction, assumptions, or target version is stale. Ars Contexta's kernel therefore includes schema validation, link checks, MOC coverage, graph analysis, and maintenance loops.[4] “Just Markdown” is insufficient without upkeep.

### Reuse creates coupling

A shared node reduces duplication but expands blast radius. Changes require inbound-link review, compatibility assumptions, and evals for dependent paths.

### Learned edges can compound mistakes

Online graph edits can improve recall, but one successful trajectory does not establish a generally valid dependency. Self-evolving graphs need evidence thresholds, append-only history, rollback, contradiction detection, and periodic revalidation against held-out tasks.[16][19]

## Security contract for transitive skill graphs

Skills are both executable artifacts and instruction-bearing context. A graph turns skill loading into a package resolver, authorization-delegation system, retrieval pipeline, and update channel simultaneously.

The risk is empirical:

- Skill-Inject reports attack success rates up to 80% from malicious instructions embedded in skill files.[25]
- CompoSkill shows that individually scanner-passing skills can form risky chains; it reports chain-formation rates up to 83.3% in white-box and 80.6% in black-box settings.[26]
- A supply-chain study over more than 1.43 million skills found that skill, package, and service dependencies are often implicit and that security-relevant signals can hide in transitive dependencies.[27]
- SkillGuard's permission model reduced, but did not eliminate, contextual and obvious injection success—evidence that manifests and runtime controls help but are not a complete defense.[28]

A secure skill graph therefore requires:

1. **Non-transitive trust.** Approving a root skill does not approve every reachable publisher, instruction, script, service, or tool.
2. **Fully qualified identity.** Resolve `registry + publisher + skill + immutable version/digest`; never depend on a bare display name.
3. **Locked closure.** Resolve the complete acyclic graph before execution and record node hashes, edge purposes, versions, publishers, and all root-to-node paths.
4. **Authority intersection, never union.** A node's effective authority is bounded by platform policy, the user grant, the root contract, the edge delegation, and the node declaration. Loading a child cannot increase authority.
5. **Path-level review.** Node-level scans are insufficient because risk can emerge only when outputs, permissions, or side effects compose.[26]
6. **Context provenance.** Preserve source and trust labels through retrieval and summarization; imported text must not become indistinguishable from root policy.
7. **Hard bounds.** Enforce maximum depth, fan-out, nodes, tokens, resolver time, runtime calls, and iteration counts.
8. **Change gates.** Recompute and review the closure when a node, edge, publisher, capability, hash, or tool schema changes.
9. **External policy enforcement.** Validate tool calls against the original user request and deterministic policy, not only the composite model context.
10. **Revocation and rollback.** Be able to invalidate every closure containing a compromised digest without accepting a rollback to an older vulnerable graph.

The strongest invariant is:

> Loading a dependency may add knowledge or reduce available authority; it must never silently expand authority, replace trusted intent, or introduce an unreviewed publisher.

## Evaluation contract

Do not adopt a graph because it looks organized. Compare it against a shallow baseline using:

### Discovery and retrieval

- root trigger precision and recall;
- correct first-hop and full-path selection;
- prerequisite-closure recall;
- irrelevant-node avoidance;
- conflict and supersession detection;
- edge precision by type and direction.

### Execution

- task success and boundary compliance;
- safe stopping and cycle handling;
- pre/postcondition satisfaction;
- failure-localization and repair cost;
- behavior when a required node is missing or stale.

### Efficiency and maintenance

- tokens, tool calls, latency, and index/build cost;
- resilience after node edits, renames, and topology changes;
- graph drift and rollback accuracy;
- human review time compared with a shallow router.

### Security

- effective permission closure;
- unreviewed publisher and dependency detection;
- prompt-injection propagation across two and three hops;
- path-level attacks composed from individually benign nodes;
- lockfile, digest, freshness, and revocation behavior.

The success metric is **better completed work under the same safety constraints**, not more nodes, prettier visualization, or lower nominal context alone.

## Hermes/GBrain/Wikic integration boundary

In the documented reference stack, Hermes and its owned skill repository form the procedural control plane; the Markdown vault/GBrain is the knowledge data plane; Wikic is the deterministic integrity layer. Root skills with direct references can call graph-shaped knowledge without making every knowledge note a separately routable skill.

For a Hermes-based skill library, pilot retrieval-only typed edges (`requires`, `conflicts_with`, `verify_with`, `supersedes`) only after a concrete shallow-routing failure. Keep execution and authority in the root, avoid self-evolving edges and transitive code loading initially, and compare against the shallow baseline before promotion.

This is narrower than “skill graphs do not work”: inferred edges are weak architecture truth when reviewed packages already declare routing and ownership. Deterministic cross-reference/metadata analysis is a better fit for stable ownership maps; use inference to propose review questions, not silently replace them.

## Related

- [Coding Agent Skill Systems](coding-agent-skill-systems.md)
- [Thin Harness, Fat Skills](thin-harness-fat-skills.md)
- [LLM Wiki Pattern](llm-wiki-pattern.md)
- [Knowledge Graph vs RAG](knowledge-graph-vs-rag.md)
- [gbrain](https://github.com/garrytan/gbrain)
- wikic
- [akshay pachaar skill graphs](https://x.com/akshay_pachaar/status/2024848778415755327)
- [agenticnotetaking  arscontexta](../../intel/github-repos/repos/agenticnotetaking--arscontexta.md)

## Sources

[1] https://x.com/akshay_pachaar/status/2024848778415755327 — Akshay Pachaar — Skill Graphs > SKILL.md
[2] https://agentskills.io/specification — Agent Skills specification
[3] https://github.com/agenticnotetaking/arscontexta/blob/2acfd5cc4473c4d06c46be63df748e77e00e2746/README.md — Ars Contexta README at 2acfd5c
[4] https://github.com/agenticnotetaking/arscontexta/blob/2acfd5cc4473c4d06c46be63df748e77e00e2746/reference/kernel.yaml — Ars Contexta kernel.yaml at 2acfd5c
[5] https://github.com/agenticnotetaking/arscontexta/blob/2acfd5cc4473c4d06c46be63df748e77e00e2746/methodology/notes%20are%20skills%20%E2%80%94%20curated%20knowledge%20injected%20when%20relevant.md — Ars Contexta — notes are skills
[8] https://arxiv.org/abs/2608.04828 — Skill-Use benchmark
[9] https://www.anthropic.com/engineering/advanced-tool-use — Anthropic — advanced tool use
[10] https://microsoft.github.io/graphrag — Microsoft GraphRAG
[12] https://agentskills.io/client-implementation/adding-skills-support — Agent Skills client implementation guide
[13] https://arxiv.org/abs/2602.12670 — SkillsBench
[14] https://arxiv.org/abs/2605.05726 — SkillRet
[15] https://arxiv.org/abs/2604.05333 — Graph-of-Skills
[16] https://arxiv.org/abs/2606.03056 — SkillDAG
[17] https://arxiv.org/abs/2608.02356 — SkillTrace
[18] https://arxiv.org/abs/2604.17870 — GraSP
[19] https://arxiv.org/abs/2605.12039 — SkillGraph
[20] https://arxiv.org/abs/2606.04781 — Agent Instruction Protocol
[21] https://code.claude.com/docs/en/skills — Claude Code skills documentation
[22] https://developers.openai.com/codex/skills — OpenAI Codex skills documentation
[23] https://docs.github.com/en/copilot/how-tos/use-copilot-agents/coding-agent/create-skills — GitHub Copilot agent skills documentation
[24] https://geminicli.com/docs/cli/skills — Gemini CLI Agent Skills documentation
[25] https://arxiv.org/abs/2602.20156 — Skill-Inject
[26] https://arxiv.org/abs/2608.16246 — CompoSkill
[27] https://arxiv.org/abs/2607.01136 — Skills Are Not Islands
[28] https://arxiv.org/abs/2606.03024 — SkillGuard
[29] https://github.com/context4ai/agent-graph — context4ai/agent-graph
[30] https://github.com/Rune-kit/rune — Rune skill mesh
[31] https://github.com/imarios/skilltree — skilltree
[32] https://github.com/artieax/sklock — sklock
[33] https://github.com/quaylabshq/skill-graph — quaylabshq/skill-graph
