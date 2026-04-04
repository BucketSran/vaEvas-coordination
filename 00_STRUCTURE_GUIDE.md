# 00 Structure Guide

这份文件只做一件事：

`告诉你 vaEvas-coordination 里每个目录是干什么的，以及你现在应该先看哪里。`

如果你第一次打开这个仓库，建议先看这份，再决定要不要继续点进 `docs/` 或 `onboarding/`。

---

## 1. 仓库总结构

`vaEvas-coordination` 现在可以按用途分成 6 块：

1. `README.md`
   仓库首页，解释这个仓库为什么存在，以及新人第一步该做什么。
2. `00_STRUCTURE_GUIDE.md`
   就是这份文件。用来解释目录结构。
3. `onboarding/`
   新人接入和第一周执行入口。
4. `docs/`
   项目规范、benchmark 流程、论文草稿、结果表。
5. `referencepaper/`
   外部参考论文 PDF 和索引。
6. `templates/` / `status/` / `risks/`
   模板、状态记录、风险记录。

---

## 2. 最重要的两个目录

### `onboarding/`

这个目录回答：

`新人现在该怎么开始。`

适合在这些场景下打开：

1. 新同学第一次进项目
2. 要配环境、看接入步骤
3. 要知道第一周交什么
4. 要用 AI 帮忙但不知道该先喂什么文档

这里最重要的文件是：

1. [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/00_START_HERE.md)
   新人唯一入口
2. [QUICK_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/QUICK_START.md)
   最短执行路径
3. [NEW_MEMBER_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/NEW_MEMBER_START.md)
   第一周做什么
4. [ONBOARDING_CHECKLIST_TEAM.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/ONBOARDING_CHECKLIST_TEAM.md)
   环境和接入清单
5. [VIRTUOSO_EVAS_TEAM_GUIDE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/VIRTUOSO_EVAS_TEAM_GUIDE.md)
   EVAS + Virtuoso 团队执行手册

### `docs/`

这个目录回答：

`团队现在采用什么流程、怎么做 benchmark、论文怎么组织、结果表填哪里。`

适合在这些场景下打开：

1. 要把 example 转 benchmark
2. 要理解 EVAS-first 闭环
3. 要维护结果表
4. 要整理 paper draft

---

## 3. docs 目录怎么读

`docs/` 里的内容已经比较多了，建议按功能理解，不要把它当一串平铺文件名。

### A. 项目总览类

先建立全局认知时看：

1. [PROJECT_OVERVIEW.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/project/PROJECT_OVERVIEW.md)
2. [REPOSITORIES.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/project/REPOSITORIES.md)
3. [WORK_ASSIGNMENT.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/project/WORK_ASSIGNMENT.md)
4. [00_DOC_MAP.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/00_DOC_MAP.md)

### B. Benchmark 工作流类

要把 example 变成 benchmark 时看：

1. [EXAMPLE_TO_BENCHMARK_WORKFLOW.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/EXAMPLE_TO_BENCHMARK_WORKFLOW.md)
2. [EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/EVAS_VIRTUOSO_CLOSED_LOOP_BENCHMARK.md)
3. [META_JSON_MIN_TEMPLATE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/META_JSON_MIN_TEMPLATE.md)

### C. 结果表类

要填实验结果时看：

1. [BENCHMARK_RESULT_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/BENCHMARK_RESULT_TABLE.md)
   记录 task / case 本身的 benchmark 建设状态
2. [AI_MODEL_EVAL_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/AI_MODEL_EVAL_TABLE.md)
   记录不同 AI 模型在各任务上的表现

### D. 流程示例类

要看闭环流程怎么落在具体 case 上时看：

1. [CLOSED_LOOP_EXAMPLE_COMPARATOR.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/CLOSED_LOOP_EXAMPLE_COMPARATOR.md)
   轻量实例
2. [CLOSED_LOOP_EXAMPLE_ADC.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/CLOSED_LOOP_EXAMPLE_ADC.md)
   中复杂度实例

### E. 论文与研究组织类

要准备 paper 或整理研究脉络时看：

1. [VAEVAS_OPENLLM_STYLE_DRAFT.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/paper/VAEVAS_OPENLLM_STYLE_DRAFT.md)
   主草稿
2. [PAPER_GAP_CHECKLIST.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/paper/PAPER_GAP_CHECKLIST.md)
   还缺什么

### F. 协作与沟通类

要同步节奏、整理上传包时看：

1. [COMMUNICATION_PACK.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/ops/COMMUNICATION_PACK.md)
2. [DAILY_SYNC.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/ops/DAILY_SYNC.md)
3. [UPLOAD_PACK_NOTE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/ops/UPLOAD_PACK_NOTE.md)

---

## 4. referencepaper 目录是做什么的

`referencepaper/` 不是项目资产本身，而是：

1. 相关论文 PDF 存档
2. related work 写作素材
3. benchmark 设计参考来源

先看：

1. [referencepaper/README.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/referencepaper/README.md)

目前已经放进去的几篇是：

1. `VerilogEval`
2. `VGen`
3. `OpenLLM-RTL`
4. `RTL-Coder`

---

## 5. templates / status / risks 是做什么的

### `templates/`

放的是模板，不是当前结论。

适合在这些场景下使用：

1. 写日报
2. 写周报
3. 记风险

### `status/`

放的是阶段状态和周度状态记录。

### `risks/`

放的是风险清单和处理记录。

---

## 6. 你现在应该看哪一部分

如果你现在的目标是：

1. 新人上手
   先看 [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/00_START_HERE.md)
2. 跑一个 example
   先看 [EXAMPLE_TO_BENCHMARK_WORKFLOW.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/EXAMPLE_TO_BENCHMARK_WORKFLOW.md)
3. 填 benchmark 结果
   先看 [BENCHMARK_RESULT_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/BENCHMARK_RESULT_TABLE.md)
4. 测试不同 AI 模型
   先看 [AI_MODEL_EVAL_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/AI_MODEL_EVAL_TABLE.md)
5. 看闭环流程怎么落地
   先看 [CLOSED_LOOP_EXAMPLE_ADC.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/CLOSED_LOOP_EXAMPLE_ADC.md)
6. 写论文
   先看 [VAEVAS_OPENLLM_STYLE_DRAFT.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/paper/VAEVAS_OPENLLM_STYLE_DRAFT.md)

---

## 7. 一句话版导航

如果只记一句：

1. `onboarding/` 解决“我现在怎么开始”
2. `docs/` 解决“团队现在怎么做事”
3. `referencepaper/` 解决“我们参考了谁”
4. `templates/status/risks` 解决“怎么记录和同步”
