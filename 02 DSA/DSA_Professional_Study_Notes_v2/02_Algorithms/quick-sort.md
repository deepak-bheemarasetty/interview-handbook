# Quick Sort

> **Classification:** Algorithm  
> **Purpose:** A divide-and-conquer sort that partitions around a pivot, then recursively sorts the two sides.

---

## 1. Learn this first — in one minute

### What is Quick Sort?

A divide-and-conquer sort that partitions around a pivot, then recursively sorts the two sides.

### Real-world analogy

Pick one person as a divider; send shorter people to one side and taller people to the other, then repeat inside each group.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[7 2 9 4 1]
pivot=1
[] [1] [7 2 9 4]

next pivot=4
[2] [4] [7 9]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Fast in-place average-case sorting; partition-based problems; Quickselect.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Partition guarantees that the pivot is in its final relative position: every left element satisfies the chosen relation and every right element satisfies the opposite.

---

## 5. Step-by-step method

Choose pivot. Partition. Recursively sort left and right partitions. Pivot itself is excluded from recursion.

---

## 6. Small example / dry run

For `[7,2,9,4,1]` pivot 1 ends at index 0. Sorting the remaining suffix repeats the process.

---

## 7. Java implementation

```java
static void quickSort(int[] a, int l, int r) {
    if (l >= r) return;

    int p = partition(a, l, r);
    quickSort(a, l, p - 1);
    quickSort(a, p + 1, r);
}

static int partition(int[] a, int l, int r) {
    int pivot = a[r], i = l;

    for (int j = l; j < r; j++) {
        if (a[j] <= pivot) {
            int t=a[i]; a[i]=a[j]; a[j]=t;
            i++;
        }
    }

    int t=a[i]; a[i]=a[r]; a[r]=t;
    return i;
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
| Time | O(n log n) average; O(n²) worst |
| Extra space | O(log n) average recursion |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Bad pivot choices on sorted input.\n- Partition off-by-one errors.\n- Forgetting worst-case behavior.

---

## 10. Real interview / real-world examples

- In-memory sorting where average performance matters.\n- Basis for selection algorithms.

---

## 11. Problems from your roadmap that connect to this

Roadmap Sorting; Pattern Divide & Conquer.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Quick Sort**?

Write your answer here:

> 

