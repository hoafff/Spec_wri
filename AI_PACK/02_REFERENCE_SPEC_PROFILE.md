# AI ATTACHMENT 02 — Real Digital IP Specification Reference Profile

> **Purpose:** Teach an AI what a good Digital IP spec looks like without letting it copy unrelated design decisions.

---

## 1. Reference specifications

### OpenTitan UART HWIP Technical Specification

https://opentitan.org/book/hw/ip/uart/

Useful sections include:

- Overview
- Features
- Description
- Hardware Interfaces
- Theory of Operation
- Registers
- Programmer-facing behavior where relevant

Hardware interface example:  
https://opentitan.org/book/hw/ip/uart/doc/interfaces.html

Theory of operation example:  
https://opentitan.org/book/hw/ip/uart/doc/theory_of_operation.html

### OpenTitan GPIO HWIP Technical Specification

https://opentitan.org/book/hw/top_earlgrey/ip_autogen/gpio/

Useful for studying:

- hardware feature summary;
- GPIO behavior;
- input/output-enable concepts;
- interrupts;
- registerized control;
- documented HW/SW interface.

### NASA/JPL ASIC Technical Specification guidance

https://parts.jpl.nasa.gov/asic/Sect.3.1.html

Use as a historical/practical ASIC technical-specification reference.

---

## 2. What may be learned from examples

The AI **may imitate**:

- document organization;
- section granularity;
- use of tables;
- interface-table style;
- use of block diagrams;
- theory-of-operation structure;
- register documentation style;
- explicit timing/behavior discussion;
- use of feature lists and scope;
- separation between behavior and implementation;
- traceability mindset.

The AI **must not copy** from examples:

- number of GPIOs;
- FIFO depth;
- bus protocol;
- register addresses;
- field names;
- reset values;
- clock frequency;
- latency;
- interrupt behavior;
- parameter values;
- architecture choices;
- security mechanisms;
- any other functional decision not supported by project requirements.

---

## 3. Structural pattern to emulate

A mature Digital IP specification commonly has material equivalent to:

```text
Document control
Overview / purpose / scope
Feature summary
System context / block diagram
Parameters and configuration
Clock and reset
Hardware interfaces
Functional description / theory of operation
Modes / states
Timing and performance
Registers / CSRs                 [if applicable]
Interrupts / events / errors     [if applicable]
Corner and illegal cases
Integration constraints
Requirement traceability
Open issues / TBDs
```

This outline is a **repo learning template**, not a claim that every company or standard mandates the exact same headings.

---

## 4. Preferred representation by information type

Use prose only when prose is clearer.

Prefer:

### Signal/interface table

| Signal | Dir | Width | Clock | Reset | Description |
|---|---|---:|---|---|---|

### State-transition table

| Current state | Condition | Action | Next state |

### Priority table

| Priority | Condition | Required behavior |

### Register table

| Offset | Register | Access | Reset | Description |

### Field table

| Bits | Name | Access | Reset | Description / side effect |

### Timing sequence

```text
Cycle N     request accepted
Cycle N+1   internal action
Cycle N+k   externally visible response
```

### Requirement traceability

| Requirement ID | Source | Spec section | Verification target |

---

## 5. Review questions inspired by real HW specs

Before accepting a section, ask:

1. Is the interface viewpoint explicit?
2. Is every width known or parameterized?
3. Which clock samples each input?
4. Which edge changes each state/output?
5. What exactly does reset do?
6. What happens if multiple controls are asserted together?
7. Are minimum/maximum/boundary values defined?
8. What happens on illegal input/state?
9. Is latency defined where consumers depend on it?
10. Could DV write a checker/assertion from this description?
11. Did the author accidentally constrain implementation without need?
12. Was any decision silently imported from a reference IP?

---

## 6. Correct use by AI

When this file is attached, the AI should say internally:

> “These examples teach me **how to document**, not **what this new IP must do**.”

If project requirements conflict with a reference example, **project requirements win**.

If a behavior is absent from project requirements, mark it **TBD** rather than copying the example.

---

## 7. Golden handoff criterion

A Digital IP spec is mature enough for handoff when:

- RTL designer can implement required externally visible behavior without guessing;
- DV engineer can create directed tests/assertions/coverage targets without guessing;
- integration-facing signals, timing, reset and configuration are defined;
- unresolved decisions are visible in a centralized TBD list;
- project requirements can be traced into the spec.

This is a practical engineering criterion used by this repo, not a quotation from OpenTitan/JPL.
