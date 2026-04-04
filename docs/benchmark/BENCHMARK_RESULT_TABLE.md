# Benchmark Result Table

This file is the team-wide result table for benchmark-seed experiments.

Use it to collect data from:

1. example execution
2. benchmark conversion
3. closed-loop parity validation
4. PR-based benchmark integration

It is intended to support both:

1. weekly engineering tracking
2. later paper tables and summary statistics

---

## Required Columns

Every new case should try to fill these columns first:

1. `owner`
2. `case_name`
3. `category`
4. `source_path`
5. `dut_compile`
6. `tb_compile`
7. `tran_generated`
8. `sim_correct`
9. `benchmark_seed`
10. `result_path`
11. `pr_link`
12. `notes`

For closed-loop or dual-validation cases, also fill:

1. `evas_fb_hz`
2. `spectre_fb_hz`
3. `ppm_cross_delta`
4. `lock_time_delta_s`
5. `parity_status`

---

## Table

| owner | case_name | category | source_path | dut_compile | tb_compile | tran_generated | sim_correct | benchmark_seed | evas_fb_hz | spectre_fb_hz | ppm_cross_delta | lock_time_delta_s | parity_status | result_path | pr_link | notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| shenbufan | lfsr | digital-logic | `behavioral-veriloga-eval/examples/digital-logic/lfsr` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | first suggested case |
| shenbufan | clk_burst_gen | stimulus | `behavioral-veriloga-eval/examples/stimulus/clk_burst_gen` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | second suggested case |
| shenbufan | digital_basics | digital-logic | `behavioral-veriloga-eval/examples/digital-logic/digital_basics` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | optional follow-up |
| liangyuxuan | dac_binary_clk_4b | data-converter | `behavioral-veriloga-eval/examples/data-converter/dac_binary_clk_4b` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | first suggested case |
| liangyuxuan | adc_dac_ideal_4b | data-converter | `behavioral-veriloga-eval/examples/data-converter/adc_dac_ideal_4b` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | second suggested case |
| liangyuxuan | dwa_ptr_gen | calibration | `behavioral-veriloga-eval/examples/calibration/dwa_ptr_gen` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | optional follow-up |
| team | cppll_timer | pll-closed-loop | `vaEvas/testspace/cppll` | `pass` | `pass` | `pass` | `pass` | `seed` | `50e6` | `50e6` | `0.0` | `[TODO]` | `dual-validated` | `testspace/cppll/output/timer_full_while_fix` | `[TODO]` | while + timer parity closure |
| team | cppll_param_shift | pll-closed-loop | `vaEvas/testspace/cppll` | `pass` | `pass` | `pass` | `pass` | `seed` | `49e6` | `49e6` | `0.0` | `9.99e-08` | `dual-validated` | `testspace/cppll/output/timer_full_param_shift` | `[TODO]` | parameter robustness check |
| team | adpll_timer | pll-closed-loop | `vaEvas/testspace/adpll` | `pass` | `pass` | `pass` | `pass` | `seed` | `50e6` | `50e6` | `0.0` | `2.5e-11` | `dual-validated` | `testspace/adpll/output/adpll_full_tuned` | `[TODO]` | timer baseline |
| team | adpll_idtmod | pll-closed-loop | `vaEvas/testspace/adpll` | `pass` | `pass` | `pass` | `pass` | `seed` | `50e6` | `50e6` | `0.0` | `7.73e-12` | `dual-validated` | `testspace/adpll/output/adpll_idtmod_full` | `[TODO]` | idtmod compatibility path |
| team | adpll_lock_smoke | end-to-end-task | `behavioral-veriloga-eval/tasks/end-to-end/voltage/adpll_lock_smoke` | `pass` | `pass` | `pass` | `pass` | `formal-benchmark` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `task-check` | `[TODO]` | `[TODO]` | already formalized benchmark task |

---

## Fill Rules

1. Use `pass` / `fail` / `N/A` where possible, not free-form wording.
2. Use absolute result paths or repository-relative result paths that others can reproduce.
3. If a case is not dual-validated, fill parity columns with `N/A`.
4. If a PR does not exist yet, keep `pr_link` as `[TODO]`.
5. If a result is provisional, say so in `notes`.

---

## Suggested Weekly Summary

At the end of each week, summarize:

1. how many rows were newly filled
2. how many cases reached `benchmark_seed`
3. how many cases reached `formal-benchmark`
4. how many rows are blocked by compile/runtime/check issues
5. top repeated failure modes
