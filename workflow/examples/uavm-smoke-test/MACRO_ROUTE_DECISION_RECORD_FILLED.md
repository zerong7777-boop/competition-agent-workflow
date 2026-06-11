# Macro Route Decision Record: UAVM Smoke Fill

## 0. Metadata

- decision_id: `uavm-phase42-smoke-recast`
- source_scoreboard: `ROUTE_SCOREBOARD_FILLED.md`
- created_at: `2026-06-10`
- status: example_only

## 1. Decision

Primary recommendation:

```text
keep_end_to_end_rank1_reloc3r_as_leaderboard_mainline
```

Next required document:

```text
end-to-end rank1 angle-improvement feasibility spec
```

## 2. Evidence

- Reloc3r official hidden result is the only complete official anchor in this smoke fill.
- Split-fusion / geometry routes are method-promising or mechanism evidence but not promotion-ready.
- Cheap-student residual compression and frozen GRelPose head evidence are insufficient for submission.
- RoMa / MASt3R / VGGT show useful source complementarity but should not become direct hidden submission paths without a new structural spec and bounded falsification.

## 3. Route State

```text
mainline:
  end-to-end rank1 / Reloc3r official family

protected output:
  final_distance = rank1 full-epoch distance

next action:
  write angle-improvement feasibility spec

stop:
  direct package generation for red bounded routes
  full three-source fusion as direct submission path
  cheap-student residual compression as current mainline

hold:
  RoMa / MASt3R / VGGT as source or mechanism evidence
  explicit geometry solver route until adapter/convention risk is solved
```

## 4. Gate Impact

- L1 remains open for method/source evidence, but new routes must declare paradigm and role.
- L2 should handle selective geometry/correspondence reasoning because the issue is structural: improve angle while preserving distance and controls.
- L3 can optimize only after a route is promotion-ready or explicitly selected as a mainline engineering target.
- Submission Intent Gate blocks any route whose bounded evidence is red or mismatched.

## 5. Next Artifact

- recommended: L2 Structural Spec for selective angle geometry/correspondence reasoning
- blocked: any immediate `result.zip` generation from held or red routes
