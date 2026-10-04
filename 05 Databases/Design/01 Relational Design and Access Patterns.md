## Overview

Relational design starts with correct relationships and constraints, then adapts read paths carefully as evidence demands.

## Keys and Cardinality

| Relationship | Usual implementation |
|---|---|
| One-to-one | Foreign key with a unique constraint |
| One-to-many | Foreign key on the many-side |
| Many-to-many | Join table with two foreign keys, usually a composite unique key |

Primary keys identify rows; foreign keys enforce that a referenced row exists. Add indexes for foreign-key lookup and real query patterns.

## Normalization and Denormalization

Normalization reduces duplication and update anomalies by storing each fact once. Denormalize deliberately for proven read bottlenecks, accepting extra storage and a synchronization/update strategy. It is a performance trade-off, not a default.

## Pagination

Offset pagination (`LIMIT ... OFFSET`) is simple but becomes slower and less stable as offsets grow. Keyset/cursor pagination uses a deterministic, indexed order such as `(created_at, id)` and a cursor from the last row; it scales better for deep traversal.

## N+1 Query Problem

N+1 happens when code loads a list, then runs one additional query per item for related data. Detect it in SQL logs/traces. Fix with a suitable join/fetch join, batch fetching, projection, or a query designed for the screen—while avoiding an accidental Cartesian explosion.

## Interview Takeaway

Normalize for integrity first; denormalize only with an explicit consistency plan. For large lists, favor keyset pagination and index the order used.

```table-of-contents
```
