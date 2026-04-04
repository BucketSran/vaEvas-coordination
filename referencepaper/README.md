# Reference Papers

This folder stores external papers that are useful for positioning `vaEvas`.

Current purpose:

1. related-work reading
2. benchmark-design reference
3. paper-writing support

---

## Current Papers

### 1. VerilogEval

File:

1. [VerilogEval_2023.pdf](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/referencepaper/VerilogEval_2023.pdf)

Why it matters:

1. benchmark-oriented evaluation for Verilog generation
2. clear executable validation mindset
3. strong reference for minimal HDL evaluation loop

Useful takeaway for `vaEvas`:

1. `prompt -> code -> compile -> functional validation`

### 2. OpenLLM-RTL

File:

1. [OpenLLM-RTL_2025.pdf](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/referencepaper/OpenLLM-RTL_2025.pdf)

Why it matters:

1. open dataset and benchmark framing for RTL generation
2. benchmark-plus-framework style organization
3. useful template for turning project work into a paper narrative

Useful takeaway for `vaEvas`:

1. dataset / benchmark / validation / framework should be presented together

### 3. RTL-Coder

File:

1. [RTL-Coder_2024.pdf](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/referencepaper/RTL-Coder_2024.pdf)

Why it matters:

1. more complete RTL generation pipeline
2. clear split between data generation, training, inference, and benchmark inference
3. useful reference for repo-level project organization

Useful takeaway for `vaEvas`:

1. think beyond benchmark tasks alone
2. organize the project as `data / benchmark / training / inference / evaluation`

### 4. VGen

File:

1. [VGen_2022.pdf](/Users/bucketsran/Documents/TsingProject/vaEvas-coordination/referencepaper/VGen_2022.pdf)

Why it matters:

1. early benchmark and evaluation framing for Verilog generation
2. explicit syntax check plus testbench functional validation
3. useful reference for the minimal executable loop

Useful takeaway for `vaEvas`:

1. separate `compile success` from `functional success`
2. keep the minimal executable loop simple and auditable

---

## Suggested Reading Order

If the goal is to position `vaEvas` as a paper:

1. `VerilogEval`
2. `VGen`
3. `OpenLLM-RTL`
4. `RTL-Coder`

If the goal is to improve benchmark workflow:

1. `VGen`
2. `VerilogEval`
3. `OpenLLM-RTL`
4. `RTL-Coder`

---

## Mapping To vaEvas

These papers can be mapped to `vaEvas` like this:

1. `VerilogEval`
   reference for executable HDL benchmark basics
2. `VGen`
   reference for minimal closed-loop evaluation
3. `OpenLLM-RTL`
   reference for paper and benchmark framing
4. `RTL-Coder`
   reference for full project-layer organization

What `vaEvas` adds beyond them:

1. Verilog-A focus rather than RTL focus
2. EVAS-first runtime validation
3. optional EVAS-Spectre parity loop
4. benchmark construction from real behavioral examples
