# Weekly Status — 2026-04-05

## Summary

This week completed the first full round of benchmark seed task asset creation.

---

## What Was Done

### behavioral-veriloga-eval: feat/new-benchmark-seeds-2026-04-05

Created 10 new benchmark task directories under `tasks/end-to-end/voltage/`:

**shenbufan ownership:**
1. `lfsr_smoke` — 31-bit LFSR, digital-logic
2. `clk_burst_gen_smoke` — clock burst generator, stimulus
3. `digital_basics_smoke` — AND/OR/NOT/DFF, digital-logic

**liangyuxuan ownership:**
4. `dac_binary_clk_4b_smoke` — 4-bit clocked binary DAC
5. `adc_dac_ideal_4b_smoke` — ideal 4-bit ADC + DAC chain
6. `dwa_ptr_gen_smoke` — DWA pointer rotation, calibration

**team:**
7. `noise_gen_smoke` — Gaussian noise generator (tests `$rdist_normal`)
8. `dac_therm_16b_smoke` — 16-bit thermometer DAC
9. `sar_adc_dac_weighted_8b_smoke` — 8-bit SAR ADC + weighted DAC (hardest)
10. `gain_extraction_smoke` — multi-module dither gain extraction (most complex)

Each task includes: `prompt.md`, `meta.json` (tier=raw, verification_status=pending), `checks.yaml`.

### Runner improvements (simulate_evas.py, run_examples_suite.py)

- Extended `CHECKS` dict in `simulate_evas.py` to cover all 10 new `_smoke` task IDs
- Extended `TASK_BY_EXAMPLE` in `run_examples_suite.py` to map all 14 examples to their task dirs
- Fixed fallback in `task_dir_for()` to raise a clear error instead of silently using a wrong default
- Fixed manifest.json: corrected all paths from `behavioral-va-eval/` to `behavioral-veriloga-eval/`

### vaEvas-coordination: main

- `BENCHMARK_RESULT_TABLE.md`: added 10 new rows (all `raw/pending/benchmark-seed`)
- Committed stale doc cleanup (old root-level docs deleted, META_JSON_MIN_TEMPLATE added)
- `status/2026-04-05_weekly-status.md`: this file

---

## Current Benchmark Coverage

| tier | count | notes |
|---|---|---|
| `verified` | 5 | cppll_timer, cppll_param_shift, adpll_timer, adpll_idtmod, adpll_lock_smoke |
| `raw/pending` | 10 | all newly created task assets |
| no task yet | 0 | all examples now covered |

---

## Next Steps

1. **shenbufan**: run lfsr_smoke, clk_burst_gen_smoke in EVAS → fill result table rows → PR
2. **liangyuxuan**: run dac_binary_clk_4b_smoke, adc_dac_ideal_4b_smoke → fill result table → PR
3. **team**: PR `feat/new-benchmark-seeds-2026-04-05` → upstream (Arcadia-1)
4. **team**: run any model (Claude/GPT) on a subset and start filling AI_MODEL_EVAL_TABLE.md
5. **team**: write related work section using papers already in `referencepaper/`
6. **team**: build the 3 required paper figures (system overview, workflow, EVAS parity loop)

---

## Blockers

None known. All task assets are created; actual EVAS simulation runs are pending team action.
