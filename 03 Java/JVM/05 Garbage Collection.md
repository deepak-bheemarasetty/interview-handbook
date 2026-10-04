```table-of-contents
```

## Garbage Collection
1. Garbage collection reclaims heap memory automatically.
2. The JVM uses reachability analysis to decide what can be collected.
3. Strong, soft, weak, and phantom references have different retention behavior.
4. GC algorithms are implementation-specific.
5. Objects are not explicitly freed by application code.

## Common GC Ideas
1. Marking finds live objects.
2. Sweeping removes unreachable objects.
3. Compacting reduces fragmentation.
4. Copying moves live objects to a new space.
5. Generational GC treats young and old objects differently.
6. Minor GC usually refers to young-generation collection.
7. Major GC often refers to old-generation collection, though the exact meaning can vary by collector.
8. Full GC typically means a broader collection cycle and is usually more expensive.

## Reference Types
1. Strong references keep objects reachable in the normal way.
2. Soft references are useful for memory-sensitive caches.
3. Weak references allow collection when no strong references remain.
4. Phantom references support advanced cleanup coordination.

## Modern Garbage Collectors
1. Serial GC is a simple single-threaded collector.
2. Parallel GC uses multiple threads to improve throughput.
3. G1 GC is designed to provide predictable pause times on large heaps.
4. ZGC focuses on very low pause times.
5. Shenandoah also focuses on low-pause garbage collection.
6. Choosing a collector depends on latency, throughput, heap size, and application goals.

## Interview Takeaway
1. Focus on why GC exists and how reachability works.
2. Keep collector internals at a high level unless the interviewer asks deeper questions.
3. Be able to name the common collectors and their high-level trade-offs.
