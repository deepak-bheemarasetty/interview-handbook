```table-of-contents
```

## JVM Performance
1. Heap size affects memory pressure and GC behavior.
2. Stack size affects recursion depth and thread footprint.
3. `OutOfMemoryError` and `StackOverflowError` are important JVM failures.
4. JVM tools like `jcmd`, `jstack`, `jmap`, and `jconsole` help diagnose problems.
5. GC logs help explain allocation and pause behavior.
6. Memory leaks can still happen in Java when references are retained unintentionally.
7. Monitoring is part of performance tuning, not just debugging.

## Interview Takeaway
1. Be able to connect memory sizing with runtime behavior.
2. Know the basic purpose of the most common JVM diagnostic tools.
3. Call out that tuning is a trade-off between latency, throughput, and memory use.
