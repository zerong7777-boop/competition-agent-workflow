# Submission Intent Record: Negative UAVM Smoke Fill

## 0. Metadata

- submission_candidate_id: `phase48-grelpose-pairuav-head-smoke`
- linked_route: GRelPose PairUAV frozen-feature head smoke
- linked_scoreboard: historical Phase48 results
- created_at: `2026-06-10`
- owner: workflow smoke-test

## 1. Candidate Summary

- artifact_candidate: no submission package should be generated
- local_validation_score:
  - best bounded head angle about `43.8259`, proxy about `0.2472`
  - required comparison anchor was Reloc3r10k angle about `8.6087`, proxy about `0.0516`
- hard_slice_summary: failed bounded feasibility gate
- control_slice_summary: not promoted to full comparison
- delta_vs_anchor: clearly worse than required anchor
- delta_vs_previous_best: clearly not competitive with rank1 shadow reference
- known_risks:
  - feature/task mismatch for frozen ScanNet/LoFTR/GRelPose features under cheap PairUAV head
  - full official inference would waste compute and submission opportunity

## 2. Provenance

- run_id: `phase48-grelpose-pairuav-head-smoke`
- config_path: source Phase48 spec/plan records, not copied into this smoke fill
- seed_or_fold: not restated in smoke fill
- command_or_script: `train_phase48_head.py` and related scripts recorded in source memory
- checkpoint_or_model: official GRelPose frozen features + PairUAV head smoke, source memory only
- prediction_artifact: Phase48 remote output recorded in source memory
- metric_file: Phase48 report/memory record
- validation_manifest: historical 4096/811 same-surface gate
- source_data_version: PairUAV historical local task records

## 3. Intent Gate

- verdict: do_not_package
- reason: bounded smoke was red; route should not create `result.zip` or submit
- required_before_packaging:
  - a different design using PairUAV-native supervision or official SuperGlue/match assets
  - new spec and bounded gate if route is reopened

## 4. Package Gate Checklist

Complete only if intent is `package_for_submission`.

- artifact_exists: not_applicable
- format_validated: not_applicable
- provenance_recorded: yes, historical route record exists
- rules_risk_acceptable: not_applicable
- expected_score_or_rank: not_applicable
- rollback_or_next_action: keep rank1 mainline and only continue geometry routes with a new design

## 5. Final Package Verdict

- verdict: cancelled
- package_path: none
- reason: not worth packaging; this is the canonical negative gate example
