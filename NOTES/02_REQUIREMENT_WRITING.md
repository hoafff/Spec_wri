# Requirement Writing Notes

## Recommended sentence pattern

```text
When <condition/event>,
the <IP/block>
SHALL <observable behavior>
<timing constraint, if required>.
```

Example:

> When `rd_en=1` and `empty=0` are sampled at rising edge N, the FIFO shall make the selected data available on `rd_data` by the specified read-response point.

If that response point is not yet decided, write TBD rather than inventing N+1.

---

## Weak vs stronger

### Weak
> FIFO supports reads.

Problems:
- no trigger;
- no empty behavior;
- no timing;
- no observable contract.

### Stronger
> When a valid read request is accepted while the FIFO is non-empty, one stored entry shall be removed and returned according to the defined read-data timing.

Still requires the read-data timing to be defined elsewhere.

---

## Avoid vague terms

Avoid unless quantified:

- fast;
- quickly;
- normally;
- robust;
- efficient;
- sufficient;
- optimized;
- soon;
- appropriate.

---

## Priority matters

Bad:

> Reset clears the counter. Enable increments the counter.

Missing:

> What if reset and enable are both active?

Better:

| Priority | Condition | Behavior |
|---:|---|---|
| 1 | reset active | reset state |
| 2 | enable active | increment |
| 3 | otherwise | hold |

Only use this table when that priority is actually required by source/architect decision.

---

## Testability check

After writing each functional requirement, ask:

> Can DV create a deterministic pass/fail checker from this requirement?

If not, locate the missing information:

- condition?
- trigger?
- expected value?
- timing?
- priority?
- legal range?
- error behavior?
