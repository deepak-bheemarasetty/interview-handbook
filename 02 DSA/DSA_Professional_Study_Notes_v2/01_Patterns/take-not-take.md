# Take / Not-Take

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A DP/backtracking modeling pattern where each item creates two decisions: include it or exclude it.

---

## 1. Learn this first — in one minute

### What is Take / Not-Take?

A DP/backtracking modeling pattern where each item creates two decisions: include it or exclude it.

### Real-world analogy

Packing a bag: for each object, either put it in or leave it out.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
          item i
          /    \
       TAKE   SKIP
        /        \
   remaining   remaining
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Subset, knapsack, partition, subsequence, choose-or-skip.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The decision tree has two branches per item. DP merges branches that reach the same state instead of recomputing them.

---

## 5. Step-by-step method

Define index + resource/state. Transition to `(i+1, state after take)` and `(i+1, same state after skip)`. Choose max/min/count/boolean according to the problem.

---

## 6. Small example / dry run

For `[2,3]`, subset sums branch: skip 2 or take 2; then each branch skips/takes 3.

---

## 7. Java implementation

```java
// conceptual recurrence
// solve(i, state) = combine(
//     solve(i+1, take(state, nums[i])),
//     solve(i+1, state)
// );
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
| Time | Naive O(2^n); DP often reduces to polynomial state count |
| Extra space | Depends on state table/recursion |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Reusing an item accidentally.\n- Missing the resource dimension.

---

## 10. Real interview / real-world examples

- Selecting projects under budget.\n- Subset sum.

---

## 11. Problems from your roadmap that connect to this

Roadmap Subsequence DP and Knapsack/Partition.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Take / Not-Take**?

Write your answer here:

> 

