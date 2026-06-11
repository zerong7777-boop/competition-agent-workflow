# Tabbit Demo Script

## Positioning

Tabbit is optional. The workflow does not depend on Tabbit, but Tabbit can be used as the live context surface:

```text
@rank screenshots + @workflow docs + @evidence trace -> ask the Competition Workflow Skill to produce route decision and submission gate output
```

This makes the demo fit the event theme without pretending the workflow only works in Tabbit.

## Files To Open Or Attach

Recommended files:

- `E:\rz\research\tabbit_hackthon\rank1.jpg`
- `E:\rz\research\tabbit_hackthon\rank2.png`
- `E:\rz\research\tabbit_hackthon\demo\UAVM_EVIDENCE_TRACE.md`
- `E:\rz\research\tabbit_hackthon\demo\COMPACT_ROUTE_SCOREBOARD.md`
- `E:\rz\research\tabbit_hackthon\demo\NEGATIVE_SUBMISSION_GATE.md`
- `E:\rz\research\tabbit_hackthon\workflow\GLOSSARY.md`

If Tabbit can access local files directly, use file context. If not, paste the relevant markdown sections or open them as browser/file tabs.

## Demo Prompt 1: Summarize The Workflow

```text
你现在是 Competition Leaderboard Workflow Skill。
请读取这些材料，输出一个 60 秒介绍：
1. 这个 workflow 解决什么问题；
2. L0/L1/L2/L3 分别做什么；
3. 为什么 submission gate 很重要；
4. 这个 UAVM 案例提供了什么证据。
要求：面向黑客松评委，简洁、有冲击力，不要编造实时榜单状态。
```

Expected output should mention:

- rules/validation first;
- paradigm method pool;
- problem-driven structural innovation;
- route scoreboard;
- `do_not_package` negative gate;
- historical rank-1 and later rank-7 screenshot evidence.

## Demo Prompt 2: Route Decision

```text
根据 COMPACT_ROUTE_SCOREBOARD 和 UAVM_EVIDENCE_TRACE，给出当前路线决策：
- 哪条是 mainline；
- 哪些是 source/control；
- 哪些 hold/reject；
- 下一步应该做什么；
- 哪些不应该生成 submission package。
请用表格输出。
```

Expected output:

- Reloc3r official = mainline / anchor.
- RoMa, MASt3R, VGGT = source/control.
- GRelPose frozen head = reject / do_not_package.
- Next step = L2/L3 gated angle improvement, not blind package generation.

## Demo Prompt 3: Negative Submission Gate

```text
根据 NEGATIVE_SUBMISSION_GATE，解释为什么 phase48-grelpose-pairuav-head-smoke 不应该生成 result.zip。
请输出：
1. evidence;
2. intent verdict;
3. package verdict;
4. 这体现了 workflow 的什么价值。
```

Expected output:

```text
intent verdict = do_not_package
package verdict = cancelled
```

## Demo Prompt 4: Create A New Competition Starter Plan

```text
假设我现在打开一个新的 Kaggle/CodaBench 比赛，请按这个 workflow 输出启动清单：
1. L0 要先读什么；
2. L1 如何做方法池；
3. 什么时候开始 L2；
4. 什么时候允许生成提交包。
```

Expected output should follow `START_NEW_COMPETITION_CHECKLIST.md`.

## Live Demo Flow

1. Show rank screenshots first.
2. Show one-page workflow map.
3. Ask Tabbit Demo Prompt 2.
4. Ask Tabbit Demo Prompt 3.
5. Close with the line:

```text
这个工作流不是让 AI 替我冲动提交，而是让 AI 帮我维护一套可验证、可追溯、可停止的冲榜决策系统。
```

## Fallback If Tabbit Fails

Use local markdown files directly:

- show `ONE_PAGE_WORKFLOW.md`;
- show `COMPACT_ROUTE_SCOREBOARD.md`;
- show `NEGATIVE_SUBMISSION_GATE.md`;
- read the 30-second opening from `DEMO_NARRATIVE.md`.

The demo should not depend on live internet or live leaderboard refresh.
