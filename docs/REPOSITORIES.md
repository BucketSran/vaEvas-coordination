# Repositories

## 协作原则

所有代码仓库统一采用：

1. `origin = 个人 fork`
2. `upstream = 团队主仓库`

默认工作方式是：

1. 从 `upstream/main` 同步最新公共基线
2. 在本地基于最新基线开任务分支
3. 推送到自己的 `origin/<branch>`
4. 通过 PR 合回 `upstream/main`

所以从协作角度看：

1. 每个人维护的是自己的 fork
2. 团队共享的是主仓库基线
3. 中间层负责人主要复核进入主仓库的改动，而不是替每个人直接维护他们的开发分支

---

## 代码仓库

### 1. EVAS

路径：

1. [EVAS](/Users/bucketsran/Documents/TsingProject/vaEvas/EVAS)

用途：

1. 模拟器能力
2. 示例与测试
3. 文档

### 2. behavioral-veriloga-eval

路径：

1. [behavioral-veriloga-eval](/Users/bucketsran/Documents/TsingProject/vaEvas/behavioral-veriloga-eval)

用途：

1. benchmark 任务
2. runner
3. 评分与结果汇总

### 3. veriloga-skills

路径：

1. [veriloga-skills](/Users/bucketsran/Documents/TsingProject/vaEvas/veriloga-skills)

用途：

1. Verilog-A 生成规则
2. EVAS/OpenVAF 验证技能
3. prompt 与技能沉淀

## 顶层协作仓库

路径：

1. [vaEvas-coordination](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination)

用途：

1. 统一项目目标
2. 统一分工与协作规则
3. 统一进度同步与对上汇报

## 工作流文档所在位置

路径：

1. [worksche](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche)

重点文档：

1. [TEAM_PLAN.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/TEAM_PLAN.md)
2. [AI_WORKFLOW_OPTIMIZATION.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/AI_WORKFLOW_OPTIMIZATION.md)
3. [GIT_WORKFLOW.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/GIT_WORKFLOW.md)
4. [ONBOARDING_CHECKLIST.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/ONBOARDING_CHECKLIST.md)
