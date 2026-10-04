# Merge Sort

> **Classification:** Algorithm  
> **Purpose:** A stable divide-and-conquer sorting algorithm that recursively sorts halves and merges them.

---

## 1. Learn this first — in one minute

### What is Merge Sort?

A stable divide-and-conquer sorting algorithm that recursively sorts halves and merges them.

### Real-world analogy

Two people independently sort two piles of cards, then one person merges the two sorted piles by repeatedly taking the smaller top card.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[8 3 5 1]
   /      \
[8 3]    [5 1]
 / \      / \
[8][3]  [5][1]
  ↓       ↓
[3 8]   [1 5]
    \   /
 [1 3 5 8]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Need predictable O(n log n), stable sorting, inversion counting variants.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Each half becomes sorted recursively. During merge, the smallest remaining item must be at the front of one of the two sorted halves.

---

## 5. Step-by-step method

Split until one element. Merge adjacent sorted pieces by two pointers. Copy merged result back.

---

## 6. Small example / dry run

`[8,3,5,1]` → `[3,8]` and `[1,5]` → merge to `[1,3,5,8]`.

---

## 7. Java implementation

```java
static void mergeSort(int[] a, int l, int r, int[] tmp) {
    if (l >= r) return;

    int m = l + (r - l) / 2;
    mergeSort(a, l, m, tmp);
    mergeSort(a, m + 1, r, tmp);

    int i=l, j=m+1, k=l;
    while (i<=m && j<=r)
        tmp[k++] = a[i] <= a[j] ? a[i++] : a[j++];
    while (i<=m) tmp[k++] = a[i++];
    while (j<=r) tmp[k++] = a[j++];

    for (i=l; i<=r; i++) a[i]=tmp[i];
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
| Time | O(n log n) |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Incorrect merge boundaries.\n- Forgetting to copy temporary values back.\n- Losing stability by using `<` instead of `<=` when stability matters.

---

## 10. Real interview / real-world examples

- Sorting large files/data batches conceptually.\n- Counting inversions in arrays.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Merge Sort**?

Write your answer here:

> 

