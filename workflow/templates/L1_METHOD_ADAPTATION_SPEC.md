# L1 Method Adaptation Spec

## 0. Metadata

- route_id:
- method_id:
- parent_method_pool_spec:
- status: draft / planned / running / complete / rejected
- owner:
- created_at:

## 1. Source Method

- method_name:
- paper_or_solution:
- code_repo:
- license:
- pretrained_weights:
- source_tier:
- reproduction_status:

## 2. Task Fit

- matching_assumptions:
- mismatched_assumptions:
- required_input_adaptation:
- required_output_adaptation:
- metric_alignment:
- expected_failure_modes:

## 3. Local Adaptation Design

- data_interface_change:
- model_interface_change:
- loss_or_target_change:
- inference_change:
- checkpoint_loading_plan:
- config_plan:

## 4. Validation Plan

- baseline_to_compare:
- validation_split:
- hard_slices:
- control_slices:
- smoke_test:
- bounded_eval:
- full_eval_condition:

## 5. Implementation Plan Link

- plan_path:
- code_owner_files:
- expected_artifacts:

## 6. Experiment Record Requirements

- command:
- config:
- seed:
- checkpoint:
- logs:
- metrics:
- output_artifact:
- verdict:

## 7. Route Verdict

- verdict: continue / promote_to_L2_analysis / promote_to_L3_engineering / reject / park
- reason:
- next_action:
