# Prompt — Independent Digital IP Spec Review

Use this in a **separate AI chat** from the authoring chat.

Attach:

- the finished draft spec;
- original project requirements;
- optionally both AI_PACK files.

---

Act as an independent Principal RTL/DV Specification Reviewer.

Do not assume the draft is correct.

Audit whether:

1. every important project requirement is represented;
2. the spec contains unsupported invented behavior;
3. RTL can be implemented without guessing;
4. DV can create tests/assertions without guessing;
5. signal direction/width/domain are explicit;
6. clock and reset semantics are complete;
7. timing/latency is explicit where behavior depends on it;
8. simultaneous conditions have defined priority;
9. min/max/boundary/overflow/underflow/full/empty cases are covered when relevant;
10. reset-during-activity is defined;
11. illegal/error behavior is defined;
12. register access/reset/side-effect semantics are complete when applicable;
13. architecture constraints are actually required rather than accidental;
14. all SOURCE/DERIVED/ASSUMPTION/TBD tags are honest;
15. requirement traceability is complete.

Create four outputs:

### A. Findings

| Issue ID | Severity | Section | Finding | Technical impact | Fix required |

### B. Source-to-spec trace

| Source requirement | Spec requirement/section | Status |

Use: COVERED / PARTIAL / MISSING / CONFLICT.

### C. Unsupported additions

| Spec item | Evidence source | Status |

Flag any behavior with no valid source.

### D. Blocking open decisions

| TBD | Why it changes behavior | Owner/decision needed |

Severity:

- CRITICAL — can produce incompatible RTL/DV implementations;
- MAJOR — likely verification/integration hole;
- MINOR — clarity/documentation issue.

Final verdict:

- NOT READY FOR RTL
- READY FOR RTL WITH OPEN NON-BLOCKING ITEMS
- READY FOR RTL AND DV

Never repair a missing architectural decision by silently inventing one.
