# L0 Contract & Validation Anchor Spec

## 0. Metadata

- competition_name:
- platform:
- task_id:
- created_at:
- owner:
- status: draft / active / blocked / complete

## 1. Competition Contract

- official_url:
- task_type:
- input_format:
- output_format:
- train_data:
- test_data:
- external_data_policy:
- pretrained_weight_policy:
- team_policy:
- submission_limit:
- deadline:

## 2. Rule Audit

- allowed:
- forbidden:
- ambiguous:
- high_risk_actions:
- questions_to_ask_organizers:
- current_rule_risk: low / medium / high / blocked

## 3. Metric And Evaluation

- official_metric:
- metric_direction: maximize / minimize
- metric_components:
- available_metric_code:
- local_metric_status: exact / reconstructed / proxy / unknown
- proxy_metric_limits:
- metric_reconstruction_gate:

## 4. Validation Protocol

- split_candidates:
- selected_split:
- split_rationale:
- leakage_checks:
- hard_slices:
- control_slices:
- repeat_policy:
- validation_status: trusted / provisional / blocked

## 5. Official Baseline Anchor

- official_baseline_source:
- baseline_code_status:
- baseline_checkpoint_status:
- baseline_metric_local:
- baseline_metric_public:
- reproducibility_notes:

## 6. Submission Contract

- submission_format:
- required_columns_or_files:
- packaging_command:
- validation_command:
- dry_run_status:
- known_failure_modes:

## 7. Stage Gate Verdict

- verdict: proceed_to_L1 / fix_L0 / blocked
- reason:
- next_required_artifact:
