## Overview

An index is an auxiliary data structure that trades storage and write work for faster reads. Most relational indexes are B-Trees, which keep keys ordered and make point lookups and ranges efficient.

## B-Tree Intuition

A B-Tree has high fan-out, so a shallow tree can locate a key with few page reads. Ordered leaves also support range scans and ordered traversal. An index is useful only when reading fewer pages than a table scan is likely to cost.

## Selectivity and Composite Indexes

Selectivity is how strongly a predicate narrows rows. A composite index `(tenant_id, created_at)` supports lookups by `tenant_id`, or `tenant_id` plus a `created_at` range. It generally does **not** efficiently support a query solely by `created_at`: this is the leftmost-prefix rule.

Index column order should reflect equality predicates first, then range/sort needs, and the actual workload. Validate it with the planner; there is no universal ordering rule.

## Covering Indexes

When the index contains every column needed by a query, the engine may answer from index pages without fetching table rows. This can reduce I/O, but wider indexes cost more memory and write maintenance.

## Reading EXPLAIN

Check the access path (scan vs index), estimated and actual rows when available, joins, sort/hash operations, and whether estimates are badly wrong. A full table scan is not automatically bad: it can be cheapest when most rows are needed.

## Write Cost

`INSERT`, `UPDATE`, and `DELETE` must also maintain affected indexes. Too many or overly wide indexes slow writes and increase storage; index measured query patterns, not every column.

## Interview Takeaway

An index helps by reducing page reads, not because it makes every query O(log n). Explain selectivity, leftmost prefix, covering indexes, and write trade-offs together.

```table-of-contents
```
