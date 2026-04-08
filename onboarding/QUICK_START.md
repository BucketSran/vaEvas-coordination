# Quick Start

## 你如果是第一次加入，只做这 6 步

1. 先确认服务器上的实际仓库路径，或者确认应该从哪里 clone 到自己的目录
2. 读 [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/00_START_HERE.md)
3. 读 [AI_ONE_CLICK_TUNNEL_AND_LOOP_PROMPTS.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/AI_ONE_CLICK_TUNNEL_AND_LOOP_PROMPTS.md)
4. 让 AI 用这些文档给你解释“项目目标 + 你的任务”
5. 按 [ONBOARDING_CHECKLIST_TEAM.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/ONBOARDING_CHECKLIST_TEAM.md) 配好 Git 和本地环境
6. 按 [FIRST_TASK_EXAMPLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/FIRST_TASK_EXAMPLE.md) 跑通第一个小任务

如果 Cadence 环境已经通，但还没找到仓库路径：

1. 先看 [REPOSITORIES.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/project/REPOSITORIES.md)
2. 再看 [2026-04-08_onboarding-path-blocker.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/status/2026-04-08_onboarding-path-blocker.md)
3. 不要继续在 VNC / SSH / Cadence 上反复试错

## 先不要做什么

1. 不要直接改代码
2. 不要直接在 `main` 上开发
3. 不要还没看清任务边界就改 runner 或评分逻辑
4. 不要只让 AI 写代码，不让 AI 先解释任务

## 你现在最需要知道的三件事

1. 项目目标不是“写点 Verilog-A”，而是做一个可执行、可评分、可回归的系统。
2. 每个人平时维护的是自己的 fork，不是直接往主仓库写。
3. 每个正式任务都应按 `brief -> kpi -> plan -> execute -> log -> review` 的流程走。

## 你今天可以直接复制给 AI 的一句话

```text
请先阅读 vaEvas-coordination 里的文档，用新手能懂的话告诉我：这个项目在做什么、我今天应该先做什么、我不应该直接做什么。
```
