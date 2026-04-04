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
9. `tier` (`raw` / `verified`)
10. `verification_status` (`pending` / `passed` / `failed`)
11. `benchmark_seed`
12. `result_path`
13. `pr_link`
14. `notes`

For closed-loop or dual-validation cases, also fill:

1. `evas_fb_hz`
2. `spectre_fb_hz`
3. `ppm_cross_delta`
4. `lock_time_delta_s`
5. `parity_status`

---

## Table

| owner | case_name | category | source_path | dut_compile | tb_compile | tran_generated | sim_correct | tier | verification_status | benchmark_seed | evas_fb_hz | spectre_fb_hz | ppm_cross_delta | lock_time_delta_s | parity_status | result_path | pr_link | notes |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| shenbufan | lfsr_smoke | digital-logic | `behavioral-veriloga-eval/tasks/end-to-end/voltage/lfsr_smoke` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `raw` | `pending` | `benchmark-seed` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | task assets created 2026-04-05; example: examples/digital-logic/lfsr |
| shenbufan | clk_burst_gen_smoke | stimulus | `behavioral-veriloga-eval/tasks/end-to-end/voltage/clk_burst_gen_smoke` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `raw` | `pending` | `benchmark-seed` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | task assets created 2026-04-05; example: examples/stimulus/clk_burst_gen |
| shenbufan | digital_basics_smoke | digital-logic | `behavioral-veriloga-eval/tasks/end-to-end/voltage/digital_basics_smoke` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `raw` | `pending` | `benchmark-seed` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | task assets created 2026-04-05; multi-module (AND/OR/NOT/DFF); example: examples/digital-logic/digital_basics |
| liangyuxuan | dac_binary_clk_4b_smoke | data-converter | `behavioral-veriloga-eval/tasks/end-to-end/voltage/dac_binary_clk_4b_smoke` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `raw` | `pending` | `benchmark-seed` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | task assets created 2026-04-05; example: examples/data-converter/dac_binary_clk_4b |
| liangyuxuan | adc_dac_ideal_4b_smoke | data-converter | `behavioral-veriloga-eval/tasks/end-to-end/voltage/adc_dac_ideal_4b_smoke` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `raw` | `pending` | `benchmark-seed` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | task assets created 2026-04-05; ADC+DAC chain; example: examples/data-converter/adc_dac_ideal_4b |
| liangyuxuan | dwa_ptr_gen_smoke | calibration | `behavioral-veriloga-eval/tasks/end-to-end/voltage/dwa_ptr_gen_smoke` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `raw` | `pending` | `benchmark-seed` | `N/A` | `N/A` | `N/A` | `N/A` | `single-sim` | `[TODO]` | `[TODO]` | task assets created 2026-04-05; example: examples/calibration/dwa_ptr_gen |
| team | cppll_timer | pll-closed-loop | `vaEvas/testspace/cppll` | `pass` | `pass` | `pass` | `pass` | `verified` | `passed` | `seed` | `50e6` | `50e6` | `0.0` | `[TODO]` | `dual-validated` | `testspace/cppll/output/timer_full_while_fix` | `[TODO]` | while + timer parity closure |
| team | cppll_param_shift | pll-closed-loop | `vaEvas/testspace/cppll` | `pass` | `pass` | `pass` | `pass` | `verified` | `passed` | `seed` | `49e6` | `49e6` | `0.0` | `9.99e-08` | `dual-validated` | `testspace/cppll/output/timer_full_param_shift` | `[TODO]` | parameter robustness check |
| team | adpll_timer | pll-closed-loop | `vaEvas/testspace/adpll` | `pass` | `pass` | `pass` | `pass` | `verified` | `passed` | `seed` | `50e6` | `50e6` | `0.0` | `2.5e-11` | `dual-validated` | `testspace/adpll/output/adpll_full_tuned` | `[TODO]` | timer baseline |
| team | adpll_idtmod | pll-closed-loop | `vaEvas/testspace/adpll` | `pass` | `pass` | `pass` | `pass` | `verified` | `passed` | `seed` | `50e6` | `50e6` | `0.0` | `7.73e-12` | `dual-validated` | `testspace/adpll/output/adpll_idtmod_full` | `[TODO]` | idtmod compatibility path |
| team | adpll_lock_smoke | end-to-end-task | `behavioral-veriloga-eval/tasks/end-to-end/voltage/adpll_lock_smoke` | `pass` | `pass` | `pass` | `pass` | `verified` | `passed` | `formal-benchmark` | `[TODO]` | `[TODO]` | `[TODO]` | `[TODO]` | `task-check` | `[TODO]` | `[TODO]` | already formalized benchmark task |

---

## Fill Rules

1. Use `pass` / `fail` / `N/A` where possible, not free-form wording.
2. Use absolute result paths or repository-relative result paths that others can reproduce.
3. If a case is not dual-validated, fill parity columns with `N/A`.
4. If a PR does not exist yet, keep `pr_link` as `[TODO]`.
5. If a result is provisional, say so in `notes`.
6. New rows default to `tier=raw` and `verification_status=pending`.
7. Only after passing the required validation gate can a row be promoted to `tier=verified` and `verification_status=passed`.

---

## Suggested Weekly Summary

At the end of each week, summarize:

1. how many rows were newly filled
2. how many cases are in `raw` vs `verified`
3. how many rows were promoted (`raw -> verified`)
4. how many cases reached `benchmark_seed`
5. how many cases reached `formal-benchmark`
6. how many rows are blocked by compile/runtime/check issues
7. top repeated failure modes
