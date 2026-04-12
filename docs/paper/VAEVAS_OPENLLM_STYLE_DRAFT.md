# vaEvas: An EVAS-First Benchmarking and Validation Framework for Verilog-A Behavioral Model Generation

## Status

This is a working draft written in an `OpenLLM-RTL`-style structure.

Purpose:

1. summarize what `vaEvas` has already built
2. organize the work into a paper-like narrative
3. leave explicit blanks for the next stage of work

This is not the final paper text.

Execution checklist for closing the paper gaps:

1. [PAPER_GAP_CHECKLIST.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/paper/PAPER_GAP_CHECKLIST.md)

---

## 1. Abstract

Large language models have recently shown strong performance on digital HDL generation, but analogous evaluation infrastructure for Verilog-A behavioral modeling remains limited. We present `vaEvas`, an EVAS-first framework for Verilog-A generation, execution, cross-simulator validation, and benchmark construction. The framework links four layers: simulator capability development in `EVAS`, benchmark task authoring in `behavioral-veriloga-eval`, modeling guidance in `veriloga-skills`, and project-level workflow coordination in `coordination`. Instead of treating text-only code generation as the endpoint, `vaEvas` emphasizes executable evaluation: generated models must compile, run, and satisfy behavior checks under EVAS, and closed-loop cases can be further compared against Virtuoso/Spectre under identical stimuli. We describe the current workflow from `example -> closed loop verification -> benchmark seed -> task PR`, report initial closed-loop case studies including `CPPLL` and `ADPLL`, and show how parity-driven debugging led to concrete EVAS semantic fixes such as `while` support and improved timer scheduling behavior. We also identify the missing pieces required to turn the current system into a mature community benchmark, including dataset scaling, unified scoring, baselines, and broader task coverage.

## 2. Introduction

Digital HDL evaluation has recently benefited from benchmarks such as `VerilogEval` and larger RTL-oriented datasets such as `OpenLLM-RTL`. In contrast, Verilog-A remains under-served despite its practical importance in analog and mixed-signal behavioral modeling. The gap is not only a data gap but also an execution gap: useful Verilog-A evaluation must handle simulator compatibility, event semantics, closed-loop dynamics, and benchmark rules that are grounded in actual model behavior rather than text similarity.

Useful external references currently collected for positioning:

1. [referencepaper/README.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/referencepaper/README.md)

`vaEvas` is motivated by this gap. Our goal is to build an end-to-end loop for Verilog-A:

1. generate or author EVAS-compatible Verilog-A
2. execute it under EVAS
3. validate behavior with explicit checks
4. use Spectre as a cross-simulator oracle when needed
5. convert stable examples into reusable benchmarks

The current system is intentionally EVAS-first. This means:

1. EVAS execution is the primary gate for benchmark inclusion
2. Spectre comparison is used for parity validation, especially on closed-loop cases
3. benchmark value comes from executable behavior, not text resemblance alone

## 3. Problem Statement

We study the following practical problem:

`How can we evaluate and improve Verilog-A model generation in a way that is executable, simulator-aware, and reusable as a benchmark?`

This differs from common code-generation benchmarks in three ways:

1. Verilog-A correctness is often behavioral rather than purely syntactic
2. simulator semantics can materially affect observed behavior
3. many valuable tasks are closed-loop and require waveform- or lock-based checks

Accordingly, `vaEvas` treats a task as solved only when it meets staged runtime criteria such as:

1. DUT compile success
2. testbench compile success
3. transient output generation
4. task-specific behavior checks
5. parity evidence when the case is a closed-loop benchmark seed

## 4. System Overview

The current `vaEvas` stack has four repositories:

1. `EVAS`
   simulator semantics, parser/runtime support, tests, example execution
2. `behavioral-veriloga-eval`
   benchmark tasks, prompts, metadata, checks, runners, reports
3. `veriloga-skills`
   generation guidance, domain routing, EVAS compatibility policy, modeling patterns
4. `coordination`
   workflow definition, onboarding, benchmark conversion process, documentation

Together, they form a loop:

`model/task idea -> EVAS execution -> behavior validation -> parity debugging -> benchmark formalization -> PR-based integration`

## 5. Benchmark Philosophy

