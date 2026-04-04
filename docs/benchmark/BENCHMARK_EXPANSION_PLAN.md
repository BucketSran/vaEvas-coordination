# Benchmark Expansion Plan: 15 → 200 Tasks

This document describes the phased strategy for expanding the vaEvas benchmark from the current 15 tasks to a target of 200 verified tasks.

---

## Guiding Constraints

All benchmark tasks must satisfy:

1. **EVAS-compatible (voltage-domain only)**
   - Uses `V() <+`, `@(cross(...))`, `@(initial_step)`, `@(timer(...))`, `transition()`
   - Does NOT use `I() <+`, `ddt()`, `idt()`, `idtmod()`, `laplace_nd()`, `slew()`, `flicker_noise()`
   - See `veriloga-skills/veriloga/SKILL.md` for the full construct list
2. **Every task has EVAS + Spectre parity validation** (`parity_required: true`)
3. **Every task has at least 2 meaningful `sim_correct` checks**
4. **Tier progression**: `raw → verified` requires EVAS run + Spectre cross-check

---

## Current State (as of 2026-04-05)

| status | count | categories |
|---|---|---|
| verified (tier=verified, passed) | 6 | pll-closed-loop (×5), end-to-end-task (×1) |
| raw (tier=raw, pending) | 22 | digital-logic, data-converter, calibration, stimulus, measurement, sample-hold, phase-detector, comms |

---

## Phase 1: Deepen Existing Categories (target: ~60 tasks)

**Goal**: add difficulty variants to already-covered circuit types.
**Prerequisite**: current 22 raw tasks promoted to verified first.

### Expansion list

| base example | new variants | new task count |
|---|---|---|
| comparator (basic) | hysteresis variant, offset-search, strongarm, rail-to-rail | +4 |
| dac_binary_clk_4b | 6b, 8b, with mismatch model | +3 |
| dac_therm_16b | with DWA enabled, with element mismatch | +2 |
| sar_adc_dac_weighted_8b | 10b, with noise floor, with offset | +3 |
| flash_adc_3b | 4b, with offset/gain error | +2 |
| lfsr | 16-bit, 23-bit, with enable gating | +3 |
| gray_counter_4b | 8-bit, with load, with async reset | +3 |
| clk_div | divide-by-3, divide-by-N parametric | +2 |
| pfd_updn | with dead-zone, with reset delay | +2 |
| xor_phase_detector | with frequency offset test, lock range check | +2 |
| sample_hold | double-sampled, with droop model | +2 |
| serializer_8b | deserializer_8b, 16b variant | +2 |
| noise_gen | correlated noise pair, chirp generator | +2 |
| gain_extraction | gain vs. frequency sweep | +2 |

**Phase 1 net new tasks**: ~34 → total ~56

---

## Phase 2: New Circuit Domains (target: ~120 tasks)

**Goal**: add 5 new circuit categories not yet present in the benchmark.
**Prerequisite**: Phase 1 parity flow running smoothly.

### New categories and example circuits

| category | example circuits (EVAS-compatible behavioral) | estimated tasks |
|---|---|---|
| **oscillator** | ring_osc_3stage, vco_behavioral (timer-based, no idtmod), relaxation_osc | 12 |
| **frequency-divider** | div2, div4, dual_modulus_div (÷N/÷N+1) | 8 |
| **pipeline-logic** | 4-stage pipeline register, forwarding logic | 8 |
| **encoder-decoder** | priority_encoder_4b, thermometer_to_binary_8b, manchester_encoder | 10 |
| **power-switch** | behavioral transmission gate, programmable gain switch | 8 |

**Note on oscillator**: VCO in behavioral EVAS mode uses `@(timer(...))` with variable period set by `V(ctrl)` and `$bound_step()` — does NOT require `idtmod()`.

**Phase 2 net new tasks**: ~46 → total ~102

---

## Phase 3: System-Level and AI-Driven (target: ~200 tasks)

**Goal**: add multi-block integration tasks and use the AI evaluation loop to generate additional verified tasks.

### System-level tasks

| system | components | difficulty |
|---|---|---|
| charge-pump PLL behavioral | PFD + CP model + divider + VCO behavioral | hard |
| delta-sigma modulator 1st order | accumulator + 1b DAC + error feedback | hard |
| pipelined ADC 2-stage | MDAC behavioral × 2 + flash + digital correction | expert |
| serializer + clock recovery | serializer + CDR behavioral | hard |

**Estimated**: 20 tasks

### AI-generation-driven tasks

Once the evaluation framework is running, AI-generated Verilog-A that passes all checks can be promoted to benchmark:

```
model generates .va → EVAS compile + sim_correct passes → Spectre parity passes → human review → PR
```

Target: 30–40 additional tasks from AI output curation.

**Phase 3 net new tasks**: ~50–60 → total **~150–165**

---

## Path to 200

| source | task count |
|---|---|
| Current tasks (15) | 15 |
| Phase 1 additions | +41 |
| Phase 2 additions | +46 |
| Phase 3 system tasks | +20 |
| Phase 3 AI-driven curation | +40 |
| Parametric sweep variants (difficulty levels) | +38 |
| **Total** | **~200** |

---

## Category Coverage Target at 200

| category | target count |
|---|---|
| digital-logic | 30 |
| data-converter | 35 |
| pll-closed-loop | 20 |
| phase-detector | 15 |
| oscillator | 15 |
| sample-hold | 10 |
| calibration | 10 |
| stimulus | 10 |
| measurement | 10 |
| encoder-decoder | 15 |
| comms | 15 |
| power-switch | 10 |
| **Total** | **~195** |

---

## Bottleneck Analysis

| bottleneck | mitigation |
|---|---|
| Every task needs a verified EVAS example | Write examples first; parity is parallel (2 students) |
| Spectre parity is manual per-task effort | Batch by category; reuse testbench templates |
| `sim_correct` checks need domain knowledge | Write checks from example `validate_*.py` scripts |
| AI-driven tasks require human review gate | Set threshold: dut_compile + sim_correct + parity all pass |

---

## Assignment

| phase | who |
|---|---|
| Phase 1 example writing | Claude Code (automated) |
| Phase 1 parity validation | new team members (EVAS + Spectre/Virtuoso) |
| Phase 2 example writing | Claude Code + team review |
| Phase 2–3 parity validation | new team members |
| AI model evaluation runs | full team |
