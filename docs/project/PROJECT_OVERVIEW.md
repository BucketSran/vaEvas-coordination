# Project Overview

## 项目一句话

`vaEvas` 的目标是建立一条从 Verilog-A 生成，到 EVAS 执行验证，再到 benchmark 评分和失败归因的完整闭环。

## 当前北极星

提升 Verilog-A agent 在 EVAS-compatible 纯电压域任务上的稳定生成与可执行评测能力。

## 当前范围

1. 仅覆盖纯电压域 Verilog-A 行为模型
2. 以 EVAS 为主验证引擎
3. 以 benchmark 的可执行结果为主要评估依据

## 当前三层结构

1. `EVAS`
   模拟器能力、示例、测试、文档
2. `behavioral-veriloga-eval`
   benchmark 任务、runner、schema、结果汇总
3. `veriloga-skills`
   Verilog-A 生成规则、技能沉淀、复用 prompt

## 当前关键指标

1. examples suite 通过率
2. benchmark 可执行率
3. deterministic `Pass@1`
4. 失败归因完整率
5. 回归不退化比例

## 进一步阅读

1. [EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md)
2. [TEAM_PLAN.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/TEAM_PLAN.md)
3. [AI_WORKFLOW_OPTIMIZATION.md](/Users/bucketsran/Documents/TsingProject/vaEvas/worksche/AI_WORKFLOW_OPTIMIZATION.md)
