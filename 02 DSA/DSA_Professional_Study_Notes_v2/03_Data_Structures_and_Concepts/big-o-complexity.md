# Big-O Complexity

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** A language for describing how running time or memory grows as input size increases.

---

## 1. Learn this first — in one minute

### What is Big-O Complexity?

A language for describing how running time or memory grows as input size increases.

### Real-world analogy

If one cashier serves 10 customers today and 1000 tomorrow, you care whether the work grows roughly 100×, 10×, or 1000²×. Big-O describes that growth trend while ignoring constants.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
n=10        n=100
O(1):   1          1
O(logn):~3         ~7
O(n):   10         100
O(n²):  100        10,000
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Use before coding and after coding to judge whether the solution fits constraints.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Constants matter in practice, but growth rate dominates as n becomes large. An O(n²) algorithm can become unusable long before O(n log n).

---

## 5. Step-by-step method

Count dominant loops/recursive work. For sequential blocks add complexities; for nested independent loops multiply. Ignore lower-order terms and constants.

---

## 6. Small example / dry run

Two nested loops over n items → about n² comparisons → O(n²). A loop plus a sort → O(n)+O(n log n)=O(n log n).

---

## 7. Java implementation

```java
// O(n)
for (int x : nums) {
    process(x);
}

// O(n^2)
for (int i=0;i<n;i++)
    for (int j=0;j<n;j++)
        process(i,j);
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
| Time | Depends on algorithm; common classes O(1), O(log n), O(n), O(n log n), O(n²), O(2^n) |
| Extra space | Analyze extra memory separately from input storage |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Calling O(n+n) O(n²).\n- Counting input storage as auxiliary space without saying so.\n- Ignoring recursion depth.

---

## 10. Real interview / real-world examples

- Choosing between brute force and hashing.\n- Deciding whether a solution fits an Infosys coding assessment time limit.

---

## 11. Problems from your roadmap that connect to this

Roadmap Foundations: Java & Complexity.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Big-O Complexity**?

Write your answer here:

> 

