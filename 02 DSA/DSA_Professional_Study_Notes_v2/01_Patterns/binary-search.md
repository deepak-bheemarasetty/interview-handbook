# Binary Search

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A search pattern that repeatedly halves a search space using a monotonic ordering or yes/no predicate.

---

## 1. Learn this first — in one minute

### What is Binary Search?

A search pattern that repeatedly halves a search space using a monotonic ordering or yes/no predicate.

### Real-world analogy

Finding a word in a dictionary: open near the middle. If the word comes later alphabetically, throw away the entire first half.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[1 3 5 7 9 11 13]
 L       M       R
         7

target = 11
7 < 11 -> discard left half

[9 11 13]
 L  M   R
    ↑ found
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Sorted data, first/last occurrence, lower/upper bound, rotated sorted arrays, or a numeric answer where feasibility changes only once.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

One comparison gives enough information to discard half the candidates. This is possible only because the remaining search space has structure.

---

## 5. Step-by-step method

1. Define the search interval. 2. Compute mid safely. 3. Decide which half can still contain the answer. 4. Preserve the interval invariant. 5. Stop when the boundary is reached.

---

## 6. Small example / dry run

Search 11 in `[1,3,5,7,9,11,13]`: middle 7 is too small → search right. Middle 11 → found.

---

## 7. Java implementation

```java
int l = 0, r = nums.length - 1;

while (l <= r) {
    int m = l + (r - l) / 2;

    if (nums[m] == target) return m;
    if (nums[m] < target) l = m + 1;
    else r = m - 1;
}
return -1;
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
| Time | O(log n) for a fixed-size ordered search space |
| Extra space | O(1) iterative |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Mixing `[l,r]` with `[l,r)` conventions.\n- Infinite loops from incorrect pointer updates.\n- Using binary search without monotonicity.\n- Overflow from `(l+r)/2` in languages where integers can overflow.

---

## 10. Real interview / real-world examples

- Dictionary lookup.\n- Finding a minimum machine speed that completes work on time.\n- Searching a sorted database index.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Binary Search, First and Last Position, Search in Rotated Sorted Array, Koko Eating Bananas.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Binary Search**?

Write your answer here:

> 

