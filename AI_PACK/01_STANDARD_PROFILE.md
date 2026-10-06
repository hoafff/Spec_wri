# AI ATTACHMENT 01 — Digital IP Specification Standard Profile

> **Purpose:** Attach this file to a new AI chat when building a Digital IC / RTL IP specification.  
> This is a **learning/compliance profile**, not a replacement for the original standards.

---

## 1. Authority model

When generating a specification, use this priority:

```text
P0 — Project source requirements / datasheet / explicit architect decisions
P1 — Applicable normative standards
P2 — Reference specifications / examples
P3 — Engineering inference
```

Rules:

- P3 must never override P0–P2.
- If P0 does not define a behavior, do **not** silently copy it from P2.
- Missing decisions that affect externally observable hardware behavior must be **TBD**.
- Any temporary engineering assumption must be labeled **ASSUMPTION**.
- Any requirement logically inferred from other requirements must be labeled **DERIVED**.
- Requirements directly supported by project input must be labeled **SOURCE**.

---

## 2. Primary hardware standard profile

### ECSS-E-ST-20-40C (11 October 2023)

Title: **ASIC, FPGA and IP Core engineering**

Official source:  
https://ecss.nl/standard/ecss-e-st-20-40c-asic-fpga-and-ip-core-engineering-11-october-2023/

Use especially the material concerning the **DEVICE Requirements Specification (DRS)** and Annex A.

For a Digital IP specification, check applicability of at least:

- device/system overview;
- partitioning and configuration;
- operating modes;
- interfaces;
- conventions (bit numbering, naming, data representation);
- functions and performance;
- internal/external protocols;
- operating frequency / clock domains;
- reset domains and reset behavior;
- internal functional behavior;
- external interface behavior;
- error handling;
- testability / DFT when applicable;
- technology constraints when applicable;
- power/electrical/thermal/package/radiation items when applicable.

For an RTL-only educational block, physical/device-level items may be **N/A**, but they should not be silently omitted if a compliance matrix is being produced.

---

## 3. Requirements-engineering profile

### ISO/IEC/IEEE 29148:2018

Title: **Systems and software engineering — Life cycle processes — Requirements engineering**

Official source:  
https://www.iso.org/standard/72089.html

Use it as a requirements-engineering discipline reference.

A useful requirement should be:

- necessary;
- clear;
- unambiguous;
- singular enough to reason about;
- feasible;
- verifiable/testable;
- traceable;
- consistent with other requirements;
- written at the correct abstraction level.

Do not claim formal ISO compliance from this summary. Use the original standard when compliance is required.

---

## 4. Hardware requirement quality rules

For each functional requirement, try to make these explicit:

```text
CONDITION
    ↓
TRIGGER / EVENT
    ↓
REQUIRED BEHAVIOR
    ↓
TIMING
    ↓
OBSERVABLE RESULT
```

Example pattern:

> When CONDITION is true at EVENT N, the IP **shall** produce OBSERVABLE RESULT by EVENT N+k.

If timing is irrelevant, state that explicitly rather than inventing a cycle count.

---

## 5. Requirement classification

Every important requirement should carry one of these tags:

| Tag | Meaning |
|---|---|
| SOURCE | Directly supported by project input |
| DERIVED | Logically required by other accepted requirements |
| ASSUMPTION | Temporary engineering assumption needing confirmation |
| TBD | Decision not yet made |
| N/A | Standard/checklist item not applicable, with reason |

Recommended IDs:

```text
REQ-FUNC-xxx   Functional behavior
REQ-INTF-xxx   Interface
REQ-CLK-xxx    Clock
REQ-RST-xxx    Reset
REQ-TIM-xxx    Timing/performance
REQ-CFG-xxx    Configuration/parameter
REQ-REG-xxx    Register/CSR
REQ-ERR-xxx    Error/illegal behavior
REQ-PWR-xxx    Power, if applicable
REQ-DFT-xxx    Testability, if applicable
```

---

## 6. Minimum Digital IP DRS coverage

The following is a practical 80/20 checklist derived for Digital RTL/IP work.

### Context
- Purpose
- In scope
- Out of scope
- System context
- Dependencies

### Configuration
- Parameters
- Legal ranges
- Defaults, only if specified
- Operating modes

### Clock and reset
- Clock names
- Clock domains
- Active edge
- Frequency constraints, if specified
- Reset polarity
- Synchronous/asynchronous semantics
- Assertion/deassertion behavior
- Reset state of externally visible state

### Interfaces
For each interface/signal:
- name;
- direction;
- width;
- protocol;
- clock domain;
- reset behavior if relevant;
- meaning;
- valid/ready or equivalent timing contract if applicable.

### Functional behavior
- Preconditions
- Trigger
- Result
- Timing
- Priority
- State transition when applicable
- Externally observable effect

### Boundary and simultaneous events
Explicitly evaluate:
- minimum/maximum values;
- overflow/wrap;
- underflow;
- full/empty;
- back-to-back operations;
- simultaneous operations;
- reset during activity;
- disabled mode;
- illegal request/state;
- X/Z handling when applicable.

### Registers, if present
- address/offset;
- width;
- access type;
- reset value;
- fields;
- side effects;
- W1C/W1S/etc. semantics;
- reserved behavior.

### Error/interrupt, if present
- cause;
- detection;
- reporting;
- masking;
- clearing;
- priority;
- reset behavior.

### Performance, if relevant
- latency;
- throughput;
- buffering;
- backpressure;
- response deadline.

### Traceability
- source requirement → IP requirement;
- IP requirement → spec section;
- IP requirement → verification target.

---

## 7. Specification readiness rule

A specification is **not READY FOR RTL/DV** when an unresolved TBD can change externally observable behavior.

Examples of blocking TBDs:

- reset is sync or async;
- read latency;
- behavior on full/empty;
- priority of simultaneous events;
- protocol handshake interpretation;
- interrupt clear semantics.

Examples that may be non-blocking:

- document owner;
- final document formatting;
- non-functional metadata that does not affect implementation.

---

## 8. Required compliance matrix

Before declaring a specification complete, produce:

| Standard/Profile Item | Applicable? | Spec Section | Source | Status | Open Issue |
|---|---:|---|---|---|---|

Status should be one of:

`PASS / OPEN / TBD / N/A`

---

## 9. Important limitation

This file is a **condensed learning profile**. It does not reproduce ECSS or ISO text and must not be treated as the legal/normative original.
