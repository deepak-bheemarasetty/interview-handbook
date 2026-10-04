# Quickselect

> **Classification:** Algorithm  
> **Purpose:** Finds the kth smallest/largest element using partitioning like quicksort without fully sorting both sides.

---

## 1. Learn this first — in one minute

### What is Quickselect?

Finds the kth smallest/largest element using partitioning like quicksort without fully sorting both sides.

### Real-world analogy

If you only need the 10th cheapest item, partition around a pivot and keep working only in the side containing rank 10 instead of sorting every item.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[7 2 9 4 1 5]
pivot=5
[2 4 1] 5 [7 9]
          ^
if k=3 -> pivot is answer
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Kth smallest/largest; only one rank needed; average linear time acceptable.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

After partition, pivot's final rank is known. Only one side can contain the desired rank, so discard the other side.

---

## 5. Step-by-step method

Partition around pivot. Compare pivot index with target index. Recurse/iterate only into the relevant side.

---

## 6. Small example / dry run

After pivot 5, values less than 5 are left and larger values right. If target rank equals pivot position, stop.

---

## 7. Java implementation

```java
// Conceptual iterative form
int l = 0, r = a.length - 1;
while (l <= r) {
    int p = partition(a, l, r);
    if (p == k) return a[p];
    if (p < k) l = p + 1;
    else r = p - 1;
}
throw new IllegalArgumentException();
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
| Time | O(n) average; O(n²) worst |
| Extra space | O(1) auxiliary iterative |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Confusing kth largest with kth smallest index.\n- Ignoring worst-case pivot behavior.

---

## 10. Real interview / real-world examples

- Find median.\n- Find top salary threshold without full sorting.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Kth Largest Element.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Quickselect**?

Write your answer here:

> 

