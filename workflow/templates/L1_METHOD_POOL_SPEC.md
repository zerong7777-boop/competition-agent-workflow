# L1 Method Pool Macro Spec

## 0. Metadata

- competition_task:
- linked_L0_contract:
- created_at:
- status: draft / active / complete

## 1. Task Interpretation

- task_type:
- input_modalities:
- output_target:
- metric_driver:
- data_scale:
- compute_budget:
- rule_constraints:

## 2. Paradigm Taxonomy

List mature paradigms that plausibly solve this task.

| paradigm_id | paradigm_name | representative_methods | expected_strength | notes |
| --- | --- | --- | --- | --- |
| P1 |  |  |  |  |

## 3. Scoring Scale

Use `1-5` unless a task-specific scale is justified.

- `5`: strong advantage / low risk / high confidence.
- `3`: usable but uncertain or medium cost.
- `1`: weak, risky, expensive, or unclear.

For cost and risk fields, invert the score so higher is better:

- `adaptation_cost_score`: `5` means cheap/easy, `1` means expensive/hard.
- `compute_cost_score`: `5` means cheap, `1` means expensive.
- `rule_safety_score`: `5` means low rule risk, `1` means high rule risk.

Recommended holistic score:

```text
0.25 * expected_ceiling
+ 0.20 * task_fit
+ 0.15 * code_maturity
+ 0.10 * pretrained_available
+ 0.10 * adaptation_cost_score
+ 0.10 * compute_cost_score
+ 0.05 * rule_safety_score
+ 0.05 * ensemble_value
```

Override weights when task-specific reasons are recorded.

## 4. Method Pool

| method_id | paradigm_id | method_name | source_tier | pretrained_available | code_maturity | expected_ceiling | task_fit | adaptation_cost_score | compute_cost_score | rule_safety_score | validation_clarity | ensemble_value | holistic_score | role |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| M1 |  |  |  |  |  |  |  |  |  |  |  |  |  | mainline / source / control / ensemble / held / rejected |

## 5. Ranking Rationale

Rank by a holistic score, then review manually for strategic diversity and rule risk.

- selected_first_wave:
- selected_second_wave:
- parked_methods:
- rejected_methods:
- override_notes:

## 6. Adaptation Queue

Each selected non-trivial method must get its own L1 method adaptation spec.

| order | method_id | target_artifact | reason |
| --- | --- | --- | --- |
| 1 |  |  |  |

## 7. L1 Scoreboard Schema

- route_id:
- method_id:
- role:
- evidence_surface: hidden_official / public_lb / full_local / bounded / smoke / diagnostic
- run_id:
- config_path:
- seed_or_fold:
- command_or_script:
- checkpoint:
- validation_split:
- local_metric:
- hard_slice_metric:
- control_slice_metric:
- artifact_path:
- verdict:
- next_action:

## 8. Stage Gate Verdict

- verdict: proceed_with_adaptation / need_more_research / return_to_L0
- reason:
- next_required_specs:
