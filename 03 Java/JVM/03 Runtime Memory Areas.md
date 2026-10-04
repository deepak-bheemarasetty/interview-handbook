```table-of-contents
```

## Runtime Memory Areas
1. The JVM defines shared and thread-local runtime data areas.
2. Shared areas are visible to all threads.
3. Thread-local areas belong to each individual thread.
4. The JVM specification describes these areas abstractly; implementations may organize them differently.

## Shared Areas
1. The heap stores objects and arrays.
2. The method area stores class-level metadata, runtime constants, and method code.
3. The heap is automatically managed and can throw `OutOfMemoryError` if memory is exhausted.
4. The runtime constant pool belongs to class-level storage.
5. Metaspace is the modern HotSpot implementation area for class metadata.

## Thread-Local Areas
1. The JVM stack stores method frames.
2. Each thread has its own program counter register.
3. Each thread has its own native method stack.
4. Stack frames contain local variables and operand stacks.
5. A stack frame is created for each method invocation and removed when the method completes.

## Object Allocation Flow
1. Objects and arrays are usually allocated on the heap.
2. Escape analysis may let the JVM optimize some allocations.
3. The exact allocation strategy is an implementation detail.

## Interview Takeaway
1. Be able to separate shared memory from per-thread memory.
2. Know what lives on the heap versus in a stack frame.
3. Remember that the method area is conceptual in the spec, while Metaspace is the modern HotSpot realization.
