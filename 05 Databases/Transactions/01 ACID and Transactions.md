## Overview

A transaction groups reads and writes into one unit of work. `COMMIT` makes its effects durable; `ROLLBACK` discards its uncommitted effects.

| Property | Meaning |
|---|---|
| Atomicity | All changes succeed together or none do |
| Consistency | A committed transaction preserves declared database rules/invariants |
| Isolation | Concurrent transactions behave with controlled interaction |
| Durability | Once committed, changes survive a crash according to the database guarantee |

## Consistency Is Not Validation

The database can enforce constraints, but application code must still define and validate business rules. ACID consistency means a transaction moves the database between valid states under the rules actually encoded.

## Practical Boundary

Keep transactions short: acquire data, validate, write, commit. Avoid slow remote calls or user interaction inside one because locks and connections may be held longer.

## Interview Takeaway

ACID does not mean every transaction is fully serializable. Isolation is configurable and must balance correctness with contention and throughput.

```table-of-contents
```
