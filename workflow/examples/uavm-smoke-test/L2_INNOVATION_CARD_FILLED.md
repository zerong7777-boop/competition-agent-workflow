# L2 Innovation Card: UAVM Smoke Fill

## 0. Metadata

- innovation_id: `uavm-i01-selective-angle-geometry-reasoning`
- linked_problem_card: `L2_PROBLEM_DEFINITION_CARD_FILLED.md`
- parent_l1_route: Reloc3r official + geometry/correspondence source diagnostics
- target_baseline: Reloc3r official hidden anchor / matched local same-surface replay
- validation_protocol: fixed same-surface replay with hard angle slice and distance-control slice
- status: accepted_to_structural_spec_for_example

## 1. Bottleneck Ledger

- bottleneck_sentence: Current direct RPR and external geometry routes can improve parts of heading evidence, but global fusion is unsafe because it can disturb base-sufficient or distance-protected cases.
- bottleneck_type: representation / information / generalization
- evidence:
  - Reloc3r official is the strongest hidden anchor
  - RoMa/MASt3R/VGGT expose complementary source behavior
  - Phase42 protects rank1 distance while seeking angle improvement
  - Phase40/43-style records show aggregate gains can miss target-balanced or promotion gates
- negative_evidence:
  - some frozen external geometry/head routes are weak or red
  - cheap non-leaky features may not be separable enough for safe gating
- why_current_baseline_fails:
  - a single direct prediction path does not explicitly separate when geometry evidence should modify heading from when the anchor should be preserved

## 2. Mechanism Scout

- related_paradigm:
  - P2 correspondence-aware regression
  - P6 geometry foundation fields
  - selective prediction / risk-coverage gating
  - residual correction with control preservation
- representative_methods:
  - RoMa dense field
  - MASt3R / DUSt3R pointmap-confidence geometry fields
  - VGGT geometry field
  - SAC-Pose-style correspondence-aware RPR
- what_mature_work_solved:
  - richer correspondence/geometry representations carry information that sparse match fields or direct RPR may miss
  - selective prediction separates intervention from no-op control behavior
- transferable_mechanism:
  - preserve base route by default, use geometry/correspondence evidence only for heading-specific correction under a bounded gate
- non_transferable_parts:
  - direct camera/pose outputs may not map cleanly to PairUAV heading/range
  - hidden-test feedback cannot tune the gate
- strongest_source_tier: Tier 1 local reproducible route evidence plus official anchor

## 3. Mechanism Ledger

- mechanism_claim: A selective heading-specific geometry branch can improve hard angle cases while preserving distance and base-sufficient controls.
- minimal_mechanism: On a fixed same-surface eval, a gated geometry branch improves hard angle slice without worsening distance parity or target-balanced controls.
- observable_signature:
  - hard angle slice improves
  - distance parity holds
  - control/base-sufficient slice does not regress
  - target-balanced angle does not regress
- control_signature:
  - no changes to final distance when the route is distance-protected
  - no hidden-feedback features in deployable gate
- falsifier:
  - hard angle slice does not improve
  - control slice regresses materially
  - distance parity fails
  - gains appear only under mismatched surface or leaky labels

## 4. Structure Ledger

- structural_rewrite: Add a separated geometry/correspondence evidence branch that can only produce a bounded heading correction through a non-leaky selective gate; preserve base distance by construction.
- changed_information_flow: external geometry evidence is not directly concatenated into the final head; it enters through a gated branch with no-op default behavior.
- changed_representation: heading evidence is represented separately from distance/range evidence.
- changed_optimization_condition: train/evaluate the intervention as a bounded residual correction against a matched base route rather than retraining a global regressor blindly.
- why_structure_not_trick:
  - not direct concatenation: branch activation is selective and auditable
  - not scalar weighting: the mechanism changes the prediction path for heading only
  - not arbitrary loss stacking: success requires hard/control slice signatures
  - not adapter-as-explanation: the gate and correction have explicit falsifiers
- baseline_invariance:
  - base distance unchanged
  - base heading unchanged when gate is off
- scale_behavior:
  - if mechanism is real, larger route-balanced source surfaces should improve coverage without breaking controls
- ablation_axis:
  - base only
  - geometry branch always on
  - gate only/no correction
  - selective heading correction
  - distance-protected vs non-distance-protected comparison

## 5. Strong Baseline And Ladder

- null_or_input_independent: constant or prior-only heading/range sanity baseline
- current_clean_baseline: Reloc3r official hidden anchor and matched local same-surface replay
- matched_baseline: same checkpoint, same manifest, same distance path, same eval code
- diagnostic_oracle: non-deployable geometry-source winner/oracle over source surfaces
- minimal_structure: heading-only gated residual with distance parity
- full_structure: route-balanced geometry/correspondence branch trained or fitted under non-leaky evidence policy

## 6. Bounded Falsification Plan

- minimal_dataset_or_split: fixed 4096/811 or val811 same-surface manifest
- compute_budget: bounded artifact/source replay before any full official inference
- fixed_seed_or_manifest: required
- hard_slice: hard angle or geometry-helpful cases
- control_slice: base-sufficient and target-balanced controls
- primary_metric: angle error improvement on hard slice
- secondary_metric: final proxy, distance parity, target-balanced angle
- stop_condition:
  - distance parity failure
  - target-balanced regression
  - no hard-slice improvement
  - leaky gate evidence
- promotion_condition:
  - hard angle slice improves
  - control slice stable
  - distance parity exact or within predeclared tolerance
  - same-surface replay clean

## 7. Risk

- rule_risk: medium if external data/pretrained models are used; must be audited per competition
- leakage_risk: high if gate uses target/error/oracle/official feedback features
- validation_risk: medium because local proxy and hidden official relation are imperfect
- compute_risk: medium-high for full geometry source generation
- implementation_complexity: high
- likely_failure_mode: gate coverage too low or correction harms true-admission/control cases

## 8. Card Gate Verdict

- verdict: accept_to_structural_spec
- reason: the card states a real problem, specific mechanism, control-preserving structure, and falsifiable bounded eval
- next_required_artifact: Structural Spec for selective angle geometry/correspondence reasoning
