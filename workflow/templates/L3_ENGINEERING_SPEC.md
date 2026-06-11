# L3 Competition Engineering Spec

## 0. Metadata

- engineering_route_id:
- parent_route:
- parent_scoreboard:
- status: draft / planned / running / complete / rejected

## 1. Target Route

- strongest_model_or_ensemble:
- current_local_score:
- current_public_score:
- known_strengths:
- known_failures:

## 2. Engineering Lever

- lever_type: training / inference / postprocess / ensemble / compute / packaging
- proposed_change:
- expected_gain:
- expected_risk:
- affected_metric_component:

## 3. Validation Design

- matched_baseline:
- validation_split:
- hard_slices:
- control_slices:
- search_space:
- overfit_controls:
- stop_condition:

## 4. Rule And Leakage Check

- external_data_or_model_policy:
- public_test_feedback_risk:
- train_test_contamination_risk:
- submission_limit_risk:
- verdict:

## 5. Experiment Plan

- commands_or_plan_path:
- config_changes:
- artifacts:
- scoreboard_update:

## 6. Engineering Verdict

- verdict: promote_to_submission_intent / continue_search / reject / park
- reason:
- next_action:
