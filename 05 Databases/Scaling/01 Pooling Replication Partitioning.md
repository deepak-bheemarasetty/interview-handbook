## Overview

Connection pools reuse a bounded set of database connections because opening connections is expensive and databases have finite capacity. Size the pool from measured database capacity and request concurrency—an oversized pool can overload the database.

## Replicas

Read replicas copy data from a primary to serve read traffic or improve availability. Asynchronous replication can lag, so a read immediately after a write may require the primary or a consistency mechanism.

## Partitioning vs Sharding

Partitioning splits one logical table into parts within a database, often by range, list, or hash. Sharding distributes data across independent database nodes. Sharding adds routing, rebalancing, cross-shard query, and operational complexity; use it only after simpler scaling options.

## Interview Takeaway

Pool connections to protect a limited resource, replicas to scale reads with explicit lag trade-offs, and shards only when a single database can no longer meet scale requirements.

```table-of-contents
```
