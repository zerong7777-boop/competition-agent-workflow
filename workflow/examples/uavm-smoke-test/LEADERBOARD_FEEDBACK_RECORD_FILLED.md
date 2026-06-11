# Leaderboard Feedback Record: UAVM Smoke Fill

## 0. Metadata

- submission_id: `reloc3r-official-full-epoch-hidden-submit`
- linked_submission_intent: historical successful package gate, not recreated in this smoke test
- linked_route: Reloc3r official full-data one-epoch long run
- submitted_at: recorded locally around 2026-05-09
- platform: CodaBench
- leaderboard_timestamp: historical local record only; current 2026-06-10 rank not refreshed

## 1. Artifact And Provenance

- package_path:
  - local submitted zip: `D:\rz\课题\毕设\UAVM\submissions\reloc3r_official_full_epoch_result.zip`
  - 5090 source artifact: `/root/autodl-tmp/uavm_2026/runs/reloc3r_official_pairuav/official_test_infer_full_epoch_final_parallel_20260508_001619/result.zip`
  - lab backup: `/home/jgzn/UAVM_submission_sync/reloc3r_official_full_epoch_result.zip`
- config_or_checkpoint: full-data one-epoch Reloc3r official checkpoint lineage
- run_id: `official_metric_full_epoch_v1_20260506_045442`
- command_or_script: official test inference pipeline recorded in source memory
- prediction_artifact: root-level `result.txt` in `result.zip`
- local_validation_summary:
  - local official-style aggregate was unstable due to near-zero angle denominator issue
  - hidden official feedback is the strongest anchor
- provenance_notes:
  - zip root entry only `result.txt`
  - `result.txt` rows `2,773,116`
- artifact_hash: `4869611B0C79E960B701576F507AF44998A2DDF28590A5709F1136418D6DE771`

## 2. Leaderboard Result

- public_score: not refreshed in this smoke test
- public_rank: local record says user reported rank 1 at submission time; not current-rank verified
- private_or_hidden_score: `0.003188`
- private_or_hidden_rank: not independently refreshed in this smoke test
- metric_components:
  - `final_score = 0.003188`
  - `distance_rel_error = 0.002528`
  - `angle_rel_error = 0.003849`
- delta_vs_previous_submission: not reconstructed in smoke test
- delta_vs_anchor: this submission becomes the anchor
- abnormal_result: no

## 3. Verdict

- verdict: confirms_local
- reason: official hidden result is strong enough to become the route anchor despite local metric reconstruction limitations
- public_private_risk_note: not analyzed here; required near final selection or when public/private mismatch appears

## 4. Next Action

- next_action: continue_route
- reason: keep Reloc3r official as leaderboard mainline; future routes must beat or complement this anchor under matched validation and submission gates
- scoreboard_update_required: yes
