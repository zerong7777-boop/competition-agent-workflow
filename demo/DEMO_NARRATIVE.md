# Demo Narrative

## 一句话版本

这是一个面向 Kaggle / CodaBench 这类竞赛冲榜的 Agent Harness 工作流：它不是让 AI 随便想一个模型去跑，而是把竞赛拆成规则锚定、强范式扫榜、问题驱动结构创新、工程优化、提交门控和榜单反馈的可复用流程。

## 30 秒开场

普通的 AI 工作流经常是：看到比赛，问模型有什么方法，改代码，跑实验，然后试着提交。

这个方式的问题是很明显的：本地验证不一定可信，方法之间不可比，弱实验容易被包装成强结论，不值得提交的结果也会浪费提交机会。

我的工作流反过来做：先建立可信评价和提交契约，再按成熟范式系统扫方法池，遇到瓶颈后才进入结构创新，最后用工程优化和 submission gate 决定是否真的生成提交包。

## 3-5 分钟讲稿

我这次做的是一个竞赛冲榜工作流，目标用户不是完全不会编程的人，而是已经有一定技术能力、想快速做出正确路线决策的人。

这个工作流基于我本地长期使用的 Agent Harness。核心不是一个 prompt，而是一套可复用的流程约束和文档协议。Agent 不是直接帮我幻想答案，而是按阶段产出 spec、plan、scoreboard、decision record 和 submission record。

第一步是 L0，Contract and Validation Anchor。比赛一开始先不跑模型，而是确认规则、数据、指标、本地验证集、官方 baseline、提交格式。这个阶段的目标是回答一个问题：我能不能安全、可信地比较方法和提交结果。

第二步是 L1，Paradigm Strong-Method Adaptation Sweep。这里不直接押一个模型，而是先做任务范式分类，再从每个成熟范式里挑 1-2 个最强方法做本地适配。比如在 PairUAV 这个 CodaBench 比赛里，我把路线分成 match-field regression、direct relative pose regression、geometry foundation model、explicit geometry solver 等不同范式。这样做的价值是防止一直在同一个局部方法里打转。

第三步是 L2，Problem-Driven Structural Innovation。只有当 L1 已经有强 baseline 并且出现瓶颈，才进入结构创新。这个阶段不能直接说“加 attention”或者“加一个 loss”。必须先把现象抽象成问题，再写 bottleneck、mechanism、innovation card，最后才允许写 structural spec。这里的思路更接近科研方法：从真实瓶颈出发，设计可证伪的结构变化。

第四步是 L3，Competition Engineering Optimization。这里才做 folds、pseudo-label、TTA、threshold、postprocess、ensemble 这些竞赛工程手段。L3 的前提是已经有强路线，不是用工程 trick 去掩盖弱 baseline。

中间最关键的两个控件是 Route Scoreboard 和 Submission Gate。Route Scoreboard 会把路线分成 mainline、source、control、held、rejected，并标清楚每个分数来自 hidden official、public leaderboard、full local、bounded、smoke 还是 diagnostic。这样我不会把一个 smoke test 当成正式结果。

Submission Gate 则保证只有真正值得交的候选才会生成提交包。如果 intent 不是 `package_for_submission`，就不会生成 `result.zip`。这点在竞赛里很重要，因为一次错误提交不仅浪费机会，还会污染后续判断。

我用一个真实案例做验证：PairUAV CodaBench 比赛。我曾经在 2026-05-09 的截图里拿到第 1，`final_score=0.003188`。后来的截图显示同一账号 `ze_rong` 在第 7，`final_score=0.003078`。这个案例里最有说服力的不是单个分数，而是整个决策链：有强 baseline，有多范式方法池，有 route scoreboard，有 L2 结构创新卡，也有明确的负例，某条 GRelPose 路线 bounded 结果很差，所以工作流给出 `do_not_package`，不生成提交包。

所以这个工作流的价值是：它让 AI 从“会建议方法”变成“能维护竞赛决策系统”。对于论文、实习求职、考研这些任务，AI 工作流当然也有用；但竞赛冲榜的好处是结果非常直观，榜单和分数就是证据。

## 收束句

我最后想强调的是，这不是为了展示一个漂亮页面，而是展示一种可以复用的 AI 工作方式：先建立可信评价，再系统探索方法，再围绕瓶颈创新，最后用提交门控和榜单反馈闭环。这套流程能在 Tabbit 这样的上下文型 AI 工具里运行，也可以迁移到任何 agent 工具中。
