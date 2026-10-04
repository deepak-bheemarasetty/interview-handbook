## Overview

Production services need to remain correct when dependencies are slow, unavailable, or receive duplicate messages.

## Caching

Cache data that is expensive to compute/read and tolerates staleness. Define key, TTL, invalidation/update strategy, eviction behavior, and stampede protection. A cache is an optimization, not the source of truth unless explicitly designed as one.

## Messaging

Kafka and similar systems decouple producers and consumers through durable records. Design for duplicate delivery with idempotent consumers, preserve ordering only within the relevant partition/key, and use a transactional outbox to avoid the database-write/publish gap.

## Resilience Patterns

Set timeouts on every remote call. Use bounded retries only for transient, idempotent work and add jitter to avoid retry storms. Circuit breakers stop repeatedly calling a failing dependency. Bulkheads bound the damage a dependency can cause. These patterns complement, rather than replace, monitoring and capacity planning.

## Interview Takeaway

Start with timeouts, then make retries safe and bounded. Pair asynchronous messaging with idempotency and a reliable event-publication pattern.

```table-of-contents
```
