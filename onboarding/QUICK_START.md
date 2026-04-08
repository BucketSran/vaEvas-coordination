# Quick Start

## 你如果是第一次加入，只做这 6 步

1. 先确认服务器上的实际仓库路径，或者确认应该从哪里 clone 到自己的目录
2. 读 [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/00_START_HERE.md)
3. 读 [AI_ONE_CLICK_TUNNEL_AND_LOOP_PROMPTS.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/AI_ONE_CLICK_TUNNEL_AND_LOOP_PROMPTS.md)
4. 让 AI 用这些文档给你解释“项目目标 + 你的任务”
5. 按 [ONBOARDING_CHECKLIST_TEAM.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/ONBOARDING_CHECKLIST_TEAM.md) 配好 Git 和本地环境
6. 按 [FIRST_TASK_EXAMPLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/FIRST_TASK_EXAMPLE.md) 跑通第一个小任务

如果你当前已经做到：

1. VNC 能连上跳板机
2. 能 `ssh -X` 到目标机
3. `source /home/cshrc/.cshrc.cadence.IC618SP201` 之后 `which spectre` 和 `which virtuoso` 正常

那你下一步最该做的事，不是继续盲猜命令，而是先问清楚这几个仓库在服务器上的实际路径：

1. `vaEvas`
2. `behavioral-veriloga-eval`
3. `sshConnect/virtuoso-bridge-lite`

可直接发这段：

```text
我现在已经成功做到这一步了：
1. VNC 能连上 thu-jin
2. 能 ssh -X 到 thu-wu
3. source /home/cshrc/.cshrc.cadence.IC618SP201 之后，which spectre 和 which virtuoso 都正常

现在我这边还没找到项目仓库目录，比如 vaEvas、behavioral-veriloga-eval、sshConnect/virtuoso-bridge-lite。
麻烦告诉我这些仓库在服务器上的实际路径，或者我应该从哪里 clone / 拷贝到自己的目录。
```

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
