# Example -> Benchmark 工作流

## 目标

把 `example` 或 `testspace` 里的可执行样例，转成团队可复用、可评分、可回归的 benchmark。

这不是“把文件搬过去”，而是走完一条标准闭环：

`选样例 -> 跑通 -> 双验证 -> 定义检查 -> 入 benchmark -> 提 PR`

---

## 什么样的 example 值得转 benchmark

至少满足以下 4 条：

1. 不是纯 toy case，而是代表一类真实建模问题。
2. 在 EVAS 中可执行。
3. 有明确的最小行为目标，不靠主观读波形。
4. 有区分度：改好会更好，改坏能看出来。

优先级：

1. 已有 EVAS 运行证据的稳定 example。
2. 已完成 EVAS + Spectre 闭环的样例。
3. 能覆盖关键语义链路的样例：
   `cross / timer / while / idtmod / lock / code update`

不建议第一轮直接转：

1. 还没跑通的样例。
2. 评分口径不清楚的样例。
3. 强依赖复杂模拟背景、暂时没人能解释的样例。

---

## 标准流程

### Step 1. 选一个 example

先写清楚：

1. 这个 example 在测什么。
2. 为什么它值得变成 benchmark。
3. 通过标准是什么。

### Step 2. 跑通 EVAS

至少拿到：

1. DUT 可编译。
2. testbench 可编译。
3. `tran.csv` 可生成。

### Step 3. 需要时做 Spectre 对照

对闭环类、事件链复杂类样例，优先做 EVAS + Spectre 双验证。

如果 EVAS 与 Spectre 不一致：

1. 先修 EVAS 语义层。
2. 不先改 benchmark 口径。
3. 不改矩阵求解底层原则。

### Step 4. 提炼 benchmark 意义

把这个 case 的价值写成一句话：

1. 它在测哪类行为模型。
2. 它在测哪类 EVAS 语义能力。
3. 它为什么不是普通 demo。

### Step 5. 正式落 benchmark 资产

放到：

`vaEvas/behavioral-veriloga-eval/tasks/...`

至少补齐：

1. `prompt.md`
2. `meta.json`
3. `checks.yaml`

### Step 6. 补 runner check

在 runner 里把 `sim_correct` 的最小判定写清楚。

要求：

1. 尽量用明确、可解释、可复现的规则。
2. 不要只写“波形看起来差不多”。

### Step 7. 用参考波形回喂一次

用已经验证过的参考输出，确认：

1. 新 benchmark 会判通过。
2. 检查规则不过严也不过松。

### Step 8. 提交 PR

每新增一个 benchmark seed，单独提一个 PR。

PR 至少写清楚：

1. 新增了哪个 task。
2. 这个 task 代表什么。
3. 跑了哪些命令。
4. 结果是什么。
5. 还有什么风险没覆盖。

---

## 已走通的参考样例

可以直接当团队模板看：

1. `CPPLL timer` 闭环样例
2. `ADPLL timer` 闭环样例
3. `ADPLL idtmod` 兼容样例

这些样例证明：

1. 我们可以先在 `testspace/` 做闭环。
2. 闭环稳定后再提炼成 benchmark。
3. `timer` 和 `idtmod` 都可以进入兼容性验证口径。

---

## 当前不建议重复做的 case

这些已经有正式 end-to-end task 或已做过首轮闭环，不适合作为新人第一轮重复劳动：

1. `clk_div_smoke`
2. `comparator_smoke`
3. `ramp_gen_smoke`
4. `d2b_4bit_smoke`
5. 已完成的 `adpll_lock_smoke`

---

## 两位新同学第一轮建议任务

### shenbufan

建议先接偏稳定、结构清楚、容易补 check 的 example：

1. `behavioral-veriloga-eval/examples/digital-logic/lfsr`
2. `behavioral-veriloga-eval/examples/stimulus/clk_burst_gen`
3. `behavioral-veriloga-eval/examples/digital-logic/digital_basics`

目标：

1. 先完成 1 条 benchmark seed。
2. 如果顺利，再补第 2 条。

优先顺序建议：

1. `lfsr`
2. `clk_burst_gen`
3. `digital_basics`

### liangyuxuan

建议先接偏 data-converter / calibration 的 example：

1. `behavioral-veriloga-eval/examples/data-converter/dac_binary_clk_4b`
2. `behavioral-veriloga-eval/examples/data-converter/adc_dac_ideal_4b`
3. `behavioral-veriloga-eval/examples/calibration/dwa_ptr_gen`

目标：

1. 先完成 1 条 benchmark seed。
2. 如果顺利，再补第 2 条。

优先顺序建议：

1. `dac_binary_clk_4b`
2. `adc_dac_ideal_4b`
3. `dwa_ptr_gen`

---

## 每位同学的最低交付

每条 benchmark seed 至少提交：

1. 选题理由
2. 运行命令
3. 结果路径
4. `prompt.md / meta.json / checks.yaml`
5. runner check 改动
6. 一次 PR

---

## 团队 gate

只有满足以下条件，example 才算正式进入 benchmark：

1. 有明确 benchmark 意义。
2. 有可执行检查。
3. 已用参考结果回喂验证。
4. 已通过 code review。
5. 已提 PR。
