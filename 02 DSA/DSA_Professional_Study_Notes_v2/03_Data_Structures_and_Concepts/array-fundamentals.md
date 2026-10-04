# Array Fundamentals

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** The basic operations and invariants of contiguous indexed storage: traversal, min/max, reverse, rotation, prefix/suffix.

---

## 1. Learn this first — in one minute

### What is Array Fundamentals?

The basic operations and invariants of contiguous indexed storage: traversal, min/max, reverse, rotation, prefix/suffix.

### Real-world analogy

A numbered row of lockers: each position is directly reachable by index, but inserting in the middle requires shifting many lockers.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
index:  0  1  2  3
array: [10 20 30 40]
        ↑       ↑
      O(1) random access
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Direct indexed access, traversal, in-place transformations.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Arrays trade cheap random access for expensive middle insertion/deletion. Many DSA patterns build on this property.

---

## 5. Step-by-step method

Traverse with indices; use two pointers for reversal; use temporary variables for swaps; use modulo for rotations; use prefix/suffix arrays for cumulative relationships.

---

## 6. Small example / dry run

Reverse `[1,2,3,4]`: swap 1↔4, then 2↔3 → `[4,3,2,1]`.

---

## 7. Java implementation

```java
for (int i=0; i<a.length; i++) {
    // access a[i] in O(1)
}

int l=0,r=a.length-1;
while(l<r){
    int t=a[l]; a[l]=a[r]; a[r]=t;
    l++; r--;
}
```

### Code walkthrough

- Identify the **state** being maintained.
- Identify the **invariant** that remains true.
- Identify exactly when a value/pointer/state changes.
- Check what happens at the first and last element.

---

## 8. Complexity

| Measure | Cost |
|---|---|
| Time | Index access O(1); traversal O(n); insertion/deletion in middle O(n) |
| Extra space | Usually O(1) auxiliary for in-place operations |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Off-by-one indices.\n- Confusing array length with last index.\n- Accidentally using O(n) extra memory.

---

## 10. Real interview / real-world examples

- Fixed-size tables.\n- Sensor readings by minute.\n- Scores stored by student index.

---

## 11. Problems from your roadmap that connect to this

Roadmap Array Fundamentals.

---

## 12. How to know you actually learned it

Before moving on, you should be able to:

- [ ] Explain the idea without looking at code.
- [ ] Draw the visual from memory.
- [ ] Explain the invariant in one sentence.
- [ ] Dry-run a small input manually.
- [ ] Write the Java solution from scratch.
- [ ] State time and space complexity and justify them.
- [ ] Explain why a brute-force approach is slower.
- [ ] Handle at least two edge cases.
- [ ] Solve a new problem where the pattern is not explicitly named.

### Self-test

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Array Fundamentals**?

Write your answer here:

> 

