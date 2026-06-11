# Competition Agent Harness Workflow v0.1.1

## 1. Purpose

This workflow is a competition-specific, copy-on-write specialization of the local Agent Harness workflow. It is designed for expert users who want fast, evidence-backed decisions in leaderboard competitions such as Codabench or Kaggle.

This is a staged Agent Harness protocol. The agent advances by producing specs, plans, records, scoreboards, and decision artifacts; the user advances the work through explicit task requests and review.

## 2. Upstream Reuse Policy

Local Agent Harness files under `E:\codex-home` are read-only references. This project copies concepts and creates competition-specific templates under `E:\rz\research\tabbit_hackthon`.

Reused concepts:

- long-task intake: task id, roots, success criteria, constraints, knowledge sink;
- control-plane style: total spec, child specs, state, records, memory;
- classic loop: research, spec, implementation plan, execution, experiment record, decision, submission, iteration;
- durable records: task-local memory, knowledge candidates, handoff notes.

Specialized concepts:

- L0 rules and validation anchoring;
- L1 paradigm-level strong-method adaptation sweep;
- L2 problem-driven structural innovation;
- L3 competition engineering optimization;
- submission intent gate before package generation;
- leaderboard feedback loop.

## 3. Read First

Before instantiating a new competition task, read:

- `GLOSSARY.md`
- `START_NEW_COMPETITION_CHECKLIST.md`

These two files define the minimum vocabulary, evidence levels, gate meanings, and startup order.
## 4. Stage Overview

```text
L0 Contract & Validation Anchor
-> L1 Paradigm Strong-Method Adaptation Sweep
-> L2 Problem-Driven Structural Innovation
-> L3 Competition Engineering Optimization
-> Submission Intent Gate
-> Submission Package Gate
-> Leaderboard Feedback Loop
-> Knowledge Review / Closeout
```

## 5. L0 Contract & Validation Anchor

L0 establishes whether the competition can be evaluated and submitted safely.

Required outputs:

- competition contract spec;
- rules risk summary and full audit notes;
- official baseline anchor;
- local validation protocol;
- metric reconstruction or proxy protocol;
- submission contract;
- initial task scoreboard schema.

Key rules:

- Local split design must be task-structure-driven, not default random.
- Proxy metrics may support early exploration, but they cannot justify formal improvement claims until metric reconstruction is strong enough.
- If validation, metric, or submission contract is not trusted, later stages must mark results as provisional.

Primary template:

- `templates/L0_CONTRACT_SPEC.md`

## 6. L1 Paradigm Strong-Method Adaptation Sweep

L1 aims to get strong scores quickly by adapting mature methods from each relevant paradigm.

Required outputs:

- paradigm taxonomy;
- method pool macro spec;
- method ranking by expected ceiling, task fit, pretrained weights, code maturity, adaptation cost, compute, rule risk, validation clarity, and ensemble value;
- one method adaptation spec per selected route;
- L1 scoreboard with local validation results, artifacts, and provenance fields.

Source tiers:

- Tier 0: official task materials, baseline, metric, leaderboard;
- Tier 1: reproducible paper/code/pretrained weights;
- Tier 2: top competition solutions;
- Tier 3: nearby research directions without mature code;
- Tier 4: weak ideas, blogs, unreproducible snippets.

Key rules:

- L1 starts with taxonomy, not a single favorite model.
- The macro spec decides method order.
- Each non-trivial adaptation requires its own spec and implementation plan.
- Early parallel work should be read-only audits; formal adaptation is limited to the selected top routes.

Primary templates:

- `templates/L1_METHOD_POOL_SPEC.md`
- `templates/L1_METHOD_ADAPTATION_SPEC.md`

## 7. L2 Problem-Driven Structural Innovation

L2 starts only after L1 provides a credible strongest baseline and observed bottlenecks. It handles structural innovation, not ordinary training or inference tricks.

Core chain:

```text
phenomenon -> problem definition -> bottleneck -> mechanism -> structural rewrite -> bounded falsification
```

Required outputs:

- problem definition card;
- bottleneck, mechanism, and structure ledgers;
- innovation card;
- card gate verdict;
- structural spec only after card acceptance;
- bounded falsification plan and record.

Hard rules:

