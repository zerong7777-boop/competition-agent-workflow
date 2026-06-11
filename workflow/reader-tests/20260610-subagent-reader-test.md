# Subagent Reader Test: Competition Workflow v0.1.1

Date: 2026-06-10
Scope: read-only fresh-reader evaluation of the competition Agent Harness workflow.

## Inputs

- `workflow/COMPETITION_WORKFLOW_SPEC.md`
- selected templates under `workflow/templates/`
- UAVM smoke-test example under `workflow/examples/uavm-smoke-test/`

## Agents

| agent | role | verdict |
| --- | --- | --- |
| Godel | main spec fresh reader | `usable_with_minor_gaps` |
| Cicero | new-competition practitioner | `usable_with_minor_gaps` |
| Dewey | skeptical demo reviewer | `usable_but_needs_narrative` |

## What Worked

- The core stage flow is understandable: L0 -> L1 -> L2 -> L3 -> route decision -> submission gates -> leaderboard feedback -> closeout.
- A new competition should start from L0 contract, validation, metric, baseline, and submission anchoring.
- L1/L2/L3 boundaries are mostly clear:
  - L1: mature paradigm and strong-method adaptation sweep.
  - L2: problem-driven structural innovation.
  - L3: competition engineering optimization.
- Submission package generation is clearly gated: only `package_for_submission` allows packaging.
- Route Scoreboard and Macro Route Decision are necessary and useful for multi-route expert decision making.
- UAVM smoke-test demonstrates that the workflow can represent real competition artifacts, held routes, negative submission intent, and macro route decisions.

## Main Gaps

1. Gate thresholds are under-specified.
   - `trusted / provisional / blocked`
   - `credible strongest baseline`
   - `serious route`
   - `card gate acceptance`

2. Scoring and ranking scales are under-specified.
   - L1 fields such as `expected_ceiling`, `code_maturity`, `adaptation_cost`, `compute_cost`, and `validation_clarity` need a common scale.

3. Provenance fields are not yet mandatory enough.
   - Scoreboard and submission records should include `run_id`, `config_path`, `seed_or_fold`, and `command_or_script`.

4. The workflow needs a short glossary.
   - `smoke`, `bounded`, `full`, `diagnostic`, `hard slice`, `control slice`, `source tier`, `trusted`, `provisional`, `blocked`.

5. Hackathon demo needs a narrative trace.
   - The UAVM smoke-test proves template fit, but a judge would still want an end-to-end trace from raw competition intake to L0/L1/L2/L3 decisions and submission gating, with links to artifacts and scores.

## Recommended Minimal Revisions

- Add `workflow/GLOSSARY.md`.
- Add `workflow/START_NEW_COMPETITION_CHECKLIST.md`.
- Add scoring scale notes to `L1_METHOD_POOL_SPEC.md`.
- Add provenance columns to `ROUTE_SCOREBOARD.md`.
- Add provenance fields to `SUBMISSION_INTENT_RECORD.md` and `LEADERBOARD_FEEDBACK_RECORD.md`.
- Add a short `workflow/examples/uavm-smoke-test/END_TO_END_TRACE.md` before building the hackathon demo narrative.

## Overall Verdict

The workflow is usable for an expert user now. It is strong enough to proceed, but before presentation it should receive a small usability pass focused on gate definitions, provenance, and the end-to-end trace narrative.
