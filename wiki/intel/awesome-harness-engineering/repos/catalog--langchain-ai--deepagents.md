---
# catalog-derived-begin
title: "langchain-ai/deepagents"
type: "repo-intel"
status: "active"
active: true
source_identity: "langchain-ai/deepagents"
source: "https://github.com/langchain-ai/deepagents"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 91
score_confidence: high
availability: available
last_reviewed: 2026-09-08
observed_revision: "5fb8b699843ecf93debc592d9dbb8a534f54db09"
readme_path: "README.md"
readme_url: "https://github.com/langchain-ai/deepagents/blob/5fb8b699843ecf93debc592d9dbb8a534f54db09/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/langchain-ai/deepagents/blob/5fb8b699843ecf93debc592d9dbb8a534f54db09/LICENSE"
---
# langchain-ai/deepagents
## Quick take
An opinionated, extensible harness bundling subagents, filesystem tools, context offloading, memory, approvals, skills, and shell access.
## Score
**91/100**
- **Harness relevance — 30/30:** Subagents, filesystems, context management, shell tools, memory, approvals, and skills make this a complete harness.
- **Practical pattern value — 24/25:** Isolated subagent contexts, pluggable backends, tool-call approval, and context offloading are directly transferable.
- **Evidence and maturity — 19/20:** LangChain actively maintains the documented MIT project atop LangGraph persistence, tracing, evaluation, and deployment infrastructure.
- **Novelty — 10/15:** The batteries-included combination is useful, though its individual agent, memory, and delegation primitives are established.
- **Risk-adjusted accessibility — 8/10:** MIT licensing and a short quick start help, but safe use depends on external tool and sandbox boundaries.
## Why it matters
- Provides a compact reference composition for long-horizon work without requiring a custom graph from scratch.
- Its pluggable filesystems and isolated subagent contexts expose clean extension boundaries.
## Caveat
The stated security model trusts the LLM and delegates enforcement to tool or sandbox boundaries, so defaults alone do not contain risky actions.
## Sources
[Repository](https://github.com/langchain-ai/deepagents) · [README](https://github.com/langchain-ai/deepagents/blob/5fb8b699843ecf93debc592d9dbb8a534f54db09/README.md) · [License](https://github.com/langchain-ai/deepagents/blob/5fb8b699843ecf93debc592d9dbb8a534f54db09/LICENSE)
