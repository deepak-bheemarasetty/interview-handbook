```table-of-contents
```

## Object Lifecycle
1. Objects are created on the heap.
2. An object becomes live or dead based on reachability.
3. If an object is no longer reachable, it becomes eligible for garbage collection.
4. Java does not require explicit object deallocation.
5. Finalization should not be relied on for cleanup.
6. Object identity and state are represented through references and the object header in JVM implementations.

## Object Header
1. The object header stores JVM-specific metadata about the object.
2. Common header data may include lock state, hash code information, and class pointer details.
3. The exact header layout is JVM implementation specific.

## Object Thinking
1. Object creation, reachability, and cleanup are controlled by the JVM.
2. Escape analysis can help the JVM optimize allocation decisions.
3. Stack allocation can sometimes be used for objects that do not escape a method.

## Interview Takeaway
1. Know the difference between object creation and object eligibility for GC.
2. Be careful not to overstate what finalization can do.
3. Mention escape analysis and stack-vs-heap allocation as JVM optimizations, not guarantees.
