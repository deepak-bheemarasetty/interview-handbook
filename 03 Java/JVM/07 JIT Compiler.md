```table-of-contents
```

## JIT Compiler
1. The JVM can interpret bytecode first and compile hot code paths later.
2. HotSpot uses runtime profiling to decide what to optimize.
3. The JVM may inline methods and optimize repeated code paths.
4. The exact optimization strategy is an implementation detail.
5. Tiered compilation balances quick startup with deeper optimization later.
6. Dead code elimination and escape analysis can improve performance.

## Interview Takeaway
1. Explain why the JVM does not compile everything up front.
2. Know the basic interpreter vs JIT trade-off.
3. Mention hot methods and tiered compilation as part of adaptive optimization.
