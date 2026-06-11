# Route Scoreboard

## 0. Metadata

- competition_task:
- linked_L0_contract:
- updated_at:
- status: draft / active / archived

## 1. Scoreboard

| route_id | stage | paradigm_id | method_or_route | role | evidence_surface | best_metric | hard_slice | control_slice | run_id | config_path | seed_or_fold | command_or_script | artifact | status | next_action |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| R1 |  |  |  | mainline / source / control / ensemble / held / rejected | hidden_official / public_lb / full_local / bounded / smoke / diagnostic |  |  |  |  |  |  |  |  |  |  |

## 2. Anchor Routes

- leaderboard_anchor:
- strongest_local_anchor:
- safest_submission_anchor:
- highest_upside_unpromoted_route:

## 3. Comparison Warnings

- non_comparable_surfaces:
- proxy_metric_limitations:
- smoke_only_routes:
- diagnostic_only_routes:
- rule_or_leakage_risks:

## 4. Provenance Requirements

Every score used for a decision should include at least one stable artifact path and, when applicable:

- `run_id`
- `config_path`
- `seed_or_fold`
- `command_or_script`
- `checkpoint_or_model`
- `metric_file`
- `submission_id_or_leaderboard_timestamp`

If provenance is incomplete, set `evidence_surface` or `status` to provisional.

## 5. Decision Queue

| priority | decision_needed | candidate_routes | required_artifact | owner |
| --- | --- | --- | --- | --- |
| 1 |  |  |  |  |

## 6. Update Rules

- Every real submission must update this scoreboard.
- Every completed bounded/full eval must update this scoreboard.
- Smoke-only routes cannot be ranked above bounded/full routes without an explicit warning.
- Hidden official scores, public leaderboard scores, and local proxies must be labeled separately.
