# Selection Sort

> **Classification:** Algorithm  
> **Purpose:** Repeatedly finds the smallest remaining element and places it at the next position.

---

## 1. Learn this first — in one minute

### What is Selection Sort?

Repeatedly finds the smallest remaining element and places it at the next position.

### Real-world analogy

Selecting the cheapest item from a shelf, putting it first, then repeating with the remaining items.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[5 2 4 1]
 ^----- minimum=1
swap -> [1 2 4 5]
       sorted prefix ↑
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Mostly educational; tiny arrays; need simple in-place selection.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

After iteration i, positions 0..i contain the i+1 smallest elements in final order.

---

## 5. Step-by-step method

For each position i, scan i..n-1 for minimum, then swap it with i.

---

## 6. Small example / dry run

`[5,2,4,1]`: minimum is 1 → `[1,2,4,5]`; next minimum in suffix is 2; done.

---

## 7. Java implementation

```java
for (int i = 0; i < n - 1; i++) {
    int min = i;
    for (int j = i + 1; j < n; j++)
        if (a[j] < a[min]) min = j;

    int t = a[i]; a[i] = a[min]; a[min] = t;
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
| Time | O(n²) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting to restrict the scan to the unsorted suffix.\n- Claiming it is O(n) on sorted input; standard selection sort still scans.

---

## 10. Real interview / real-world examples

- Teaching sorting invariants.\n- Tiny datasets where implementation simplicity matters.

---

## 11. Problems from your roadmap that connect to this

Roadmap Sorting Algorithms.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Selection Sort**?

Write your answer here:

> 

