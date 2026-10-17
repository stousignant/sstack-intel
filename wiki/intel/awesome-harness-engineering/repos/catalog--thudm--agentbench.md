---
# catalog-derived-begin
title: "THUDM/AgentBench"
type: "repo-intel"
status: "active"
active: true
source_identity: "THUDM/AgentBench"
source: "https://github.com/THUDM/AgentBench"
source_categories: [["Design Primitives","Verification & CI Integration"]]
source_occurrences: [["Design Primitives","Verification & CI Integration"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 77
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "d1e4a10db08c87075c78972e48ecc182be03e2d5"
readme_path: "README.md"
readme_url: "https://github.com/THUDM/AgentBench/blob/d1e4a10db08c87075c78972e48ecc182be03e2d5/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/THUDM/AgentBench/blob/d1e4a10db08c87075c78972e48ecc182be03e2d5/LICENSE"
---
# THUDM/AgentBench
## Quick take
A research benchmark and containerized evaluation harness for testing agents across operating systems, databases, knowledge graphs, web tasks, and embodied environments.
## Score
**77/100**
- **Harness relevance — 20/30:** AgentBench is a substantial verification environment for agents rather than a general-purpose runtime harness.
- **Practical pattern value — 22/25:** Containerized task workers, controller allocation, extension points, and multi-environment evaluation are reusable patterns.
- **Evidence and maturity — 20/20:** ICLR publication, datasets, leaderboards, multiple releases, and institutional stewardship provide strong evidence.
- **Novelty — 11/15:** Unified evaluation across heterogeneous interactive environments remains a distinctive verification design.
- **Risk-adjusted accessibility — 4/10:** Apache-2.0 is permissive, but old dependencies, Docker services, large datasets, and high RAM needs make evaluation heavy.
## Why it matters
- Offers a reusable controller-worker architecture for heterogeneous interactive agent evaluations.
- Provides both function-calling and historical benchmark variants with documented extension points.
## Caveat
Several tasks require substantial Docker, data, memory, and older Python dependencies, and the README notes a memory leak in one worker.
## Sources
[Repository](https://github.com/THUDM/AgentBench) · [README](https://github.com/THUDM/AgentBench/blob/d1e4a10db08c87075c78972e48ecc182be03e2d5/README.md) · [License](https://github.com/THUDM/AgentBench/blob/d1e4a10db08c87075c78972e48ecc182be03e2d5/LICENSE)
