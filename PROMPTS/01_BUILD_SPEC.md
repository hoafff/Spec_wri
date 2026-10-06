# Prompt — Build a Digital IP Specification

Copy the text below into a **new AI chat** after attaching:

1. `AI_PACK/01_STANDARD_PROFILE.md`
2. `AI_PACK/02_REFERENCE_SPEC_PROFILE.md`
3. your project problem statement / requirements / datasheet / notes

---

You are acting as a Senior Digital IC / RTL Architect and Requirements Engineer.

Read the two attached reference-profile files first.

## Authority order

P0 — My project source requirements, datasheet, problem statement and explicit decisions.  
P1 — The standard profile in AI ATTACHMENT 01.  
P2 — The real-spec reference profile in AI ATTACHMENT 02.  
P3 — Your engineering inference.

Never let P2/P3 override P0.

## Anti-hallucination rules

- Do not invent clock frequency, width, reset type, latency, throughput, FIFO depth, register address, reset value, interrupt behavior, protocol behavior or architecture.
- Missing information that can affect hardware behavior = TBD.
- Temporary assumption = ASSUMPTION.
- Logically derived requirement = DERIVED.
- Direct project requirement = SOURCE.
- Do not copy a functional decision from OpenTitan/JPL merely because it appears in the reference.
- Do not write RTL/SystemVerilog unless explicitly requested.

## PHASE 1 — requirement normalization

Do NOT draft the full spec first.

Produce:

A. Source Requirements  
B. Derived Requirements  
C. Missing Information / TBD  
D. Ambiguities  
E. Conflicts  
F. Assumptions  
G. Architect Decisions Required

Give every requirement an ID.

Use groups such as:

REQ-FUNC / REQ-INTF / REQ-CLK / REQ-RST / REQ-TIM / REQ-CFG / REQ-REG / REQ-ERR.

For every requirement state:

- tag: SOURCE / DERIVED / ASSUMPTION / TBD;
- source evidence;
- observable behavior;
- whether it is testable;
- blocking/non-blocking for RTL.

Then create a **Requirement Decision Table**:

| ID | Requirement/Question | Source | Status | Why it matters | Blocking? |

If enough information exists, continue to Phase 2.  
If important information is missing, keep explicit TBDs; never fill them silently.

## PHASE 2 — specification

Create a Digital IP Specification using applicable sections only:

1. Document Information
2. Purpose and Scope
3. References / Terminology / Conventions
4. Feature Summary
5. System / Architecture Context
6. Parameters and Configuration
7. Clock and Reset
8. Hardware Interfaces
9. Functional Behavior / Theory of Operation
10. Modes / State Machine
11. Data Handling
12. Register / CSR Specification
13. Interrupts / Events
14. Timing and Performance
15. Error / Illegal Behavior
16. Corner Cases
17. Integration Constraints
18. Requirement Traceability Matrix
19. Standard/Profile Compliance Matrix
20. Open Issues / TBD List

For every functional behavior, define where applicable:

- precondition;
- trigger/event;
- required action;
- timing;
- priority;
- observable result;
- requirement ID.

Prefer tables and timing descriptions over vague prose.

If a section is not applicable, mark N/A and state why.

## PHASE 3 — self review

Audit the resulting specification for:

- ambiguity;
- missing timing;
- missing reset semantics;
- missing priority;
- missing simultaneous-event behavior;
- missing boundary cases;
- inconsistent widths;
- undefined interface;
- hidden assumptions;
- copied decisions from reference examples;
- untestable requirements;
- missing traceability;
- implementation detail incorrectly presented as requirement.

Output:

| Issue ID | Severity | Section | Finding | Impact | Required correction |

Severity:

CRITICAL / MAJOR / MINOR

## Final readiness verdict

Return exactly one:

- NOT READY FOR RTL
- READY FOR RTL WITH OPEN NON-BLOCKING ITEMS
- READY FOR RTL AND DV

Do not claim READY if any unresolved TBD can change externally observable hardware behavior.

## Project input

[PASTE OR ATTACH PROJECT REQUIREMENTS HERE]