The benchmark philosophy in `vaEvas` is execution-first.

### 5.1 Core principles

1. do not score a task only by code appearance
2. require runnable evidence wherever possible
3. keep benchmark rules interpretable
4. use parity checks for high-value closed-loop tasks
5. preserve failure attribution so simulator issues and model issues are not mixed together

### 5.2 Example-to-benchmark conversion

A case is not promoted by copying files alone. It must pass the following workflow:

1. select an example with real modeling meaning
2. run EVAS successfully
3. perform EVAS + Spectre comparison when the case is closed-loop or semantically sensitive
4. define benchmark value in one sentence
5. formalize `prompt.md`, `meta.json`, and `checks.yaml`
6. implement runner checks
7. replay validated outputs
8. submit a dedicated PR

This workflow is already documented and used inside the team.

## 6. Task Taxonomy

At the moment, `vaEvas` covers or is beginning to cover the following task types:

1. simple voltage-domain executable smoke tasks
2. digital-style control/stimulus blocks written in Verilog-A
3. data-converter and calibration-flavored examples
4. closed-loop clocking and PLL-style behavioral models

Current concrete seed cases include:

1. `CPPLL timer` closed-loop case
2. `CPPLL parameter-shift` variant
3. `ADPLL timer` closed-loop case
4. `ADPLL idtmod` compatibility case
5. `adpll_lock_smoke` as a formalized end-to-end benchmark task

### Blank: full benchmark inventory

`[TODO]`

Add a complete table of:

1. current tasks in `behavioral-veriloga-eval`
2. candidate examples not yet promoted
3. per-task status: smoke, benchmark seed, or formal benchmark

## 7. Evaluation Pipeline

The current evaluation pipeline can be summarized as follows.

### 7.1 Generation or authoring stage

The input may be:

1. an existing example
2. a generated Verilog-A candidate
3. a manually-authored reference model

### 7.2 EVAS execution stage

The first hard gate is EVAS execution:

1. parser/compiler acceptance
2. DUT/testbench compilation
3. transient result generation
4. non-degenerate output behavior

### 7.3 Behavior scoring stage

Task-specific checks are implemented in the benchmark runner.

Examples:

1. late-window clock frequency alignment
2. lock assertion visibility
3. waveform-based or logic-style output checks

### 7.4 Cross-simulator parity stage

For closed-loop cases, EVAS results are compared with Spectre using identical stimuli.

Current parity metrics include:

1. `ppm_cross_delta`
2. `rmse_vctrl_v`
3. `rmse_fb_v`
4. `evas_fb_hz`
5. `spectre_fb_hz`
6. `lock_time_delta_s`

### 7.5 Failure-attribution stage

When mismatch appears, the workflow explicitly prefers:

1. checking EVAS semantics first
2. avoiding premature benchmark rule changes
3. escalating to model-code review only after repeated EVAS-side attempts fail

## 8. Current Technical Contributions

The current project already contains several concrete technical contributions.

### 8.1 EVAS semantic repair through parity debugging

Closed-loop verification exposed an EVAS mismatch that looked like a timer inconsistency with Virtuoso/Spectre. The actual root cause was deeper:

1. missing or incorrect `while` support affected phase-wrap logic
2. timer scheduling behavior needed more reliable absolute-time handling

This led to:

1. frontend/compiler support for `while`
2. runtime improvements for timer-related parity behavior
3. additional regression tests

### 8.2 Proof that lock behavior does not require `idtmod`

The project showed that stable lock behavior can be achieved with event-driven timer-based modeling, without requiring `idtmod` for the baseline path.

This matters because:

1. it gives an EVAS-friendly modeling baseline
2. it reduces premature dependence on more delicate operators
3. it creates a clean A/B path for future `idt/idtmod` decisions

### 8.3 `idtmod` as compatibility path rather than default path

The `ADPLL idtmod` variant demonstrates that `idtmod` can still be supported as a compatibility option, but should be justified through parity improvement rather than assumed as the default best style.

### 8.4 Formalization of benchmark-construction workflow

The team now has a reusable documented path from example to benchmark. This is important because it converts individual experiments into auditable benchmark growth.

## 9. Current Empirical Evidence

