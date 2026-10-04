## Overview

Concurrent transactions can interfere unless isolation controls what each can observe and modify. Engines use locks, MVCC snapshots, or both; exact behavior varies by database.

## Common Anomalies

| Anomaly | Example |
|---|---|
| Lost update | Two requests read 10, each writes 11; one increment disappears |
| Dirty read | A transaction sees another's uncommitted change that later rolls back |
| Non-repeatable read | Re-reading one row returns a different committed value |
| Phantom read | Re-running a predicate returns new/deleted matching rows |

## Isolation Levels

| Level | Typical protection |
|---|---|
| Read Uncommitted | Few guarantees; may allow dirty reads where supported |
| Read Committed | Prevents dirty reads; repeated reads may differ |
| Repeatable Read | Repeated row reads stay stable; phantom behavior is engine-specific |
| Serializable | Equivalent to some serial order; may block, abort, or retry transactions |

Always describe both the SQL level and the database implementation; vendor semantics differ.

## Optimistic vs Pessimistic Locking

Optimistic locking reads normally, then updates only if a version still matches. It works well when conflicts are uncommon and callers can retry.

```sql
UPDATE inventory SET quantity = ?, version = version + 1
WHERE id = ? AND version = ?;
```

Pessimistic locking obtains a lock before changing data (for example, `SELECT ... FOR UPDATE`). It suits expected contention but can reduce concurrency and contribute to deadlocks.

## Deadlocks

A deadlock is a cycle of waiting transactions. The database normally aborts one victim. Prevent them by keeping transactions short, acquiring resources in a consistent order, indexing predicates, and retrying safe aborted work.

## Interview Takeaway

Choose optimistic locking for rare conflicts and pessimistic locking for short, high-contention critical sections. Every robust design also has a deadlock/retry strategy.

```table-of-contents
```
