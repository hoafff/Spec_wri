# Checklist — Is the Spec Ready for RTL/DV?

Use this before declaring a Digital IP specification complete.

## A. Scope and context

- [ ] Purpose is clear.
- [ ] In-scope behavior is defined.
- [ ] Out-of-scope behavior is stated.
- [ ] External dependencies are known.
- [ ] Interface viewpoint is explicit.

## B. Clock and reset

- [ ] Every clock domain is identified.
- [ ] Active clock edge is identified.
- [ ] Frequency constraints are specified if required.
- [ ] Reset polarity is defined.
- [ ] Synchronous/asynchronous semantics are defined.
- [ ] Assertion behavior is defined.
- [ ] Deassertion behavior is defined.
- [ ] Reset state of externally visible state is defined.

## C. Interfaces

- [ ] Every signal/interface has direction.
- [ ] Width is defined or parameterized.
- [ ] Clock domain is known.
- [ ] Handshake semantics are complete.
- [ ] Valid-data timing is known.
- [ ] Backpressure behavior is known where applicable.

## D. Functional behavior

- [ ] Normal operation is defined.
- [ ] Each operation has a trigger.
- [ ] Observable result is defined.
- [ ] Timing/latency is defined where relevant.
- [ ] Priority is defined for competing conditions.
- [ ] Operating modes are defined.
- [ ] State transitions are defined where applicable.

## E. Boundary / corner cases

- [ ] Minimum configuration/value checked.
- [ ] Maximum configuration/value checked.
- [ ] Overflow/wrap defined.
- [ ] Underflow defined.
- [ ] Full/empty defined where applicable.
- [ ] Simultaneous events defined.
- [ ] Back-to-back operations defined.
- [ ] Reset during activity defined.
- [ ] Disabled behavior defined.
- [ ] Illegal request/state behavior defined.

## F. Registers / interrupts

- [ ] Register offsets are defined if applicable.
- [ ] Access types are defined.
- [ ] Reset values are defined.
- [ ] Side effects are defined.
- [ ] Reserved bits behavior is defined.
- [ ] Interrupt trigger semantics are defined.
- [ ] Mask/clear/reset behavior is defined.

## G. Requirement quality

- [ ] Requirements have IDs.
- [ ] SOURCE vs DERIVED vs ASSUMPTION vs TBD is visible.
- [ ] No requirement relies on vague words without measurable meaning.
- [ ] No unsupported implementation choice has been promoted to requirement.
- [ ] No behavior was copied from an example without a project source.
- [ ] Requirements are testable or explicitly justified otherwise.

## H. Traceability

- [ ] Source requirement → spec requirement exists.
- [ ] Spec requirement → section exists.
- [ ] Functional requirement → verification target exists.
- [ ] No unexplained orphan requirement exists.

## I. Blocking-TBD gate

Ask:

> Can two competent RTL designers read this spec and produce externally incompatible behavior while both believing they complied?

If **yes**, the spec is not ready.

Ask:

> Can RTL and DV disagree about expected behavior because the document is silent?

If **yes**, the spec is not ready.

### Verdict

- **NOT READY FOR RTL** — blocking behavior decisions remain.
- **READY FOR RTL WITH OPEN NON-BLOCKING ITEMS** — open items do not affect required observable behavior.
- **READY FOR RTL AND DV** — behavior, interfaces, timing, reset and traceability are sufficiently defined.
