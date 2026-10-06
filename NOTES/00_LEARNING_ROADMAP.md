# Learning Roadmap — Digital IP Specification

## Goal

Learn to convert an incomplete hardware problem statement into a specification that can be handed to RTL and DV.

## 80/20 sequence

### Stage 1 — Learn to separate facts from guesses
Master:

- SOURCE
- DERIVED
- ASSUMPTION
- TBD

If this is wrong, the rest of the spec can look professional but still be false.

### Stage 2 — Interface + clock/reset
For every block, be able to answer:

- What enters/leaves?
- How wide?
- Which clock?
- Which edge?
- What does reset do?

### Stage 3 — Functional contracts
Practice writing:

```text
condition → event → behavior → timing → observable result
```

### Stage 4 — Priority and corner cases
Always ask:

- what if two controls happen together?
- what happens at min/max?
- reset during operation?
- illegal operation?
- overflow/underflow/full/empty?

### Stage 5 — Traceability
Learn:

```text
source requirement
      ↓
IP requirement
      ↓
spec behavior
      ↓
test/assertion/coverage
```

### Stage 6 — Review
Review from two viewpoints:

- RTL: “Can I implement without guessing?”
- DV: “Can I predict pass/fail without guessing?”

---

## Practice order

Recommended blocks:

1. Counter
2. Synchronous FIFO
3. GPIO controller
4. APB register block
5. UART
6. SPI controller
7. DMA-like block

Do not move to a more complex block just because the current spec is short. Move on when the current block has no hidden behavioral ambiguity.
