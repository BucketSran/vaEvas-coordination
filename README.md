# vaEvas Coordination

这是 `vaEvas` 项目的顶层协作仓库，用来统一管理：

1. 项目目标
2. 组织分工
3. AI 工作流
4. Git 协作规则
5. 新成员接入
6. 周进度、风险、阶段汇报

这个仓库不承载产品代码。

产品代码仍在以下三个独立仓库中：

1. `EVAS`
2. `behavioral-veriloga-eval`
3. `veriloga-skills`

---

## 仓库定位

如果把整个项目拆成三层：

1. 代码仓库层
   负责实现、验证、benchmark、skills
2. 工作流层
   负责任务模板、执行闭环、日志和 review
3. 顶层协作层
   负责目标统一、进度同步、分工管理、对上汇报

本仓库就是第 3 层，也就是顶层协作层。

---

## Git 协作原则

`vaEvas` 的代码仓库默认采用：

1. `origin`
   指向个人 fork
2. `upstream`
   指向团队主仓库

这意味着：

1. 每个人日常维护的是自己的 fork，而不是直接在主仓库上开发。
2. 团队统一基线是 `upstream/main`。
3. 所有正式改动先进入个人 fork，再通过 PR 合回主仓库。

这样做的目的不是增加流程，而是保护主线稳定，支持多人并行开发，并让 review、回滚和质量控制更容易执行。

具体操作规范见：

1. [GIT_WORKFLOW.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/GIT_WORKFLOW.md)

---

## 第一次进入先看什么

如果你是第一次接触这个项目，而且很多操作会依赖 AI，建议不要直接跳进所有文档。

先按这个顺序：

1. [onboarding/QUICK_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/QUICK_START.md)
   先看 5 分钟启动版，知道第一天到底做什么。
2. [onboarding/AI_PROMPT_STARTER.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/AI_PROMPT_STARTER.md)
   直接复制 prompt 给 AI，减少自己理解成本。
3. [onboarding/VIRTUOSO_EVAS_TEAM_GUIDE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/VIRTUOSO_EVAS_TEAM_GUIDE.md)
   新成员 Virtuoso 连接、最小概念和双验证执行手册。
4. [onboarding/NEW_MEMBER_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/NEW_MEMBER_START.md)
   看完整的新成员接入路径。
5. [docs/PROJECT_OVERVIEW.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/PROJECT_OVERVIEW.md)
6. [docs/REPOSITORIES.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/REPOSITORIES.md)
7. [docs/DAILY_SYNC.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/DAILY_SYNC.md)
8. [docs/COMMUNICATION_PACK.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/COMMUNICATION_PACK.md)

## 如果你主要依赖 AI

建议把 AI 当成“项目助教 + 执行助手”，不要让它替你猜项目目标。

正确做法是：

1. 先让 AI 读 `coordination` 和 `worksche` 文档
2. 再让 AI 告诉你当前项目在做什么
3. 再让 AI 帮你确认今天该接什么任务
4. 最后才让 AI 帮你执行具体操作

优先使用：

1. [onboarding/AI_PROMPT_STARTER.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/AI_PROMPT_STARTER.md)
2. [onboarding/FIRST_TASK_EXAMPLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/FIRST_TASK_EXAMPLE.md)

---

## 和 `vaEvas/worksche` 的关系

`vaEvas/worksche/` 里放的是项目内执行文档：

1. [TEAM_PLAN.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/TEAM_PLAN.md)
2. [AI_WORKFLOW_OPTIMIZATION.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/AI_WORKFLOW_OPTIMIZATION.md)
3. [GIT_WORKFLOW.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/GIT_WORKFLOW.md)
4. [ONBOARDING_CHECKLIST.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/ONBOARDING_CHECKLIST.md)

这里的关系是：

1. `vaEvas-coordination`
   管顶层协作、汇报、同步节奏
2. `vaEvas/worksche`
   管团队执行、任务模板、交付规范

---

## 推荐每天第一件事

1. 先同步本仓库，确认目标、优先级、周状态和风险是否更新。
2. 再同步当天涉及的代码仓库 `upstream/main`。
3. 开始当天任务前，确认对应的 `brief/kpi/plan` 是否齐全。

---

## 目录说明

1. `docs/`
   项目概览、仓库说明、同步节奏、沟通材料。
2. `templates/`
   周报、状态更新、风险记录模板。
3. `status/`
   阶段状态、周进度、临时同步记录。
4. `risks/`
   风险清单和处理记录。
5. `onboarding/`
   新成员接入材料。

## 仅上传 coordination 时

如果你只上传本仓库，请先阅读：

1. [docs/UPLOAD_PACK_NOTE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/UPLOAD_PACK_NOTE.md)
