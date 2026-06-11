# Start New Competition Checklist

Use this checklist when instantiating the workflow for a new Kaggle, CodaBench, or similar leaderboard competition.

## 0. Create Task Shell

- [ ] Choose `task_id`.
- [ ] Confirm project root, control-plane root, remote root, and knowledge sink.
- [ ] Create task directories:

```text
<competition-task>/
  task.md
  workflow/
  specs/
  plans/
  runs/
  scoreboards/
  decisions/
  submissions/
  memory/
  knowledge-candidates/
```

- [ ] Copy or link the workflow templates.
- [ ] Record success criteria and non-goals.

## 1. L0 Contract And Validation Anchor

Create `specs/L0_contract.md` from `templates/L0_CONTRACT_SPEC.md`.

Required before L1:

- [ ] Official task URL and task type recorded.
- [ ] Rules, external data, pretrained weights, team rules, and submission limits audited.
- [ ] Official metric and metric direction recorded.
- [ ] Local metric status marked as `exact`, `reconstructed`, `proxy`, or `unknown`.
- [ ] At least two split candidates considered if the task has structure.
- [ ] One active validation protocol selected.
- [ ] Official or simple baseline anchor recorded.
- [ ] Submission format and dry-run requirements captured.
- [ ] L0 verdict is `proceed_to_L1` or the blocker is explicit.

## 2. L1 Paradigm And Method Pool

Create `specs/L1_method_pool.md` from `templates/L1_METHOD_POOL_SPEC.md`.

Required before method adaptation:

- [ ] Define task interpretation.
- [ ] Build a paradigm taxonomy.
- [ ] Add candidate methods with source tiers.
- [ ] Score methods using the L1 scale.
- [ ] Select first-wave and second-wave methods.
- [ ] Create `scoreboards/route_scoreboard.md` from `templates/ROUTE_SCOREBOARD.md` if more than one serious route exists.
- [ ] For each selected non-trivial route, create a method adaptation spec.

A serious route is any route that can affect mainline, source/teacher policy, ensemble, or submission decisions.

## 3. L2 Structural Innovation

Start L2 only after there is a credible strongest baseline and observed bottlenecks.

Required sequence:

- [ ] Create a problem definition card.
- [ ] Pass Problem Gate or route the issue back to L0/L1/L3.
- [ ] Create an innovation card only after the problem card passes.
- [ ] Pass Card Gate before writing a structural spec.
- [ ] Define bounded falsification before any large training or leaderboard claim.

## 4. L3 Competition Engineering

Start L3 when there is a strong route or credible candidate.

Examples:

- folds, seeds, pseudo-labels, hard mining, curriculum;
- TTA, thresholds, calibration, routing;
- postprocessing, ensembling, stacking;
- packaging and compute optimization.

Every L3 change must update route scoreboard or a run record with provenance.

## 5. Submission

Before packaging:

- [ ] Create a submission intent record.
- [ ] Verify intent verdict is `package_for_submission`.
- [ ] If verdict is anything else, do not generate the package.

Before submitting:

- [ ] Run package gate checks.
- [ ] Record artifact path, command/script, config, checkpoint, and expected score/rank.
- [ ] Confirm rules risk is acceptable.

After submitting:

- [ ] Create a leaderboard feedback record.
- [ ] Update route scoreboard.
- [ ] Decide next action.

## 6. Closeout

Near final or competition closeout:

- [ ] Review scoreboards, decisions, and best artifacts.
- [ ] Promote durable knowledge candidates.
- [ ] Write handoff / final strategy summary.
- [ ] Record what should not be reopened without new evidence.
