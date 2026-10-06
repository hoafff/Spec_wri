# <IP_NAME> Digital IP Specification

**Version:** <x.y>  
**Status:** Draft / Review / Approved  
**Owner:** <name/team>  
**Last updated:** <date>

---

## 1. Purpose and Scope

### 1.1 Purpose
<TBD>

### 1.2 In scope
- <TBD>

### 1.3 Out of scope
- <TBD>

---

## 2. References and Conventions

### 2.1 References
- <project requirement source>
- <protocol standard>
- <applicable standard>

### 2.2 Conventions
- Signal direction viewpoint: IP/DUT
- Bit numbering: <TBD>
- Endianness: <TBD/N/A>
- Active-low naming convention: <TBD>

---

## 3. Feature Summary

- <feature>
- <feature>

---

## 4. System / Architecture Context

### 4.1 Context diagram
<TBD>

### 4.2 External dependencies
<TBD>

---

## 5. Parameters and Configuration

| Parameter | Type | Default | Legal values | Description | Requirement |
|---|---|---|---|---|---|

---

## 6. Clock and Reset

### 6.1 Clocks

| Clock | Domain | Active edge | Frequency constraints | Description |
|---|---|---|---|---|

### 6.2 Resets

| Reset | Domain | Polarity | Sync/Async | Assertion | Deassertion | Description |
|---|---|---|---|---|---|---|

### 6.3 Reset state

| State/output | Reset value | Requirement |
|---|---|---|

---

## 7. Hardware Interfaces

| Signal | Dir | Width | Clock domain | Reset value | Description | Requirement |
|---|---|---:|---|---|---|---|

For protocol interfaces, define the complete handshake/timing contract.

---

## 8. Functional Behavior

For each function:

### 8.x <FUNCTION>

**Precondition:** <...>  
**Trigger:** <...>  
**Required behavior:** <...>  
**Timing:** <...>  
**Priority:** <...>  
**Observable result:** <...>  
**Requirement IDs:** <...>

Use truth/transition/priority tables where clearer.

---

## 9. Operating Modes / State Machine

N/A unless required.

| State | Entry condition | Behavior | Exit condition | Next state |
|---|---|---|---|---|

---

## 10. Data Handling

<TBD/N/A>

---

## 11. Registers / CSRs

N/A if the block has no software-visible registers.

| Offset | Register | Width | Access | Reset | Description |
|---:|---|---:|---|---|---|

Field details:

| Bits | Field | Access | Reset | Description / side effect |
|---|---|---|---|---|

---

## 12. Interrupts / Events

N/A if not present.

| Event | Trigger | Masking | Clear behavior | Reset behavior | Requirement |
|---|---|---|---|---|---|

---

## 13. Timing and Performance

| Item | Requirement | Source |
|---|---|---|
| Latency | TBD | |
| Throughput | TBD | |
| Backpressure | TBD | |

Do not invent performance numbers.

---

## 14. Error / Illegal Behavior

| Condition | Required behavior | Reporting | Requirement |
|---|---|---|---|

---

## 15. Corner Cases

Explicitly evaluate applicable cases:

- minimum value/configuration;
- maximum value/configuration;
- wrap/overflow;
- underflow;
- full/empty;
- simultaneous operations;
- back-to-back operations;
- reset during operation;
- disabled mode;
- illegal input/state;
- X/Z behavior when relevant.

---

## 16. Integration Constraints

<TBD/N/A>

---

## 17. Requirement Traceability Matrix

| Requirement ID | Type | Source | Spec section | Observable result | Verification target |
|---|---|---|---|---|---|

Type: SOURCE / DERIVED / ASSUMPTION / TBD.

---

## 18. Standard/Profile Compliance Matrix

| Item | Applicable | Section | Status | Reason/Open issue |
|---|---:|---|---|---|

---

## 19. Open Issues / TBD

| TBD ID | Decision needed | Impact | Blocking RTL? | Owner |
|---|---|---|---:|---|

---

## 20. Revision History

| Version | Date | Author | Change |
|---|---|---|---|
