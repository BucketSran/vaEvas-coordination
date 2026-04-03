# EVAS ↔ Virtuoso 闭环验证与 Benchmark 规范

## 1. 目标与原则

本规范用于团队统一执行 Verilog-A 行为一致性验证。

核心目标：

1. 提升 EVAS 与 Virtuoso/Spectre 的行为一致性。
2. 建立可复现、可比较、可持续迭代的 benchmark。

核心原则：

1. EVAS-first：先跑 EVAS 预检，再跑 Spectre 对照。
2. 先修 EVAS：若不一致，优先修 EVAS 语义层。
3. 边界明确：不触碰 EVAS 矩阵求解底层原理。
4. 证据驱动：所有结论必须附指标和产物路径。

---

## 2. 适用范围

适用于团队所有需要 EVAS 与 Spectre 对照的任务，包括：

1. 新模型接入验证
2. EVAS 语义修复验证
3. 回归风险检查
4. benchmark 周期更新

示例目录（CPPLL）：

1. `<repo>/vaEvas/testspace/cppll`
2. 运行脚本：`run_dual_verify.py`
3. gate 脚本：`ab_gate_decision.py`

---

## 3. 标准闭环流程

## 3.1 Step 1: 生成或更新模型代码

要求：

1. 明确 DUT 与 testbench。
2. 固定输入激励与观察窗。
3. 输出目录用独立 label，避免覆盖历史数据。

## 3.2 Step 2: EVAS 预检

命令模板：

```bash
cd <repo>/vaEvas/testspace/cppll
python3 run_dual_verify.py --tb tb_cppll_lock_iter2.scs --va cppll_va.va --label <label> --evas-only
```

通过条件：

1. EVAS 仿真成功。
2. 关键信号非退化（非全常值、非空输出）。

## 3.3 Step 3: EVAS + Spectre 全对照

命令模板：

```bash
cd <repo>/vaEvas/testspace/cppll
python3 run_dual_verify.py --tb tb_cppll_lock_iter2.scs --va cppll_va.va --label <label>
```

输出文件：

1. `output/<label>/consistency_report.json`
2. `output/<label>/evas/tran.csv`
3. `output/<label>/spectre/tran_spectre.csv`

## 3.4 Step 4: Gate 判定

命令模板：

```bash
cd <repo>/vaEvas/testspace/cppll
python3 ab_gate_decision.py \
  --baseline output/baseline_no_idt_ppm/consistency_report.json \
  --candidate output/<label>/consistency_report.json \
  --primary ppm_cross_delta \
  --max-abs 1000 \
  --evas-fix-attempt <n> \
  --max-evas-fix-attempts 3
```

重点看 `next_action`：

1. `accept_candidate`：当前候选可接受。
2. `fix_evas_semantics_and_rerun`：继续修 EVAS 语义并复跑。
3. `review_model_code_after_evas_attempts`：EVAS 尝试已到上限，回看模型代码。

## 3.5 Step 5: EVAS 修复优先级

不一致时，优先按以下顺序修 EVAS：

1. 事件触发语义（cross/above/timer）
2. 调度与重排策略（下一触发时刻、步进边界）
3. 观测与统计口径（计边阈值、去毛刺）

禁止项：

1. 未经评审直接改矩阵求解底层。
2. 没有对照数据就改模型参数来“对齐结果”。

## 3.6 Step 6: 进入模型代码复核条件

仅当以下条件同时满足时才回看模型代码：

1. EVAS 语义修复连续 3 轮无明显改善。
2. baseline 与 candidate 指标都有效。
3. 已排除统计口径偏差。

---

## 4. 指标体系（建议团队统一）

## 4.1 主指标

1. `ppm_cross_delta`
2. `rmse_vctrl_v`
3. `rmse_fb_v`

## 4.2 辅助指标

1. `evas_fb_hz` 与 `spectre_fb_hz`
2. `lock_time_delta_s`
3. 末窗 lock 占比（建议新增并长期跟踪）

## 4.3 判定建议

阶段化阈值建议：

1. P0（系统可用）：`ppm_cross_delta <= 100000`
2. P1（工程可比）：`ppm_cross_delta <= 10000`
3. P2（目标收敛）：`ppm_cross_delta <= 1000`

说明：

1. 阈值不宜一步到位，否则容易卡死迭代节奏。
2. 统一评估窗和口径比“单点好看”更重要。

---

## 5. Benchmark 建设规范

## 5.1 单条 benchmark 至少包含

1. DUT 与 testbench 文件版本
2. 运行命令
3. 报告路径
4. 关键指标
5. 判定结果
6. 下一步动作

## 5.2 建议目录组织

可在任务目录下按 label 保留完整历史：

1. `output/<label>/consistency_report.json`
2. `output/<label>/gate_decision.json`
3. `output/<label>/evas/*`
4. `output/<label>/spectre/*`

## 5.3 周期维护建议

每周至少维护一次：

1. 新增案例数
2. 达标案例数
3. 回归退化案例数
4. Top 3 失败模式
5. 对应修复动作与效果

---

## 6. 任务角色分工建议

1. 模型负责人：维护 DUT 与 testbench 的一致输入定义。
2. EVAS 负责人：维护语义实现与回归稳定性。
3. Benchmark 负责人：维护指标、阈值、报表与周度总结。

多人协作时，必须保证：

1. 同一轮只改一个主变量（模型或 EVAS 语义）。
2. 每轮都有可复现实验标签和结果产物。

---

## 7. 复盘模板（每轮都写）

建议固定写 6 行：

1. 本轮目标
2. 修改点
3. 运行命令
4. 关键指标变化
5. 判定与 next_action
6. 风险与下轮计划

---

## 8. 团队执行口令（建议统一）

在任务开始前，可直接复制这句给 AI 或新成员：

```text
按 EVAS-first 闭环执行：先 EVAS 预检，再 Spectre 对照；若不一致先修 EVAS 语义层，不改矩阵求解底层；每轮输出 consistency_report 和 gate_decision，并给出下一轮动作。
```

这样可以显著减少“只改代码不留证据”的问题。
