# Template Gap Audit From UAVM Smoke Test

## Summary

The v0.1 workflow is usable, but the UAVM trial exposed two missing cross-stage artifacts:

1. A route scoreboard template.
2. A macro route decision record template.

Without these, L1/L2/L3 artifacts exist but an expert user lacks a compact decision surface for fast leaderboard strategy.

## Gaps

### 1. Route Scoreboard Is First-Class

UAVM has many routes that are not comparable by a single score:

- hidden official anchor;
- local full-dev proxy;
- bounded 2048/4096/811 probes;
- smoke-only route health;
- diagnostic mechanism evidence;
- held source routes.

The workflow needs a standard scoreboard to show route role, evidence tier, comparison surface, status, and next action.

### 2. Macro Route Decision Record Is First-Class

The UAVM Phase42 decision was not a submission gate and not a method spec. It was a strategic route decision:

```text
keep Reloc3r official as mainline
protect rank1 distance
seek angle improvement through a bounded spec
hold geometry/source routes as evidence
```

This kind of decision is common in expert competition work and should have its own template.

### 3. L1 Method Pool Needs Role, Not Only Ranking

A method can be:

- mainline;
- source/teacher;
- diagnostic control;
- ensemble member;
- held route;
- rejected route.

A raw ranking is not enough.

### 4. L2/L3 Boundary Needs A Field

The trial confirmed the L2/L3 split matters. Training recipe, threshold search, pseudo-labeling, and packaging are L3 unless tied to a structural bottleneck and Innovation Card.

### 5. Current Leaderboard Status Must Be Timestamped

Historical rank and current rank can diverge. Any public rank field should include source and timestamp, or explicitly say not refreshed.

## Action Taken In v0.1.1

Added templates:

- `workflow/templates/ROUTE_SCOREBOARD.md`
- `workflow/templates/MACRO_ROUTE_DECISION_RECORD.md`

Updated the main workflow spec to reference these as cross-cutting artifacts.
## Action Taken In Usability Pass

Added workflow-level usability files:

- `workflow/GLOSSARY.md`
- `workflow/START_NEW_COMPETITION_CHECKLIST.md`

Updated templates:

- `L1_METHOD_POOL_SPEC.md`: added 1-5 scoring scale and role field.
- `ROUTE_SCOREBOARD.md`: added provenance requirements and run/config/seed/command fields.
- `SUBMISSION_INTENT_RECORD.md`: added provenance section before the intent gate.
- `LEADERBOARD_FEEDBACK_RECORD.md`: added artifact/provenance fields and leaderboard timestamp.

Updated example:

- Added `END_TO_END_TRACE.md`.
- Updated route scoreboard, negative submission intent, and leaderboard feedback examples with provenance fields.