The current evidence base is still small, but it is already stronger than a toy demonstration.

### 9.1 Closed-loop cases already validated

Known validated directions include:

1. `CPPLL timer` parity closure after EVAS fixes
2. parameter-shifted `CPPLL` stability check
3. `ADPLL timer` successful closed-loop alignment
4. `ADPLL idtmod` compatibility validation

### 9.2 Benchmark task already formalized

The project has already promoted at least one case into a formal benchmark task:

1. `adpll_lock_smoke`

This includes:

1. prompt
2. metadata
3. checks
4. runner integration

### Blank: result table

`[TODO]`

Insert a compact quantitative table with:

1. task name
2. EVAS pass/fail
3. Spectre comparison status
4. main parity metric
5. promotion status

Working table template:

1. [BENCHMARK_RESULT_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/benchmark/BENCHMARK_RESULT_TABLE.md)

### Blank: baseline comparison

`[TODO]`

Add comparison against:

1. non-executable text-only evaluation
2. naive compile-only evaluation
3. digital HDL benchmark assumptions

Working model-evaluation table:

1. [AI_MODEL_EVAL_TABLE.md](/Users/bucketsran/Documents/TsingProject/vaEvas/coordination/docs/benchmark/AI_MODEL_EVAL_TABLE.md)

## 10. Comparison to RTL-Oriented Work

Compared with RTL-oriented benchmarks such as `VerilogEval` and `OpenLLM-RTL`, `vaEvas` differs in several ways.

### 10.1 Similarities

1. both aim to evaluate executable HDL generation
2. both benefit from standardized task packaging
3. both need clear pass/fail criteria and benchmark reproducibility

### 10.2 Key differences

1. `vaEvas` targets Verilog-A rather than RTL
2. `vaEvas` must handle analog behavioral semantics and event-driven modeling subtleties
3. `vaEvas` needs simulator-aware validation
4. `vaEvas` includes cross-simulator parity for selected tasks
5. `vaEvas` currently emphasizes workflow and failure attribution more explicitly

### 10.3 Related-Work Positioning

The closest public references to `vaEvas` currently come from RTL-oriented LLM evaluation and generation systems rather than from Verilog-A-specific benchmarks.

`VerilogEval` represents the most direct baseline for executable HDL evaluation. Its core contribution is to evaluate generated Verilog through runnable functional validation rather than text similarity alone. This is closely aligned with the execution-first philosophy of `vaEvas`. However, `vaEvas` differs by targeting Verilog-A behavioral models, where waveform semantics, event handling, and simulator behavior matter more directly than in typical RTL tasks.

`VGen` is especially useful as a reference for the minimal executable loop. It separates syntax acceptance from functional validation through testbenches, which maps naturally to the `L0/L1` split used in our workflow. In that sense, `VGen` is a useful conceptual baseline for the lightweight side of `vaEvas`: compile success is necessary but not sufficient, and behavior checks must remain explicit and auditable.

`OpenLLM-RTL` is closer to `vaEvas` in project shape than in domain. It treats RTL generation as a benchmark-and-framework problem rather than as isolated prompt demos. This is similar to how `vaEvas` tries to connect examples, benchmark tasks, checks, and evaluation artifacts into one system. The difference is that `vaEvas` adds simulator-aware behavioral validation and selective EVAS-Spectre parity loops for high-value tasks.

`RTL-Coder` is valuable as a reference for end-to-end project organization. It shows how a research effort can be structured across data generation, training, inference, and benchmark inference. While `vaEvas` is not yet equally mature on the model-training side, it can benefit from the same systems view: benchmark construction should not remain an isolated activity, but should eventually connect to task generation, model prompting, evaluation, and failure attribution.

Taken together, these RTL-side works suggest that `vaEvas` is best positioned not as a copy of an RTL benchmark, but as an extension of executable HDL evaluation into the Verilog-A setting. Its distinctive additions are:

1. Verilog-A rather than RTL as the target language
2. EVAS-first runtime validation
3. layered closure from minimal execution to parity-sensitive validation
4. benchmark construction from real behavioral examples
5. optional cross-simulator parity against Virtuoso/Spectre

