---
# catalog-derived-begin
title: "QwenAudio/qwen-audio-agent"
type: "repo-intel"
status: "active"
active: true
source_identity: "QwenAudio/qwen-audio-agent"
source: "https://github.com/QwenAudio/qwen-audio-agent"
source_categories: [["Reference Implementations","Demo Harnesses"]]
source_occurrences: [["Reference Implementations","Demo Harnesses"]]
# catalog-derived-end
review_state: reviewed
harness_intel_score: 78
score_confidence: medium
availability: available
last_reviewed: 2026-09-08
observed_revision: "1a043c597c29f3fd70e53f2a70bbe792e1c2b97f"
readme_path: "README.md"
readme_url: "https://github.com/QwenAudio/qwen-audio-agent/blob/1a043c597c29f3fd70e53f2a70bbe792e1c2b97f/README.md"
metadata_observed: 2026-09-08
license_url: "https://github.com/QwenAudio/qwen-audio-agent/blob/1a043c597c29f3fd70e53f2a70bbe792e1c2b97f/LICENSE"
---
# QwenAudio/qwen-audio-agent
## Quick take
Qwen Audio Agent is a realtime voice harness that keeps a conversational frontend present while a backend agent performs longer tasks.
## Score
**78/100**
- **Harness relevance — 24/30:** Wraps backend agents with continuous realtime voice, task lifecycle, gateway, skills, and multimodal interfaces.
- **Practical pattern value — 18/25:** ACP bridges, progress narration, gateway extensions, frontend/backend separation, and task cards are reusable interaction patterns.
- **Evidence and maturity — 16/20:** The active Apache-2.0 package has CI, documentation, multiple releases, desktop builds, and a support matrix.
- **Novelty — 13/15:** Maintaining conversational presence while a separate backend agent works is an unusually focused harness combination.
- **Risk-adjusted accessibility — 7/10:** npm and desktop paths help, but Node requirements, audio services, credentials, and backend-agent setup add complexity.
## Why it matters
- Its frontend and backend separation is a concrete pattern for narrating progress without blocking task execution.
- ACP support and gateway extensions connect the voice layer to several existing coding-agent runtimes.
## Caveat
The project is young and version 2.0 is still in development; audio providers, desktop packaging, credentials, and backend agents create a broad integration surface.
## Sources
[Repository](https://github.com/QwenAudio/qwen-audio-agent) · [README](https://github.com/QwenAudio/qwen-audio-agent/blob/1a043c597c29f3fd70e53f2a70bbe792e1c2b97f/README.md) · [License](https://github.com/QwenAudio/qwen-audio-agent/blob/1a043c597c29f3fd70e53f2a70bbe792e1c2b97f/LICENSE)
