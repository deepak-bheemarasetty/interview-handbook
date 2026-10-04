```table-of-contents
```

## Java Memory Model
1. The Java Memory Model explains how threads see shared memory.
2. It is different from JVM runtime memory areas.
3. Visibility, atomicity, ordering, and happens-before are the main ideas.
4. The JMM is a specification for correct concurrent behavior, not a physical memory layout.

## Core Rules
1. `volatile` helps with visibility and ordering.
2. `synchronized` provides mutual exclusion and visibility guarantees.
3. Instruction reordering can happen unless constrained by the memory model.
4. Happens-before establishes when one action is guaranteed to be visible to another.
5. Atomicity matters for compound operations like incrementing counters.

## Interview Takeaway
1. Separate memory layout from memory visibility.
2. Be precise about what `volatile` does and does not guarantee.
3. Be able to explain happens-before in simple interview language.
