# Work Assignment

这份文件是当前阶段最直接的任务分配单。

目的：

1. 让每个人知道自己先做什么
2. 避免重复劳动
3. 保证 benchmark、结果表、PR 三件事一起推进

如果你只想知道“我现在该做哪个 case”，优先看这份文件。

---

## 1. 当前分工原则

本轮分工遵循三个原则：

1. 新同学先从可执行、可解释、容易形成 benchmark seed 的 case 开始
2. 先补 benchmark 覆盖率和结果表，不优先碰 EVAS 内核
3. 每个人的任务都必须以 `结果表 + benchmark seed + PR` 结束

---

## 2. 谁负责什么

### shenbufan

定位：

`负责数字逻辑 / stimulus 方向的基础 benchmark 覆盖率。`

第一轮任务顺序：

1. `lfsr`
2. `clk_burst_gen`
3. `digital_basics`

对应路径：

1. `behavioral-veriloga-eval/examples/digital-logic/lfsr`
2. `behavioral-veriloga-eval/examples/stimulus/clk_burst_gen`
3. `behavioral-veriloga-eval/examples/digital-logic/digital_basics`

最低目标：

1. 至少完成 1 个 case 的 `L0 + L1`
2. 至少把 1 个 case 推成 benchmark seed candidate
3. 填 [BENCHMARK_RESULT_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/BENCHMARK_RESULT_TABLE.md)
4. 填 [AI_MODEL_EVAL_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/AI_MODEL_EVAL_TABLE.md)
5. 提 1 个 PR

推荐交付顺序：

1. 先 `lfsr`
2. 再 `clk_burst_gen`
3. `digital_basics` 作为补充

### liangyuxuan

定位：

`负责 data-converter / calibration 方向的行为类 benchmark 覆盖率。`

第一轮任务顺序：

1. `dac_binary_clk_4b`
2. `adc_dac_ideal_4b`
3. `dwa_ptr_gen`

对应路径：

1. `behavioral-veriloga-eval/examples/data-converter/dac_binary_clk_4b`
2. `behavioral-veriloga-eval/examples/data-converter/adc_dac_ideal_4b`
3. `behavioral-veriloga-eval/examples/calibration/dwa_ptr_gen`

最低目标：

1. 至少完成 1 个 case 的 `L0 + L1`
2. 至少把 1 个 case 推成 benchmark seed candidate
3. 填 [BENCHMARK_RESULT_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/BENCHMARK_RESULT_TABLE.md)
4. 填 [AI_MODEL_EVAL_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/AI_MODEL_EVAL_TABLE.md)
5. 提 1 个 PR

推荐交付顺序：

1. 先 `dac_binary_clk_4b`
2. 再 `adc_dac_ideal_4b`
3. `dwa_ptr_gen` 作为补充

### 当前负责人

定位：

`负责高价值 parity case、benchmark 方法收敛和论文主线。`

当前重点：

1. 维护 `CPPLL / ADPLL` 这类高价值闭环案例
2. 审核两位同学的 benchmark seed 和结果表
3. 维护论文主草稿与 related work
4. 决定哪些 case 值得升格成正式 benchmark

---

## 3. 每个人必须交什么

每位同学本轮任务至少提交：

1. case 选题理由
2. 运行命令
3. 关键结果路径
4. `dut_compile / tb_compile / tran_generated / sim_correct`
5. 是否达到 benchmark seed candidate
6. 在 [BENCHMARK_RESULT_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/BENCHMARK_RESULT_TABLE.md) 中填入对应数据
7. 在 [AI_MODEL_EVAL_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/AI_MODEL_EVAL_TABLE.md) 中填入对应模型行
8. 1 个 PR

---

## 4. 现在不要重复做什么

以下 case 当前不适合再作为新人第一轮重复劳动：

1. `clk_div_smoke`
2. `comparator_smoke`
3. `ramp_gen_smoke`
4. `d2b_4bit_smoke`
5. `adpll_lock_smoke`

原因：

1. 已经有正式 task
2. 已做过首轮闭环
3. 当前更需要补新的 benchmark 覆盖面

---

## 5. 推荐执行顺序

如果是新人，建议按这个顺序做：

1. 看 [00_START_HERE.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/00_START_HERE.md)
2. 看 [NEW_MEMBER_START.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/onboarding/NEW_MEMBER_START.md)
3. 看 [EXAMPLE_TO_BENCHMARK_WORKFLOW.md](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/docs/benchmark/EXAMPLE_TO_BENCHMARK_WORKFLOW.md)
4. 认领自己的 case
5. 先跑 `L0`
6. 再跑 `L1`
7. 填两张表
8. 判断能否成为 benchmark seed
9. 提 PR

---

## 6. 一句话版

如果只记一件事：

`每个人这轮都不是只把 case 跑通，而是要把 case 变成可记录、可比较、可提 PR 的 benchmark 工作成果。`
