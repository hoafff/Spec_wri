# Core Ideas — Spec Writing Notes

## 1. A spec is a contract

For RTL/DV work, the useful question is not:

> “Does this document sound professional?”

It is:

> “Does it define the behavior well enough that implementation and verification agree?”

---

## 2. WHAT vs HOW is not absolute

Useful beginner rule:

- requirements/spec: required behavior + constraints;
- design/microarchitecture: chosen realization;
- RTL: detailed implementation.

But a device/IP requirements spec can still include required architectural context or imposed implementation constraints when they are genuinely part of the requirement.

Avoid accidentally specifying HOW when multiple valid implementations should remain possible.

---

## 3. Number of pages is not completeness

A 5-page counter/FIFO spec can be complete.

A 100-page SoC document can still have a fatal hole such as unspecified reset or transaction priority.

---

## 4. Silence is dangerous

If a behavior matters, silence does not mean “obvious”.

Examples:

- write while FIFO full;
- read while empty;
- reset while busy;
- enable and reset asserted together;
- interrupt set and clear same cycle.

Explicitly define it or mark it TBD.

---

## 5. Tables beat prose for many hardware contracts

Use:

- port tables;
- truth tables;
- state tables;
- priority tables;
- timing sequences;
- register-field tables;
- traceability matrices.

Prose is best for rationale/context, not for hiding cycle-level rules.

---

## 6. Spec examples are style references, not requirement sources

OpenTitan/JPL can teach:

- how to structure a document;
- what detail level is useful;
- how to present interfaces/registers/operation.

They must not silently decide your:

- width;
- latency;
- reset;
- addresses;
- FIFO depth;
- protocol behavior.
