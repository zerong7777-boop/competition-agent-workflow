# L2 Problem Definition Card

## 0. Metadata

- problem_id:
- source_stage: L1 / leaderboard_feedback / L2_pre_scout
- related_routes:
- current_strongest_baseline:
- validation_protocol:
- status: draft / need_more_evidence / accepted / rejected / redirected

## 1. Raw Phenomena

- metric_gap:
- slice_gap:
- case_patterns:
- leaderboard_gap:
- abnormal_logs_or_artifacts:

## 2. Phenomenon Normalization

- repeated_across_runs:
- repeated_across_methods:
- tied_to_specific_data_regime:
- tied_to_specific_metric_component:
- tied_to_specific_failure_mode:

## 3. Problem Statement Drafts

Use the format:

```text
Under <data regime / task condition>, current strong baselines fail to <desired behavior>, because the task requires <missing capability / unresolved constraint>.
```

Draft at least two alternatives before selecting one.

1.
2.
3.

## 4. Selected Problem Statement


## 5. Scope

- affected_regime:
- control_regime:
- primary_metric_component:
- secondary_metric_component:
- excluded_cases:
- excluded_explanations:

## 6. False Problem Checks

- validation_split_bug_ruled_out:
- metric_reconstruction_bug_ruled_out:
- submission_format_bug_ruled_out:
- preprocessing_bug_ruled_out:
- label_or_target_leakage_ruled_out:
- weak_baseline_ruled_out:
- random_seed_or_split_artifact_ruled_out:

## 7. Evidence Strength

- evidence_level: anecdotal / single_run_supported / repeated_local_supported / slice_supported / cross_method_supported / leaderboard_supported
- strongest_evidence:
- weakest_assumption:
- missing_evidence:

## 8. Candidate Bottlenecks

- bottleneck_1:
- bottleneck_2:
- bottleneck_3:

## 9. Problem Gate Verdict

- verdict: proceed_to_bottleneck_ledger / need_more_evidence / send_back_to_L1 / send_to_L3 / send_back_to_L0 / reject_false_problem
- reason:
- next_required_artifact:
