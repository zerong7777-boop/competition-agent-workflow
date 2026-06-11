# L1 Method Pool Macro Spec: UAVM Smoke Fill

## 0. Metadata

- competition_task: UAVM PairUAV CodaBench
- linked_L0_contract: `L0_CONTRACT_SPEC_FILLED.md`
- created_at: `2026-06-10`
- status: example_only

## 1. Task Interpretation

- task_type: relative pose / heading-range prediction from image pairs
- input_modalities: paired UAV images
- output_target: heading and range/distance values for each test pair
- metric_driver: official final score combines angle and distance relative errors
- data_scale: official hidden submission recorded `2,773,116` rows
- compute_budget: historical task used lab RTX 3090 and remote RTX 5090-class host
- rule_constraints: no forbidden test/train leakage; preserve submission contract

## 2. Paradigm Taxonomy

| paradigm_id | paradigm_name | representative_methods | expected_strength | notes |
| --- | --- | --- | --- | --- |
| P1 | match-field regression | official SuperGlue baseline, EfficientLoFTR, RoMa | stable bridge | closest to official baseline; can degrade into plug-in engineering |
| P2 | correspondence/covisibility-aware regression | SAC-Pose, CoMatch, FAR, Alligat0R | research-shaped bridge | useful when direct RPR overfits priors |
| P3 | direct relative pose regression | Reloc3r official, Reloc3r v1/v2, MARePo-style shells | strongest current anchor | current hidden-official anchor is Reloc3r official |
| P4 | consistency/refinement | EquiPose, RePoseD, MapNet-like | enhancer | best as add-on after strong route stabilizes |
| P5 | explicit geometry solver | MADPose, PoseLib, PnP/E/F/H | high interpretability | convention/scale risk; current MADPose adapter negative |
| P6 | 3D / geometry foundation model | MASt3R, DUSt3R, VGGT | high ceiling | useful as frozen geometry fields or train-time teachers |
| P7 | retrieval/geolocalization pretraining | LPN, FSRA, TransGeo, University-1652-family references | auxiliary | not direct mainline under current evidence |

## 3. Method Pool

| method_id | paradigm_id | method_name | source_tier | code_maturity | expected_ceiling | adaptation_cost | rule_risk | validation_clarity | role |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| M1 | P3 | Reloc3r official | Tier 1/2 local proven | high after adaptation | high | medium | medium | high via hidden anchor | mainline |
| M2 | P1/P2 | RoMa dense field | Tier 1 local bounded | medium | medium-high | medium | medium | medium | source/control |
| M3 | P6/P2 | MASt3R geometry field | Tier 1 local bounded | medium | high angle | medium | medium | medium | angle source |
| M4 | P6 | VGGT geometry field | Tier 1 local bounded | medium | high distance | medium-high | medium | medium | source/control |
| M5 | P5 | MADPose official | Tier 1 local bounded negative | medium | unknown | high | medium-high | medium | held/rejected |
| M6 | P2 | SAC-Pose official-style | Tier 1 partial local | medium-low | high if redesigned | high | medium | low-medium | structural candidate |
| M7 | P1 | EfficientLoFTR | Tier 1 local bounded | high | medium | low | low | medium | fast control |

## 4. Ranking Rationale

- selected_first_wave:
  - `M1 Reloc3r official` as direct mainline and hidden-official anchor
  - `M2 RoMa dense`, `M3 MASt3R`, `M4 VGGT` as mechanism/source evidence, not immediate standalone submissions
- selected_second_wave:
  - `M6 SAC-Pose official-style` only after explicit redesign or if correspondence-aware route is reopened
  - `M7 EfficientLoFTR` as fast healthy matcher baseline/control
- parked_methods:
  - retrieval/geolocalization pretraining routes
  - consistency/refinement wrappers without a strong base route
- rejected_or_held_methods:
  - current MADPose adapter as standalone route
  - full three-source RoMa+MASt3R+VGGT as direct submission path

## 5. Adaptation Queue

| order | method_id | target_artifact | reason |
| --- | --- | --- | --- |
| 1 | M1 | Reloc3r official route anchor | strongest official hidden result |
| 2 | M1+source-policy | Reloc3r source-policy finetune diagnostic | use geometry/correspondence signals at train time while keeping test-time direct RPR |
| 3 | M3/M4/M2 | source complementarity/hybrid evidence | decide whether geometry fields solve angle/range subproblems differently |
| 4 | M6 | correspondence-aware structural redesign | only if L2 problem/card supports it |

## 6. L1 Scoreboard Schema

Recommended extra columns found by this smoke test:

- role: mainline / source / control / held / rejected
- evidence_surface: hidden_official / public_lb / full_local / bounded / smoke / diagnostic
- comparison_validity: direct / matched_surface / proxy_only / non_comparable

## 7. Stage Gate Verdict

- verdict: proceed_with_adaptation
- reason: historical route pool is rich enough to test ranking and macro decision workflow
- next_required_specs:
  - route scoreboard
  - macro route decision record
  - L2 problem card for angle improvement under distance preservation
