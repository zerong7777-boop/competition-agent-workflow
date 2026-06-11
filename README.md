# Competition Agent Workflow

This repository contains a competition-specific, copy-on-write specialization of a local Agent Harness workflow.

It is designed for Kaggle / CodaBench style leaderboard climbing by expert users: first anchor the rules and validation protocol, then sweep strong task paradigms, then enter problem-driven structural innovation, and only generate submission packages after explicit gates pass.

- Project root: `E:\rz\research\tabbit_hackthon`
- Control-plane root: `E:\codex-home`
- Task id: `20260610-tabbit-ntu-workflow-hackathon`
- Upstream harness policy: read-only reference; copy and specialize only
- Primary goal: build a first-place-oriented workflow for AI-assisted competition leaderboard climbing

Start from [`workflow/COMPETITION_WORKFLOW_SPEC.md`](workflow/COMPETITION_WORKFLOW_SPEC.md).

Smoke-test example: [`workflow/examples/uavm-smoke-test`](workflow/examples/uavm-smoke-test).

Read first:

- [`workflow/GLOSSARY.md`](workflow/GLOSSARY.md)
- [`workflow/START_NEW_COMPETITION_CHECKLIST.md`](workflow/START_NEW_COMPETITION_CHECKLIST.md)
- [`workflow/reader-tests/20260610-subagent-reader-test.md`](workflow/reader-tests/20260610-subagent-reader-test.md)

Demo cut-down:

- [`demo/index.html`](demo/index.html): static local projection page
- [`demo/README.md`](demo/README.md)
- [`demo/DEMO_NARRATIVE.md`](demo/DEMO_NARRATIVE.md)
- [`demo/TABBIT_DEMO_SCRIPT.md`](demo/TABBIT_DEMO_SCRIPT.md)

Evidence images:

- [`rank1.jpg`](rank1.jpg): historical CodaBench rank-1 screenshot for `ze_rong` on 2026-05-09.
- [`rank2.png`](rank2.png): later screenshot showing `ze_rong` at rank 7.

The demo uses these screenshots as evidence only and does not claim real-time leaderboard status.