- L2 cannot jump from phenomenon to module idea.
- L2 cannot write an innovation card before a problem definition card.
- L2 cannot write a structural spec before an accepted innovation card.
- A structure is not mature if it is only direct concatenation, scalar weighting, arbitrary loss stacking, or adapter-as-explanation.
- Bounded falsification comes before large training or leaderboard claims.

Problem statement format:

```text
Under <data regime / task condition>, current strong baselines fail to <desired behavior>, because the task requires <missing capability / unresolved constraint>.
```

Primary templates:

- `templates/L2_PROBLEM_DEFINITION_CARD.md`
- `templates/L2_INNOVATION_CARD.md`

## 8. L3 Competition Engineering Optimization

L3 extracts performance from the strongest routes after L1 and L2 have produced credible candidates.

Scope:

- training strategy: folds, pseudo-labels, hard mining, curriculum, multi-stage fine-tuning;
- inference strategy: TTA, sliding window, threshold search, calibration, routing;
- postprocessing: connected components, rule-based corrections, smoothing;
- ensemble: blending, stacking, diversity selection;
- compute and submission engineering.

Key rules:

- L3 should operate on a strong route, not compensate for a weak L1 baseline.
- L3 changes must be tracked against validation protocol and submission risk.
- If an engineering trick changes the task definition, uses leaked data, or violates rules, it must be rejected.

Primary template:

- `templates/L3_ENGINEERING_SPEC.md`

## 9. Route Scoreboard And Macro Decisions

The workflow needs a compact cross-stage decision surface. L1, L2, and L3 can all produce useful evidence, but not every route is a submission candidate or mainline method.

Required artifacts when more than one serious route exists:

- route scoreboard;
- macro route decision record.

Key rules:

- A route must declare its role: mainline, source/teacher, control, ensemble member, held route, or rejected route.
- Hidden official scores, public leaderboard scores, local full evals, bounded evals, smoke tests, and diagnostics must be labeled separately.
- A macro route decision can choose to continue, hold, stop, or protect a route without generating a submission package.
- Every score used for a route decision must include provenance or be marked provisional.

Primary templates:

- `templates/ROUTE_SCOREBOARD.md`
- `templates/MACRO_ROUTE_DECISION_RECORD.md`
## 10. Submission Gates

The workflow separates submission intent from submission package generation.

Intent gate outputs:

- `do_not_package`
- `need_more_validation`
- `hold_for_final_merge`
- `package_for_submission`

Only `package_for_submission` permits building a submission artifact.

Package gate checks:

- artifact exists and matches submission format;
- local validation and provenance are recorded, including run id, config, seed/fold, command/script, and artifact paths;
- rules risk is acceptable;
- score/rank expectation is stated;
- rollback or next action is clear.

Primary template:

- `templates/SUBMISSION_INTENT_RECORD.md`

## 11. Leaderboard Feedback Loop

Every real submission must produce a concise feedback record.

Minimum fields:

- submission name or id;
- artifact path;
- timestamp;
- public score and rank if available;
- delta vs previous submission and anchor;
- linked route and local validation summary;
- immediate verdict;
- next action.

Public/private overfitting analysis is required only when the result is abnormal, high-stakes, or near final selection.

Primary template:

- `templates/LEADERBOARD_FEEDBACK_RECORD.md`

## 12. Knowledge Review / Closeout

During active competition work, lightweight records are enough. Near final or closeout, review which findings should become durable knowledge.

Possible knowledge candidates:

- reusable validation design;
- task-specific data insights;
- successful adaptation patterns;
- rejected mechanisms with evidence;
- competition engineering patterns;
- final strategy rationale.

Knowledge review is not required after every iteration.

## 13. Recommended Directory Shape For An Instantiated Competition Task

```text
<competition-task>/
  task.md
  workflow/
  specs/
    L0_contract.md
    L1_method_pool.md
    L1_methods/
    L2_problem_cards/
    L2_innovation_cards/
    L3_engineering/
  plans/
  runs/
  scoreboards/
  decisions/
  submissions/
  memory/
  knowledge-candidates/
```

## 14. v0.1.1 Open Points

- The later hackathon demo version should be a cut-down derived from this mature workflow.
- A concrete competition instance, such as UAVM, can be used to test whether the templates are discoverable and usable.
- Further card/gate scoring can be added after more real instantiations expose which checks are still too vague.





