# Competition Workflow Glossary

This glossary fixes the minimum shared vocabulary for the competition workflow. If a term is ambiguous in a task record, use the definitions here.

## Evidence Levels

- `smoke`: proves mechanics only. It can show code imports, data parses, checkpoint loads, one batch runs, or a submission file validates. It cannot claim metric improvement.
- `diagnostic`: investigates a signal or failure mode. It can guide decisions, but it is not deployable method evidence unless promoted by a bounded or full eval.
- `bounded`: tests a route on a fixed, limited, matched surface with a declared baseline, hard slice, control slice, and stop rule. It can support route-level decisions.
- `full_local`: evaluates a candidate on the strongest trusted local protocol available for the task.
- `public_lb`: score or rank from the public leaderboard. It must be timestamped.
- `hidden_official`: official hidden/private result. It is the strongest anchor if provenance is clean.

## Validation Status

- `trusted`: split, metric, artifacts, and submission contract are stable enough to compare routes and make submission decisions.
- `provisional`: useful for exploration, but not enough to claim final improvement or package a submission without extra checks.
- `blocked`: validation, metric, data, or submission contract is too uncertain to compare routes safely.

## Route Roles

- `mainline`: route currently used as the main leaderboard path.
- `source`: route used for features, teachers, diagnostics, or training policy, not directly submitted.
- `control`: route used to calibrate difficulty, cost, or comparison validity.
- `ensemble`: route intended to contribute to blending/stacking.
- `held`: useful evidence exists, but it is not active now.
- `rejected`: route should not continue without a new problem statement or spec.

## Slices

- `hard_slice`: samples or regimes where the current strong baseline fails and the route is expected to help.
- `control_slice`: samples or regimes that should not regress if the route is working safely.
- `affected_regime`: data regime targeted by a problem definition or innovation card.
- `base_sufficient`: cases where the current baseline is already good enough and interventions should usually no-op.

## Gates

- `Intent Gate`: decides whether a candidate deserves packaging work.
- `Package Gate`: validates the actual submission artifact after intent is `package_for_submission`.
- `Problem Gate`: decides whether raw phenomena define a real L2 problem.
- `Card Gate`: decides whether an L2 innovation card is ready for a structural spec.
- `Promotion Gate`: decides whether bounded evidence is strong enough for larger training, L3 engineering, or submission intent.

## Source Tiers

- `Tier 0`: official task materials, official baseline, metric code, leaderboard, organizer notes.
- `Tier 1`: reproducible paper/code/pretrained weights or locally reproduced route.
- `Tier 2`: top competition solution writeups or repos.
- `Tier 3`: nearby research directions without mature code or task-fit evidence.
- `Tier 4`: weak ideas, blogs, snippets, or unreproducible claims.

## Comparison Rules

- Do not compare `smoke` or `diagnostic` evidence against `full_local`, `public_lb`, or `hidden_official` as if they are equivalent.
- Do not claim real improvement from a proxy metric unless the metric reconstruction gate says it is strong enough for that claim.
- Every public or hidden leaderboard rank must include source and timestamp.
- Every score used for route decisions must be traceable to a run, config, seed/fold, command/script, artifact, or external source.
