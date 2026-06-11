# Slide Outline

## Slide 1. 标题

标题：竞赛冲榜 Agent Workflow

副标题：从“问 AI 一个方法”到“维护可复用的 leaderboard decision system”

要点：

- 面向 Kaggle / CodaBench / AI 竞赛
- 目标：高手快速决策冲榜
- 基于本地 Agent Harness 的比赛特化版本

## Slide 2. 痛点

标题：普通 AI 冲榜为什么容易失控

要点：

- 本地验证不可信，榜单反馈被误读
- 方法之间不可比，smoke / bounded / full eval 混在一起
- 看到一个新方法就跑，缺少范式视角
- 不值得交的结果也会被打包提交
- 调参记录和决策依据不可追溯

## Slide 3. 总流程

标题：我们的流程

图：

```text
L0 规则与验证锚定
-> L1 强范式扫榜
-> L2 问题驱动结构创新
-> L3 竞赛工程优化
-> Submission Gate
-> Leaderboard Feedback
```

一句话：先建立可信评价，再做方法池，再做结构创新，最后才冲提交。

## Slide 4. 核心控件

标题：不是 prompt，是决策系统

展示 3 个控件：

- Route Scoreboard：mainline / source / control / hold / reject
- Innovation Card：phenomenon -> problem -> bottleneck -> mechanism
- Submission Intent Gate：`do_not_package` / `package_for_submission`

## Slide 5. 真实案例：PairUAV CodaBench

标题：真实竞赛证据

展示：

- `rank1.jpg`：2026-05-09，`ze_rong` 第 1，`final_score=0.003188`
- `rank2.png`：后续截图，`ze_rong` 第 7，`final_score=0.003078`

口径：截图证明这个 workflow 背后有真实冲榜经验，但不声明现场实时排名。

## Slide 6. 多路线决策

标题：为什么需要 Route Scoreboard

展示 compact route table：

- Reloc3r official：mainline / hidden official anchor
- RoMa / MASt3R / VGGT：source / mechanism evidence
- GRelPose frozen head：reject / do_not_package

一句话：不是所有有结果的路线都值得提交。

## Slide 7. 负例最能说明专业性

标题：不值得交，就不生成提交包

展示：

```text
GRelPose bounded smoke red
-> Submission Intent: do_not_package
-> Package Verdict: cancelled
```

要点：

- 保护提交机会
- 防止无效实验污染判断
- 让 agent 遵守 workflow，而不是自己冲动打包

## Slide 8. Tabbit 演示

标题：Tabbit 可以作为上下文和 Skill 入口

现场操作：

- @rank1.jpg
- @rank2.png
- @END_TO_END_TRACE.md
- @COMPACT_ROUTE_SCOREBOARD.md
- 让 Tabbit 输出：当前路线决策和是否应该打包提交

口径：不强依赖 Tabbit，但可以在 Tabbit 中作为可复用 Skill 运行。

## Slide 9. 价值

标题：为什么这个能拿第一

要点：

- 结果可验证：真实榜单截图
- 流程可复用：L0-L3 + gate + feedback
- 决策可追溯：scoreboard + provenance
- 专业性强：知道什么时候不提交
- 可迁移：Kaggle、CodaBench、科研 benchmark 都能用

## Slide 10. 结尾

标题：AI 工具真正有价值的地方

结尾句：

AI 不是替我随便想一个方法，而是帮我把复杂竞赛变成可复用、可追溯、可决策的工作流。