The remaining related-work gap is on the Verilog-A side. Prior Verilog-A literature has addressed modeling tools, automatic behavioral abstraction, and data-driven model construction, but we have not yet fully integrated those references into a dedicated subsection. That integration remains necessary for a paper-ready version of this draft.

## 11. Data and Artifact Design

The benchmark artifact design currently centers around task directories with:

1. `prompt.md`
2. `meta.json`
3. `checks.yaml`
4. runner-side behavior check logic

Closed-loop artifact bundles may additionally include:

1. EVAS waveforms
2. Spectre waveforms
3. `consistency_report.json`
4. gate decisions and iteration labels

### Blank: dataset schema

`[TODO]`

Define a stable schema for:

1. task categories
2. reference artifacts
3. accepted metrics
4. failure tags
5. benchmark maturity stage

## 12. Skills and Human-in-the-Loop Workflow

One distinctive aspect of `vaEvas` is that benchmark growth is not treated as pure dataset scraping. Instead, model generation guidance and benchmark authoring are tied together through:

1. `veriloga-skills`
2. EVAS compatibility guidance
3. parity-gate rules for `idt/idtmod`
4. documented onboarding and PR workflow

This is useful because Verilog-A tasks often require:

1. domain-aware modeling patterns
2. simulator support awareness
3. structured debugging when runtime behavior is wrong

### Blank: human vs automated roles

`[TODO]`

Clarify which parts are currently:

1. human-authored
2. AI-assisted
3. automatically scored
4. not yet automated

## 13. Limitations

The current project has important limitations.

1. coverage is still small
2. the benchmark suite is not yet broad enough to claim field-wide representativeness
3. most current evidence is concentrated on voltage-domain and closed-loop examples
4. quantitative comparison against external baselines is still incomplete
5. benchmark maturity is uneven across task families
6. current reporting is stronger on workflow than on large-scale statistics

## 14. Next Priorities

The next stage of work should focus on the following blanks first.

### Priority A: scale benchmark inventory

`[TODO]`

Promote more examples into benchmark seeds, especially:

1. `lfsr`
2. `clk_burst_gen`
3. `digital_basics`
4. `dac_binary_clk_4b`
5. `adc_dac_ideal_4b`
6. `dwa_ptr_gen`

### Priority B: add formal result tables

`[TODO]`

Create reproducible tables for:

1. task counts
2. pass rates
3. parity-qualified tasks
4. failure modes
5. per-category coverage

### Priority C: unify scoring language

`[TODO]`

Define a consistent score stack across tasks, for example:

1. `dut_compile`
2. `tb_compile`
3. `sim_correct`
4. parity-qualified or not
5. failure attribution tag

### Priority D: strengthen related work

`[TODO]`

Integrate:

1. `VerilogEval`
2. `OpenLLM-RTL`
3. prior Verilog-A modeling/tool papers

### Priority E: prepare paper-grade figures

`[TODO]`

Potential figures:

1. overall system diagram
2. example-to-benchmark conversion pipeline
3. EVAS-first closed-loop parity loop
4. benchmark taxonomy table
5. CPPLL/ADPLL parity result snapshots

## 15. Proposed Paper Claim

If written as a paper today, the most honest claim would be:

`vaEvas is an emerging execution-first framework for Verilog-A generation evaluation, centered on EVAS-compatible runtime validation, parity-guided debugging, and benchmark construction from real behavioral examples.`

It is not yet strongest as a "large benchmark paper."

It is strongest today as a paper about:

1. evaluation methodology
2. simulator-aware benchmark construction
3. closed-loop behavioral validation workflow
4. early benchmark artifacts for Verilog-A

## 16. One-Paragraph Version

`vaEvas` aims to do for Verilog-A what recent HDL benchmarks have done for Verilog/RTL, but with a stronger emphasis on execution, simulator semantics, and closed-loop behavioral evidence. The current system already links simulator repair, benchmark authoring, skills guidance, and team workflow into one loop. Its clearest present strengths are EVAS-first evaluation, EVAS-Spectre parity debugging, and the conversion of real examples such as CPPLL and ADPLL into benchmark-ready assets. The main unfinished work is scale: more tasks, more uniform scoring, stronger baselines, and paper-grade aggregate results.
