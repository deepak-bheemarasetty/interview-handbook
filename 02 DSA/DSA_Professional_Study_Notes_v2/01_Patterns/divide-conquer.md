# Divide & Conquer

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A strategy that divides a problem into smaller independent subproblems, solves them recursively, and combines their answers.

---

## 1. Learn this first — in one minute

### What is Divide & Conquer?

A strategy that divides a problem into smaller independent subproblems, solves them recursively, and combines their answers.

### Real-world analogy

Sorting a huge pile of documents by splitting it into smaller piles, sorting each pile, then merging the sorted piles.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[8 3 5 1 7 2]
      /      \
[8 3 5]    [1 7 2]
  / \         / \
...           ...

solve halves -> combine
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Independent halves; recursive structure; merge/combine step is manageable; recurrence analysis.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If a large problem can be broken into smaller independent versions of the same problem, recursion handles the smaller versions and a combine operation produces the full answer.

---

## 5. Step-by-step method

1. Define base case. 2. Split. 3. Recursively solve each half. 4. Combine. 5. Analyze the recurrence.

---

## 6. Small example / dry run

Merge sort splits `[8,3,5,1]` into `[8,3]` and `[5,1]`, sorts each, then merges `[3,8]` and `[1,5]` into `[1,3,5,8]`.

---

## 7. Java implementation

```java
void solve(int l, int r) {
    if (l >= r) return;

    int mid = l + (r - l) / 2;
    solve(l, mid);
    solve(mid + 1, r);

    combine(l, mid, r);
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
| Time | Depends on recurrence; merge sort is O(n log n) |
| Extra space | Depends on recursion and combine storage |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using divide-and-conquer when subproblems overlap heavily; DP may be better.\n- Forgetting the combine step's cost.\n- Incorrect base case.

---

## 10. Real interview / real-world examples

- Merge sorting records.\n- Binary search.\n- Large numerical computations split across independent chunks.

---

## 11. Problems from your roadmap that connect to this

Pattern sheet Divide & Conquer; roadmap Sorting and Advanced algorithms.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Divide & Conquer**?

Write your answer here:

> 

