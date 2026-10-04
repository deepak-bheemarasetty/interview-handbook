## Overview

`CompletableFuture` composes asynchronous stages without manually coordinating callbacks. Reactive programming models asynchronous streams with backpressure; it is useful when the whole request path is non-blocking, not as a default replacement for ordinary code.

## CompletableFuture

Use `thenApply` for a synchronous transformation, `thenCompose` when a stage returns another future, and `thenCombine` to combine independent futures. Supply an explicit, bounded executor for blocking work instead of accidentally consuming the shared common pool.

```java
CompletableFuture<User> user = findUser(id);
CompletableFuture<Profile> profile = user.thenCompose(u -> findProfile(u.id()));
```

Handle failure deliberately with `exceptionally`, `handle`, or `whenComplete`. Do not block with `get()`/`join()` inside a request path unless there is a clear boundary and capacity plan.

## Reactive Basics

Reactive Streams coordinate a publisher, subscriber, subscription, and demand. Backpressure lets a consumer signal how much it can handle. Blocking calls on an event-loop thread undermine the model; isolate them on appropriate schedulers or use conventional blocking infrastructure.

## Interview Takeaway

Use futures to compose independent async work and reactive streams for end-to-end high-concurrency streaming/non-blocking workflows. Neither makes blocking I/O disappear.

```table-of-contents
```
