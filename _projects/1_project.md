---
layout: page
title: Custom 8-bit CPU
description: CPU Architecture at Northwestern University
img: assets/img/1.jpg
importance: 2
category: work
related_publications: false
profile_date: 2024-07-15
profile_importance: 2
profile_summary: Designed and fabricated an 8-bit CPU with custom ISA, control logic, and assembly tooling during a CTD Northwestern residency.
---

Three weeks, a bench full of discrete logic, and a mandate to understand computers from the transistor up. Working with Windy City Labs at CTD Northwestern, I engineered an 8-bit CPU: defining the instruction set, wiring the control logic, and validating everything with a bespoke assembler.

**Hardware architecture**
- Harvard-style data path with dedicated instruction and data memory, microcoded control ROM, and tri-state bus arbitration.
- Custom ISA featuring 16 opcodes (ALU, branch, memory, IO) with single-cycle execution for arithmetic and pipelined micro-ops for memory access.
- PLA-driven control unit that sequences clock phases, manages register enables, and stabilises asynchronous inputs from the front-panel switches.

**Tooling & validation**
- KiCad schematics + PCB layouts for the ALU, register file, and clock generator; SPICE checks confirmed timing margins before fabrication.
- Wrote a Python assembler that emits hex suitable for the EEPROM burner; added macros for loops and immediate constants to speed prototyping.
- Oscilloscope + logic analyser sessions captured micro-instruction traces, letting me tune propagation delay and debounce timing.

**Teaching impact**
- Delivered lightning talks to other cohorts to explain opcodes, address modes, and why the flag register matters for branching.
- Produced lab notes and test programs (Fibonacci, LED chaser, mini calculator) so future students can extend the platform.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/1.1.jpg" title="KiCad schematic snapshot" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Control-unit schematic driving instruction sequencing and bus arbitration.
</div>

Next up: port the design into CPLDs for a compact Mk2 and explore microcode tweaks that unlock multiply/divide instructions.
