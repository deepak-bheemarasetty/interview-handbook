## Overview

Spring Data JPA commonly separates controller, service, and repository responsibilities. The service coordinates a use case and is usually the transaction boundary; repositories provide persistence access.

## @Transactional

`@Transactional` creates/interacts with a transaction through Spring's proxy mechanism. By default, runtime exceptions trigger rollback; checked exceptions generally do not unless configured. A call from one method to another on the same object bypasses the proxy, so self-invocation may not apply transactional behavior.

Keep the transaction focused on database work. Long transactions retain connections and may hold locks.

## Lazy vs Eager Loading

Lazy loading defers a relationship query until accessed; eager loading retrieves it immediately. Neither is universally right. Eager loading can load far too much; lazy loading outside an active persistence context can fail and can create N+1 queries.

## Preventing N+1

For each endpoint, deliberately choose fetch joins, entity graphs, batch fetching, or DTO projections. Inspect generated SQL; do not fix N+1 by marking every relationship eager.

## JDBC and Connection Pools

JPA ultimately uses JDBC to communicate with the database. A `DataSource` normally supplies pooled JDBC connections; release them promptly by ending transactions.

## Interview Takeaway

Put transaction boundaries around service-level use cases, understand proxy/self-invocation behavior, and treat fetching as a per-query design choice.

```table-of-contents
```
