# L0 Contract & Validation Anchor Spec: UAVM Smoke Fill

## 0. Metadata

- competition_name: UAVM PairUAV CodaBench competition
- platform: CodaBench
- task_id: `20260417-uavm-pairuav-codabench`
- created_at: `2026-06-10`
- owner: workflow smoke-test
- status: example_only

## 1. Competition Contract

- official_url: `https://www.codabench.org/competitions/15251/#/results-tab`
- task_type: image-pair relative pose / heading-range prediction
- output_format: `result.zip` with root-level `result.txt`
- train_data: PairUAV train split
- test_data: name-masked competition test set
- external_data_policy: must be checked against official rules before use
- pretrained_weight_policy: must be checked against official rules before use
- submission_limit: not captured in this local smoke fill

## 2. Rule Audit

- allowed:
  - result submission through CodaBench
  - local validation and official-style dry runs
  - isolated exploration directories
- forbidden:
  - using University-1652 test split for training
  - using name-masked competition test set for training
  - overwriting mainline repos, checkpoints, running outputs, `result.txt`, or `result.zip` without explicit plan approval
- high_risk_actions:
  - hidden-test feedback tuning
  - package generation without submission intent gate
  - route promotion from weak or mismatched local proxy
- current_rule_risk: medium

## 3. Metric And Evaluation

- official_metric: final score with distance and angle relative errors, as recorded from official hidden-test feedback
- metric_direction: minimize
- metric_components:
  - `final_score`
  - `distance_rel_error`
  - `angle_rel_error`
- local_metric_status: reconstructed/proxy; historical official-style local aggregate had a near-zero angle denominator issue
- proxy_metric_limits:
  - local stable proxy can rank bounded routes but cannot replace official hidden-test feedback
  - old `devsplit_v1` scalar improvements should not override hidden official anchor
- metric_reconstruction_gate:
  - exact surface/provenance replay required before comparing a new route to the anchor

## 4. Validation Protocol

- split_candidates:
  - `devsplit_v1` full validation
  - fixed 4096/811 bounded surfaces
  - target-grouped or target-balanced splits for label-fitted gates
- selected_split: example uses historical 4096/811 and val811 references when available
- split_rationale: PairUAV has target/pair structure; default random split is unsafe
- leakage_checks:
  - no train/test identity overlap for split-fitted gates
  - no target ID, GT, error, oracle, official feedback, path/status/hash fields as deployable evidence
- hard_slices:
  - heading hard cases
  - geometry/semantic mismatch cases
  - false-admission risk cases
- control_slices:
  - base-distance-preserving cases
  - easy/base-sufficient cases
  - target-balanced controls
- validation_status: provisional but usable for smoke-test illustration

## 5. Official Baseline Anchor

- official_baseline_source: Reloc3r official full-data one-epoch long run, local task memory
- baseline_code_status: adapted official route exists in historical task
- baseline_checkpoint_status: full-data one-epoch checkpoint lineage recorded
- baseline_metric_public:
  - `final_score = 0.003188`
  - `distance_rel_error = 0.002528`
  - `angle_rel_error = 0.003849`
  - user/local record says it was rank 1 at submission time
- reproducibility_notes:
  - submitted zip SHA256 recorded as `4869611B0C79E960B701576F507AF44998A2DDF28590A5709F1136418D6DE771`
  - `result.txt` row count recorded as `2,773,116`

## 6. Submission Contract

- submission_format: root-level `result.txt` inside `result.zip`
- required_columns_or_files: exact line/column format not restated in this smoke fill
- dry_run_status: historical records include submission file audits and package checks
- known_failure_modes:
  - wrong root entry
  - wrong row count/order
  - package generated for a route that should have been held

## 7. Stage Gate Verdict

- verdict: proceed_to_L1
- reason: historical task has enough contract, metric, anchor, and validation records to support method-pool testing
- next_required_artifact: L1 method pool macro spec and route scoreboard
