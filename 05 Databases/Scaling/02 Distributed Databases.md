## Overview

Distributed databases must make trade-offs across independent machines, partial failures, and network delay.

## Replication and Consensus

Replication copies data for availability and read scale. Consensus protocols coordinate a group on an ordered log/leader despite failures; they support strongly coordinated systems but add latency and operational complexity.

## Distributed Transactions

Two-phase commit coordinates an atomic outcome across participants but can block when the coordinator fails. In many services, use a local transaction plus an outbox, idempotent consumers, retries, and compensating actions rather than one global transaction.

## CAP and Consistency

During a network partition, a distributed system cannot guarantee both linearizable consistency and availability for every request. CAP is about behavior *during partitions*, not a permanent three-way slider. Consistency models range from strong/linearizable reads to eventual and causal forms; choose based on product invariants.

## CDC and Scaling Patterns

Change Data Capture streams committed database changes to other systems for search indexes, analytics, or events. Treat delivery as at-least-once unless guaranteed otherwise: consumers must be idempotent. Common scaling sequence: good schema/indexes → caching/read replicas → partitioning → sharding only when needed.

## Interview Takeaway

Name the invariant first, then choose the consistency, transaction, and scaling mechanism that preserves it under failure.

```table-of-contents
```
