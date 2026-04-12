# vaEvas Coordination

这是 `vaEvas` 项目的协作入口仓库。

这里不放产品代码，主要用来统一：

1. 项目目标
2. 仓库分工
3. 新人接入
4. AI 工作流
5. Git 协作规则
6. 周进度、风险和阶段同步

如果你是第一次接触这个项目，先记住一句话：

`这个仓库回答“我们在做什么、你今天该做什么、做完后怎么提交”。`

如果你进入项目后需要开始真正拆任务、记执行证据、写 brief/kpi/plan/log/review，请继续进入：

1. [worksche/README.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/README.md)

## 先看哪里

如果你只想最快开始，不要先把所有文档都读一遍。

按这个顺序看：

1. [00_STRUCTURE_GUIDE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/00_STRUCTURE_GUIDE.md)
2. [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/00_START_HERE.md)
3. [QUICK_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/QUICK_START.md)
4. [ONBOARDING_CHECKLIST_TEAM.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/ONBOARDING_CHECKLIST_TEAM.md)
5. [00_DOC_MAP.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/00_DOC_MAP.md)

如果你遇到“分工文档里有任务名，但自己本地仓库看不到”的情况，不要先猜自己拉错仓库。先看：

1. [2026-04-12_repo-visibility-note.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/status/2026-04-12_repo-visibility-note.md)
2. [REPOSITORIES.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/project/REPOSITORIES.md)

如果你只有 10 分钟，就先只看第 1 和第 2 个文件。

如果当前使用者是 `Bucketsran`：

1. 你默认是中间层负责人
2. 你主要关心分工、优先级、KPI、风险、同步口径
3. 每次同步本仓库时，优先看 [BUCKETSRAN_SYNC_PROFILE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/ops/BUCKETSRAN_SYNC_PROFILE.md)

## 你今天要做什么

新人第一轮任务可以压缩成 5 步：

1. 先确认服务器上的实际仓库路径，或者确认应该从哪里 clone
2. 读入口文档，知道项目和仓库分工
3. 认领一个 `example`
4. 按 `example -> closed loop -> benchmark seed` 跑一轮
5. 最后提一个 PR

一句话版交付定义：

`跑通一个 example，留下闭环验证证据，判断它能不能转 benchmark，并把结果通过 PR 提交。`

## 四个相关仓库分别做什么

`vaEvas` 相关工作通常分布在 4 个仓库：

1. `coordination`
   管协作、分工、入口文档、流程和同步节奏
2. `EVAS`
   管模拟器能力和语义实现
3. `behavioral-veriloga-eval`
   管 benchmark、runner、任务定义和评分
4. `veriloga-skills`
   管 Verilog-A 生成与审查的技能规则和参考资料

给新人最重要的理解是：

1. 大多数第一轮任务先从 `coordination` 开始接收
2. 大多数第一周工作会落在 `behavioral-veriloga-eval` 或 example 验证流程
3. 不要默认自己第一周就需要修改 `EVAS` 内核

## 这个仓库和代码仓库的关系

可以把整个项目理解成三层：

1. 代码仓库层
   `EVAS`、`behavioral-veriloga-eval`、`veriloga-skills`
2. 工作流层
   brief、kpi、plan、log、review 这类执行规范
3. 协作层
   也就是本仓库，负责把目标、节奏和任务入口说明白

所以本仓库的价值不是“多一个文档仓库”，而是让大家少走弯路。

## Git 协作怎么理解

代码仓库默认采用：

1. `origin`
   指向个人 fork
2. `upstream`
   指向团队主仓库

这意味着：

1. 日常开发先在个人 fork 上进行
2. 团队统一基线是 `upstream/main`
3. 正式改动通过 PR 合回主仓库

如果你需要更详细的 Git 规范，看：

1. [GIT_WORKFLOW.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/GIT_WORKFLOW.md)

## 如果你主要依赖 AI

推荐把 AI 当作“项目助教 + 执行助手”，而不是直接让它猜你的任务。

更稳的顺序是：

1. 先让 AI 读本仓库入口文档
2. 让 AI 总结当前项目目标和你负责的范围
3. 让 AI 帮你拆出今天的一轮任务
4. 最后再让 AI 帮你执行、验证和整理 PR

优先用这些入口：

1. [AI_PROMPT_STARTER.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/AI_PROMPT_STARTER.md)
2. [FIRST_TASK_EXAMPLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/FIRST_TASK_EXAMPLE.md)
3. [BUCKETSRAN_SYNC_PROFILE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/ops/BUCKETSRAN_SYNC_PROFILE.md)

## 推荐阅读路径

如果你希望按层次看文档，建议这样走：

1. [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/00_START_HERE.md)
2. [QUICK_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/QUICK_START.md)
3. [NEW_MEMBER_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/NEW_MEMBER_START.md)
4. [PROJECT_OVERVIEW.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/project/PROJECT_OVERVIEW.md)
5. [REPOSITORIES.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/project/REPOSITORIES.md)
6. [EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/benchmark/EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md)

## 每天开始前看什么

建议每天开始前先确认这三件事：

1. 当前优先级有没有变化
2. 你今天要动的是哪个仓库
3. 这轮任务的 `brief / kpi / plan` 是否齐全

## 目录说明

1. `docs/`
   项目概览、仓库说明、闭环规范、沟通材料
2. `onboarding/`
   新成员入口、操作手册、快速开始材料
3. `templates/`
   周报、状态更新、风险记录模板
4. `status/`
   阶段状态和周进度记录
5. `risks/`
   风险清单和处理记录

## 只拿到这个仓库怎么办

如果你当前只拿到了 `coordination`，先不要慌，先按这里走：

1. [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/00_START_HERE.md)
2. [ONBOARDING_CHECKLIST_TEAM.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/onboarding/ONBOARDING_CHECKLIST_TEAM.md)
3. [2026-04-12_repo-visibility-note.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/status/2026-04-12_repo-visibility-note.md)
4. [UPLOAD_PACK_NOTE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/ops/UPLOAD_PACK_NOTE.md)

这样你至少能先把项目入口、任务边界和第一轮交付搞清楚。
