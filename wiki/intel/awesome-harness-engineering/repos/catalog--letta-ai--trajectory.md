---
# catalog-derived-begin
title: "letta-ai/trajectory"
type: "repo-intel"
status: "active"
active: true
source_identity: "letta-ai/trajectory"
source: "https://github.com/letta-ai/trajectory"
source_categories: [["Design Primitives","Memory & State"]]
source_occurrences: [["Design Primitives","Memory & State"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "21ae92d10579499b183d93929c85da0b91233167"
readme_path: "README.md"
readme_url: "https://github.com/letta-ai/trajectory/blob/21ae92d10579499b183d93929c85da0b91233167/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/letta-ai/trajectory/blob/21ae92d10579499b183d93929c85da0b91233167/LICENSE"
---
# letta-ai/trajectory
## Quick take
A cross-harness transcript normalizer that produces deterministic records for evaluation, training, search, and memory formation.
## Score
**81/100**
- **Harness relevance — 20/30:** Trajectory is a substantial interoperability layer for harness transcripts and downstream agent-memory workflows.
- **Practical pattern value — 25/25:** Its typed adapters and deterministic normalized records are directly reusable for training, evaluation, search, and dreaming pipelines.
- **Evidence and maturity — 14/20:** The README documents installation, validation, development, and adapters for eight named runtimes, but the project is recent.
- **Novelty — 15/15:** A single validated trajectory schema across diverse coding-agent formats is unusually differentiated.
- **Risk-adjusted accessibility — 7/10:** Apache-2.0 licensing and a focused API help evaluation, though local transcript formats can drift and contain sensitive content.
## Why it matters
- Provides concrete adapters for Claude Code, Codex, Letta Code, OMP, OpenClaw, OpenCode, pi, and Deep Agents.
- Separates source-specific parsing from a validated common record model.
## Caveat
The young adapter set depends on private runtime formats that may change, and normalized trajectories can retain sensitive session content.
## Sources
[Repository](https://github.com/letta-ai/trajectory) · [README](https://github.com/letta-ai/trajectory/blob/21ae92d10579499b183d93929c85da0b91233167/README.md) · [License](https://github.com/letta-ai/trajectory/blob/21ae92d10579499b183d93929c85da0b91233167/LICENSE)
