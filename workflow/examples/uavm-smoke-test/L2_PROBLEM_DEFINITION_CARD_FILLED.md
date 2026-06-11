# L2 Problem Definition Card: UAVM Smoke Fill

## 0. Metadata

- problem_id: `uavm-p01-angle-under-distance-preservation`
- source_stage: L1 / macro_route_decision
- related_routes:
  - Reloc3r official full-epoch hidden anchor
  - RoMa / MASt3R / VGGT geometry-source diagnostics
  - split-fusion and angle-splice attempts
- current_strongest_baseline: Reloc3r official full-data one-epoch hidden submission
- validation_protocol: fixed same-surface replay plus target-balanced controls
- status: accepted_for_example

## 1. Raw Phenomena

- metric_gap:
  - official hidden anchor is strong: `final_score=0.003188`, `distance_rel_error=0.002528`, `angle_rel_error=0.003849`
  - later macro decisions focus on improving angle while protecting the rank1 distance anchor
- slice_gap:
  - geometry/teacher signals help only sparse or route-specific subsets in historical audits
  - target-balanced controls can regress even when aggregate angle improves slightly
- case_patterns:
  - direct RPR is strong, but geometry/correspondence signals expose complementary angle/distance behavior
- leaderboard_gap:
  - user later reported current rank changed; not verified in this smoke test
- abnormal_logs_or_artifacts:
  - local official-style aggregate had near-zero angle denominator instability, so local aggregate cannot be treated as authoritative

## 2. Phenomenon Normalization

- repeated_across_runs: yes, multiple route records separate angle, distance, and proxy behavior
- repeated_across_methods: yes, RoMa/MASt3R/VGGT/MADPose/SAC-Pose/Reloc3r family records show different failure modes
- tied_to_specific_data_regime: yes, fixed PairUAV target/pair structure and hidden-test universe
- tied_to_specific_metric_component: yes, angle improvement is useful only if distance remains protected
- tied_to_specific_failure_mode: yes, helpful geometry can also harm control/base-sufficient cases

## 3. Problem Statement Drafts

1. Under PairUAV cases where the direct RPR anchor already predicts distance well, current strong baselines fail to improve heading safely because the task requires angle-specific geometric evidence without disturbing distance predictions.
2. Under heterogeneous PairUAV target regimes, current strong baselines fail to use external geometry consistently because the task requires distinguishing helpful geometry evidence from harmful control-risk evidence.
3. Under semantic or visual similarity that does not imply geometric solvability, current strong baselines fail to separate apparent matchability from reliable pose evidence because the task requires a solvability-aware evidence path.

## 4. Selected Problem Statement

Under PairUAV cases where the direct RPR anchor already predicts distance well, current strong baselines fail to improve heading safely because the task requires angle-specific geometric evidence without disturbing distance predictions.

## 5. Scope

- affected_regime:
  - rank1-distance-protected samples where heading can still be improved
  - cases where geometry/correspondence sources disagree with or refine the base route
- control_regime:
  - base-sufficient samples
  - target-balanced controls
  - samples where distance should remain identical or near-identical
- primary_metric_component: angle relative error / angle MAE on comparable validation surface
- secondary_metric_component: final score/proxy, distance relative error, distance parity
- excluded_cases:
  - package generation or hidden submission without intent gate
  - direct full official geometry source generation if cost is not feasible
- excluded_explanations:
  - validation bug as sole explanation
  - weak baseline as sole explanation
  - result-order or submission-format bug as sole explanation

## 6. False Problem Checks

- validation_split_bug_ruled_out: partially; fixed same-surface replay is required for each route
- metric_reconstruction_bug_ruled_out: partially; official hidden anchor is trusted, local aggregate instability is known
- submission_format_bug_ruled_out: yes for the Reloc3r hidden anchor package
- preprocessing_bug_ruled_out: route-dependent, not globally ruled out
- label_or_target_leakage_ruled_out: enforced as route guardrail, must be checked per bounded run
- weak_baseline_ruled_out: yes for Reloc3r official hidden anchor
- random_seed_or_split_artifact_ruled_out: partially; target-balanced and same-surface controls are required

## 7. Evidence Strength

- evidence_level: cross_method_supported
- strongest_evidence:
  - Reloc3r hidden official anchor
  - method paradigm summary separating RoMa/MASt3R/VGGT/Reloc3r roles
  - Phase42 macro route decision protecting rank1 distance while seeking angle upside
- weakest_assumption:
  - local bounded angle/source signals will transfer to hidden official universe
- missing_evidence:
  - current leaderboard/public rank refresh
  - a clean structural design that improves angle with distance parity under matched evaluation

## 8. Candidate Bottlenecks

- bottleneck_1: direct RPR anchor lacks selective angle-specific geometry correction that preserves distance invariance
- bottleneck_2: external geometry/correspondence sources are helpful only in specific regimes and unsafe if globally fused
- bottleneck_3: local validation cannot promote a route unless comparison surface and hidden-anchor relation are explicit

## 9. Problem Gate Verdict

- verdict: proceed_to_bottleneck_ledger
- reason: the problem is cross-method-supported, tied to a key metric component, and has explicit hard/control regimes
- next_required_artifact: L2 innovation card for selective angle geometry / correspondence reasoning
