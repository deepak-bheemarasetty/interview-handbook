## Overview

SQL is a declarative language: specify the result, and the database chooses an execution plan. Conceptually, filter rows first, then group, filter groups, project, sort, and limit.

## Core Clauses

| Clause | Purpose |
|---|---|
| `SELECT` | Choose columns or expressions to return |
| `WHERE` | Filter individual rows before grouping |
| `GROUP BY` | Form groups for aggregates such as `COUNT` and `SUM` |
| `HAVING` | Filter groups after aggregation |
| `ORDER BY` | Sort the final result |

```sql
SELECT customer_id, COUNT(*) AS order_count
FROM orders
WHERE created_at >= DATE '2026-01-01'
GROUP BY customer_id
HAVING COUNT(*) >= 3
ORDER BY order_count DESC;
```

## Joins

`INNER JOIN` returns matching pairs. `LEFT JOIN` preserves every left-side row and supplies `NULL` for absent right-side matches. Use `LEFT JOIN` when absence itself matters. Be alert to one-to-many joins multiplying rows.

## Subqueries

Use a subquery for a derived value/set; prefer `EXISTS` when testing whether a related row exists because it expresses intent and can stop after the first match.

## Interview Takeaway

The key distinction is `WHERE` filters rows while `HAVING` filters aggregated groups. Choose join type from the required semantics, not habit.

```table-of-contents
```
