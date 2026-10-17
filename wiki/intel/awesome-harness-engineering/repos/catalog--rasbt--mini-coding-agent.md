---
# catalog-derived-begin
title: "rasbt/mini-coding-agent"
type: "repo-intel"
status: "active"
active: true
source_identity: "rasbt/mini-coding-agent"
source: "https://github.com/rasbt/mini-coding-agent"
source_categories: [["Reference Implementations","Tutorials & Educational"]]
source_occurrences: [["Reference Implementations","Tutorials & Educational"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 81
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "717cae4ff10d01773bd12951f62a575825053414"
readme_path: "README.md"
readme_url: "https://github.com/rasbt/mini-coding-agent/blob/717cae4ff10d01773bd12951f62a575825053414/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/rasbt/mini-coding-agent/blob/717cae4ff10d01773bd12951f62a575825053414/LICENSE"
---
# rasbt/mini-coding-agent
## Quick take
A minimal readable local coding agent that demonstrates six core harness components without a large framework.
## Score
**81/100**
- **Harness relevance — 29/30:** Implements a small complete coding-agent loop intended to expose core harness mechanics.
- **Practical pattern value — 24/25:** Live context, stable prompts, checked tools, approvals, compaction, transcripts, memory, and bounded delegation are reusable.
- **Evidence and maturity — 10/20:** The Apache-2.0 repository has a detailed README and companion tutorial but limited release or test evidence.
- **Novelty — 9/15:** The components are familiar, but their compact readable integration has strong educational value.
- **Risk-adjusted accessibility — 9/10:** The local Python and Ollama setup avoids hosted credentials, with model installation as the main prerequisite.
## Why it matters
- Shows stable prompt prefixes, structured tool validation, workspace controls, approvals, output clipping, and context reduction together.
- Separates durable transcripts from smaller working memory and includes bounded delegation and session resumption.
## Caveat
The backend is currently Ollama-specific, and this review did not run the agent or assess behavior across local model sizes.
## Sources
[Repository](https://github.com/rasbt/mini-coding-agent) · [README](https://github.com/rasbt/mini-coding-agent/blob/717cae4ff10d01773bd12951f62a575825053414/README.md) · [License](https://github.com/rasbt/mini-coding-agent/blob/717cae4ff10d01773bd12951f62a575825053414/LICENSE)
