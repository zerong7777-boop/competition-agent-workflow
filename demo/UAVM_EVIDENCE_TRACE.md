# UAVM Evidence Trace

This is the short demo version of the longer trace in `workflow/examples/uavm-smoke-test/END_TO_END_TRACE.md`.

## Evidence Images

| file | what it shows | safe presentation wording |
| --- | --- | --- |
| `../rank1.jpg` | `ze_rong` ranked #1 on 2026-05-09 11:57, `final_score=0.003188`, `distance_rel_error=0.002528`, `angle_rel_error=0.003849` | “这个账号曾经在 PairUAV CodaBench 榜单上拿到第 1。” |
| `../rank2.png` | later screenshot shows `ze_rong` at #7, `final_score=0.003078`, `distance_rel_error=0.002412`, `angle_rel_error=0.003744` | “后续榜单竞争继续变化，截图里显示同一账号位于第 7。” |

Do not say this is the live leaderboard on the presentation day unless it is refreshed that day.

## Why This Is A Good Demo Case

- It is a real CodaBench-style leaderboard competition.
- The score is objective and easy for judges to understand.
- There is a real historical rank-1 screenshot.
- The workflow records not only successful submissions, but also held and rejected routes.
- It demonstrates expert decision making, not just prompt generation.

## Workflow Trace

```text
Raw PairUAV competition
-> L0 contract: metric / validation / submission format
-> L1 method pool: Reloc3r, RoMa, MASt3R, VGGT, MADPose, SAC-Pose, GRelPose
-> Route scoreboard: mainline / source / control / hold / reject
-> L2 problem: improve heading without destroying distance
-> Innovation card: selective heading-specific geometry reasoning
-> Macro route decision: protect Reloc3r official mainline
-> Submission gate: weak GRelPose route = do_not_package
-> Leaderboard feedback: hidden official anchor recorded
```

## Key Numbers For Slide

Historical rank-1 anchor from screenshot/local record:

```text
participant = ze_rong
rank = 1
submission date = 2026-05-09 11:57
final_score = 0.003188
distance_rel_error = 0.002528
angle_rel_error = 0.003849
```

Later screenshot:

```text
participant = ze_rong
rank shown = 7
row date = 2026-05-28 01:00
final_score = 0.003078
distance_rel_error = 0.002412
angle_rel_error = 0.003744
```

## Demo Message

The point is not “the rank never changes.” The point is that a real leaderboard case can be managed with a workflow that separates evidence levels, route roles, structural innovation, and submission gating.
