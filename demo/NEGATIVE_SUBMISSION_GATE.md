# Negative Submission Gate

## Demo Point

The workflow is valuable not only because it finds routes to submit, but because it prevents bad submissions.

## Example Route

Route:

```text
phase48-grelpose-pairuav-head-smoke
```

Evidence:

```text
best bounded head angle ~= 43.8259
best bounded proxy ~= 0.2472
required Reloc3r10k anchor angle ~= 8.6087
required Reloc3r10k proxy ~= 0.0516
```

Interpretation:

- The bounded result is clearly red.
- The route likely has feature/task mismatch.
- Full official inference would waste compute.
- A submission package would not be justified.

## Workflow Decision

```text
Submission Intent: do_not_package
Package Verdict: cancelled
```

## Presentation Line

```text
很多 AI 工具会帮你生成结果包，但真正专业的竞赛 workflow 必须知道什么时候不该生成结果包。
```

## Why Judges Should Care

- Submission opportunities are limited.
- Bad submissions pollute route judgment.
- Leaderboard feedback can create false confidence.
- A mature workflow must enforce stop conditions, not only action generation.
