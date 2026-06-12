# Status

## Current State

Competition Agent Harness Workflow v0.1.1 has been initialized under `E:\rz\research\tabbit_hackthon`.

## Done

- Created project-level task metadata.
- Created mature workflow spec covering L0-L3, submission gates, leaderboard feedback, and closeout.
- Created first-pass templates for L0, L1, L2, L3, submission intent, and leaderboard feedback.

## Missing

- A UAVM smoke-test instance has been instantiated for workflow usability testing; no fresh competition run has been started.
- No hackathon demo cut-down has been created yet.
- No fresh-reader test has been run yet.

## 2026-06-10 Smoke Test Update

- Added a UAVM smoke-test instantiation under `workflow/examples/uavm-smoke-test`.
- Added `ROUTE_SCOREBOARD.md` and `MACRO_ROUTE_DECISION_RECORD.md` templates after the smoke test exposed that expert competition work needs cross-stage route decisions.
- Updated the main workflow spec to reference these cross-cutting artifacts.
## 2026-06-10 Subagent Reader Test

- Ran three fresh-reader subagents against the workflow spec, templates, and UAVM smoke-test example.
- Verdicts: two `usable_with_minor_gaps`, one `usable_but_needs_narrative`.
- Reader-test report written to `workflow/reader-tests/20260610-subagent-reader-test.md`.
- Main gaps: gate thresholds, scoring scales, provenance fields, glossary, and end-to-end demo trace.
## 2026-06-10 Minimal Usability Pass

- Added `workflow/GLOSSARY.md`.
- Added `workflow/START_NEW_COMPETITION_CHECKLIST.md`.
- Updated `L1_METHOD_POOL_SPEC.md` with scoring scale and route role fields.
- Updated route, submission intent, and leaderboard feedback templates with provenance fields.
- Added `workflow/examples/uavm-smoke-test/END_TO_END_TRACE.md`.
- Updated UAVM filled examples to include provenance fields where available.
## 2026-06-11 Demo Cut-Down v1

- Created `demo/` presentation layer.
- Added narrative, slide outline, one-page workflow, UAVM evidence trace, compact route scoreboard, negative submission gate, and Tabbit demo script.
- Demo references `rank1.jpg` and `rank2.png` as screenshot evidence and explicitly avoids claiming live leaderboard status.
## 2026-06-12 Static Projection Page

- Added `demo/index.html` as a dependency-free browser projection page.
- The page uses local relative image references to `../rank1.jpg` and `../rank2.png`.
- The page presents the workflow in this order: evidence-backed opening, pain points, L0-L3 map, L1 method pool, L2 problem-driven innovation, rank screenshots, submission gate, Tabbit context surface, closing value.
## 2026-06-12 GitHub Publication

- Initialized a local git repository.
- Created public GitHub repository: `https://github.com/zerong7777-boop/competition-agent-workflow`.
- Pushed the workflow, templates, demo cut-down, static projection page, and rank evidence images to `main`.
- Local git author email is set to GitHub noreply for this repository to satisfy GitHub private email protection.
## 2026-06-12 Static Projection Page V2

- Reworked `demo/index.html` from a documentation-style projection page into a 3-5 minute hackathon presentation page.
- Strengthened the hero with rank evidence, GitHub repository entry, and a clearer positioning line.
- Reordered the presentation around pain point, control flow, L1 paradigm sweep, L2 problem-driven innovation, route scoreboard, submission stop gate, evidence chain, optional Tabbit surface, and closing value.
- Downgraded Tabbit from a main demo dependency to an optional context surface cameo.
- Verified desktop and mobile first-screen rendering with Chrome headless screenshots.
