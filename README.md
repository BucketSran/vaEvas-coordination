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

## 第一次进入先看什么

按这个顺序：

1. [docs/PROJECT_OVERVIEW.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/PROJECT_OVERVIEW.md)
2. [docs/REPOSITORIES.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/REPOSITORIES.md)
3. [docs/DAILY_SYNC.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/DAILY_SYNC.md)
4. [docs/COMMUNICATION_PACK.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/COMMUNICATION_PACK.md)
5. [onboarding/NEW_MEMBER_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/NEW_MEMBER_START.md)

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
