---
# catalog-derived-begin
title: "aws-samples/sample-human-in-the-loop-patterns"
type: "repo-intel"
status: "active"
active: true
source_identity: "aws-samples/sample-human-in-the-loop-patterns"
source: "https://github.com/aws-samples/sample-human-in-the-loop-patterns"
source_categories: [["Design Primitives","Human-in-the-Loop"]]
source_occurrences: [["Design Primitives","Human-in-the-Loop"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 71
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "e7188fdf108b66d1052580355db6d8e54cd647d2"
readme_path: "README.md"
readme_url: "https://github.com/aws-samples/sample-human-in-the-loop-patterns/blob/e7188fdf108b66d1052580355db6d8e54cd647d2/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/aws-samples/sample-human-in-the-loop-patterns/blob/e7188fdf108b66d1052580355db6d8e54cd647d2/LICENSE"
---
# aws-samples/sample-human-in-the-loop-patterns
## Quick take
A focused AWS sample comparing four ways to pause sensitive agent tool calls for human approval.
## Score
**71/100**
- **Harness relevance — 23/30:** Demonstrates four approval mechanisms around sensitive agent tool calls.
- **Practical pattern value — 22/25:** Hook, per-tool, asynchronous workflow, and MCP elicitation examples provide reusable approval choices.
- **Evidence and maturity — 10/20:** The AWS sample is documented with deployment and test paths but is young and has no release evidence.
- **Novelty — 11/15:** Comparing centralized, fine-grained, third-party, and protocol-native approval in one sample is distinctive.
- **Risk-adjusted accessibility — 5/10:** MIT-0 helps reuse, but most methods require AWS credentials, deployment, and several managed services.
## Why it matters
- Makes the trade space between framework hooks, embedded policy, asynchronous approval, and MCP elicitation concrete.
- Each method includes its own agent entrypoint, deployment path, and test script.
## Caveat
Most examples depend on AgentCore and AWS infrastructure, and no deployment or behavioral test was performed for this review.
## Sources
[Repository](https://github.com/aws-samples/sample-human-in-the-loop-patterns) · [README](https://github.com/aws-samples/sample-human-in-the-loop-patterns/blob/e7188fdf108b66d1052580355db6d8e54cd647d2/README.md) · [License](https://github.com/aws-samples/sample-human-in-the-loop-patterns/blob/e7188fdf108b66d1052580355db6d8e54cd647d2/LICENSE)
