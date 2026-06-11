# Submission Intent Record

## 0. Metadata

- submission_candidate_id:
- linked_route:
- linked_scoreboard:
- created_at:
- owner:

## 1. Candidate Summary

- artifact_candidate:
- local_validation_score:
- hard_slice_summary:
- control_slice_summary:
- delta_vs_anchor:
- delta_vs_previous_best:
- known_risks:

## 2. Provenance

- run_id:
- config_path:
- seed_or_fold:
- command_or_script:
- checkpoint_or_model:
- prediction_artifact:
- metric_file:
- validation_manifest:
- source_data_version:

If these fields are incomplete, do not use this record as strong submission evidence without a written exception.

## 3. Intent Gate

- verdict: do_not_package / need_more_validation / hold_for_final_merge / package_for_submission
- reason:
- required_before_packaging:

## 4. Package Gate Checklist

Complete only if intent is `package_for_submission`.

- artifact_exists:
- format_validated:
- provenance_recorded:
- rules_risk_acceptable:
- expected_score_or_rank:
- rollback_or_next_action:

## 5. Final Package Verdict

- verdict: ready_to_submit / blocked / cancelled
- package_path:
- reason:
