# Interview Plan — Sunday 4 October to Wednesday 7 October 2026

## Objective

Close the highest-risk interview gaps before Wednesday: database indexes, transactions/isolation/locking, Java concurrency, and Spring database integration. Review and practice are more valuable than starting broad new topics.

## Sunday — Database Foundations

### Morning — SQL and Design (2 hours)

- [ ] Review [[05 Databases/SQL/01 SQL Fundamentals]]
- [ ] Practice joins, aggregations, `WHERE` vs `HAVING`, and subqueries
- [ ] Review [[05 Databases/Design/01 Relational Design and Access Patterns]]
- [ ] Write and explain two pagination and N+1 solutions

### Afternoon — Indexes (2 hours)

- [ ] Study [[05 Databases/Indexes/01 Indexes and Query Plans]]
- [ ] Explain B-Tree intuition, selectivity, composite indexes, and leftmost prefix
- [ ] Read three sample `EXPLAIN` plans and identify scan, index, sort, and row estimates

### Evening — Transactions (90 minutes)

- [ ] Review [[05 Databases/Transactions/01 ACID and Transactions]]
- [ ] Review [[05 Databases/Transactions/02 Isolation and Locking]]
- [ ] Create a one-page cheat sheet: ACID, anomalies, isolation levels, optimistic vs pessimistic locking, deadlocks
- [ ] End with 10 minutes of recall without notes

## Monday — Java and Spring

### Morning — Java (2 hours)

- [ ] Review existing Collections, [[03 Java/Collections/02 HashMap]], [[03 Java/Core Java/Generics]], and [[03 Java/Concurrency/Concurrency]]
- [ ] Review [[03 Java/Core Java/OOP and SOLID]] and [[03 Java/Core Java/Exceptions]]
- [ ] Explain `HashMap` collisions/resizing, PECS, checked vs unchecked exceptions, and composition vs inheritance

### Afternoon — Concurrency (90 minutes)

- [ ] Review race conditions, atomicity vs visibility, `volatile`, `synchronized`, locks, executors, and thread pools
- [ ] Explain [[03 Java/Concurrency/CompletableFuture and Reactive Basics]] at a high level
- [ ] Practice two concurrency scenarios: lost update and deadlock

### Evening — Spring Boot (2 hours)

- [ ] Review [[04 Spring/Core/01 IoC and Dependency Injection]]
- [ ] Review [[04 Spring/Boot/01 Spring Boot Configuration]] and [[04 Spring/Boot/02 REST APIs and Error Handling]]
- [ ] Review [[04 Spring/Data JPA/01 JPA Transactions and Fetching]]
- [ ] Explain constructor injection, auto-configuration, DTO validation, `@ControllerAdvice`, `@Transactional`, lazy/eager loading, and N+1

## Tuesday — Mock and Consolidation

### Morning — Targeted Review (90 minutes)

- [ ] Revisit mistakes from Sunday/Monday
- [ ] Re-test indexes, composite indexes, isolation, locking, and transactions from memory
- [ ] Re-test Java Collections, `HashMap`, concurrency, Generics, and exceptions

### Afternoon — Full Mock (60 minutes)

Use this interview structure:

| Section | Time |
|---|---:|
| Database | 25 min |
| Java | 15 min |
| Spring Boot | 10 min |
| Production/troubleshooting | 10 min |

- [ ] Record questions you could not answer clearly
- [ ] Rewrite each weak answer as: definition → example → trade-off

### Evening — Final Gap Closure (60–90 minutes)

- [ ] Review only mock mistakes and the cheat sheet
- [ ] Review [[04 Spring/Boot/03 Production Basics]]
- [ ] Prepare a concise project story and three questions for the interviewer
- [ ] Stop studying at least one hour before sleep

## Wednesday — Interview Day

### 30–45 Minutes Before the Interview

- [ ] Index cheat sheet: selectivity, composite indexes, leftmost prefix, covering index
- [ ] ACID, isolation levels, optimistic vs pessimistic locking, deadlocks
- [ ] Java Collections, `HashMap`, concurrency, and Generics
- [ ] Spring DI, `@Transactional`, REST status codes, and N+1

### Final Rules

- [ ] Do not start new material
- [ ] State assumptions before answering design questions
- [ ] Explain trade-offs and failure modes, not just definitions
- [ ] If unsure, say how you would verify the answer (logs, `EXPLAIN`, metrics, documentation)
- [ ] Stop reviewing and arrive calm and prepared

## Out of Scope Before Wednesday

MongoDB depth, advanced JVM internals, distributed transactions, CAP, CDC, Spring Security, messaging, and reactive programming are deferred unless a mock exposes a specific gap. See the later-depth notes for post-interview study.

```table-of-contents
```
