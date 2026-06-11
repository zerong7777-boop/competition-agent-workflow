# UAVM End-To-End Trace

This trace is a presentation-oriented reconstruction from local Agent Harness records. It is not a fresh CodaBench investigation and does not claim the current leaderboard rank on 2026-06-10.

## 1. Raw Competition Intake

Input evidence:

- Competition URL: `https://www.codabench.org/competitions/15251/#/results-tab`
- Local task: `E:\codex-home\tasks\20260417-uavm-pairuav-codabench\task.md`
- Local memory: `E:\codex-home\tasks\20260417-uavm-pairuav-codabench\memory\handoff.md`

Key captured facts:

- Task is PairUAV heading/range prediction from image pairs.
- CodaBench accepts result submissions.
- `result.zip` must contain root-level `result.txt`.
- University-1652 test split and name-masked competition test set must not be used for training.

Workflow artifact:

- `L0_CONTRACT_SPEC_FILLED.md`

## 2. L0 Contract And Validation Anchor

L0 converted raw competition facts into a safety contract:

- rule risk: medium;
- metric direction: minimize;
- metric components: `final_score`, `distance_rel_error`, `angle_rel_error`;
- local metric status: reconstructed/proxy with known limitations;
- validation design: fixed PairUAV surfaces such as 4096/811 and val811, not default random split;
- submission contract: root-level `result.txt` inside `result.zip`.

Anchor evidence:

- Reloc3r official full-data one-epoch hidden submission:
  - `final_score = 0.003188`
  - `distance_rel_error = 0.002528`
  - `angle_rel_error = 0.003849`
  - `result.txt` rows: `2,773,116`
  - zip SHA256: `4869611B0C79E960B701576F507AF44998A2DDF28590A5709F1136418D6DE771`

Source memory:

- `E:\codex-home\tasks\20260417-uavm-pairuav-codabench\memory\reloc3r-official-training-eval-summary-v1.md`

## 3. L1 Paradigm Strong-Method Sweep

L1 grouped methods by paradigm instead of treating every route as the same kind of model tweak.

Workflow artifact:

- `L1_METHOD_POOL_SPEC_FILLED.md`

Paradigms represented:

- P1 match-field regression: SuperGlue, EfficientLoFTR, RoMa.
- P2 correspondence/covisibility-aware regression: SAC-Pose, CoMatch, FAR.
- P3 direct relative pose regression: Reloc3r official, Reloc3r variants.
- P5 explicit geometry solver: MADPose.
- P6 3D / geometry foundation model: MASt3R, DUSt3R, VGGT.

Key route roles:

- Reloc3r official: leaderboard mainline.
- RoMa / MASt3R / VGGT: source or mechanism evidence, not direct submissions.
- MADPose and frozen external head routes: held or rejected under current evidence.

Source memories:

- `method-candidate-pool-task-index-v1.md`
- `method-implementation-paradigm-summary-v1.md`

## 4. Route Scoreboard

The route scoreboard compressed multi-route state into a single decision surface.

Workflow artifact:

- `ROUTE_SCOREBOARD_FILLED.md`

Why it mattered:

- Hidden official results, local full-dev results, bounded probes, smoke tests, and diagnostics are not comparable without labels.
- A route can be a mainline, source, control, held route, or rejected route.
- Negative or held routes should not silently become submission candidates.

Example states:

- `reloc3r-official-full-epoch`: anchor.
- `roma-dense-field`: held/source.
- `mast3r-geometry-field`: held/source for angle evidence.
- `grelpose-frozen-head`: rejected, do not package or submit.

## 5. L2 Problem Definition

L2 did not start from a module idea. It first abstracted phenomena into a problem.

Workflow artifact:

- `L2_PROBLEM_DEFINITION_CARD_FILLED.md`

Selected problem statement:

```text
Under PairUAV cases where the direct RPR anchor already predicts distance well, current strong baselines fail to improve heading safely because the task requires angle-specific geometric evidence without disturbing distance predictions.
```

Why this is L2, not L3:

- The issue is not just thresholding, TTA, or fold search.
- The route must preserve distance while changing heading evidence flow.
- Hard/control slices are central to the claim.

## 6. L2 Innovation Card

The innovation card turned the problem into a falsifiable structural hypothesis.

Workflow artifact:

- `L2_INNOVATION_CARD_FILLED.md`

Mechanism claim:

```text
A selective heading-specific geometry branch can improve hard angle cases while preserving distance and base-sufficient controls.
```

Structural rewrite:

- separated geometry/correspondence branch;
- no direct global concat into final head;
- gated heading correction;
- base distance preserved by construction;
- no-op behavior on control slices.

Falsifiers:

- hard angle slice does not improve;
- control slice regresses;
- distance parity fails;
- gain depends on leaky features or mismatched surfaces.

## 7. Macro Route Decision

The macro decision selected strategy without generating a submission package.

Workflow artifact:

- `MACRO_ROUTE_DECISION_RECORD_FILLED.md`

Decision:

```text
keep_end_to_end_rank1_reloc3r_as_leaderboard_mainline
```

Route state:

- mainline: Reloc3r official family;
- protected output: rank1 full-epoch distance;
- next action: angle-improvement feasibility spec;
- hold: RoMa / MASt3R / VGGT as source or mechanism evidence;
- stop: full three-source fusion as direct submission path, cheap-student residual compression, red bounded routes.

Source memory:

- `phase42-macro-route-decision-results-v1.md`

## 8. Submission Intent Gate Negative Example

The workflow explicitly prevents packaging weak candidates.

Workflow artifact:

- `SUBMISSION_INTENT_RECORD_NEGATIVE_FILLED.md`

Example route:

- `phase48-grelpose-pairuav-head-smoke`

Evidence:

- best bounded head was much worse than the required Reloc3r10k anchor;
- likely feature/task mismatch;
- full official inference would waste compute and submission opportunity.

Intent verdict:

```text
do_not_package
```

Package verdict:

```text
cancelled
```

This is the concrete example of the rule: not worth submitting means no `result.zip` is generated.

## 9. Leaderboard Feedback Anchor

A strong official hidden result becomes an anchor only after artifact and feedback are recorded.

Workflow artifact:

- `LEADERBOARD_FEEDBACK_RECORD_FILLED.md`

Recorded feedback:

- `final_score = 0.003188`
- `distance_rel_error = 0.002528`
- `angle_rel_error = 0.003849`

Provenance:

- submitted artifact paths;
- checkpoint lineage;
- row count;
- zip hash;
- local validation caveat.

## 10. What This Trace Proves

This trace proves that the workflow can represent a real competition process with:

- rules and validation anchoring;
- strong-method paradigm sweep;
- route roles beyond direct submission;
- problem-driven structural innovation;
- strategic macro route decisions;
- negative submission intent gates;
- leaderboard feedback and anchor formation.

It does not prove that a fresh competition can be solved live during a short demo. The hackathon demo should present this trace as evidence of workflow maturity, then use a smaller cut-down example to show the mechanics interactively.

## 11. Demo Use

For a presentation, the clean story is:

```text
Raw competition -> L0 contract -> L1 method pool -> route scoreboard -> L2 problem/innovation -> macro route decision -> submission intent gate -> leaderboard feedback
```

The strongest visual/table artifacts are:

- route scoreboard;
- macro route decision;
- negative submission intent record;
- L2 problem definition + innovation card;
- leaderboard feedback anchor.
