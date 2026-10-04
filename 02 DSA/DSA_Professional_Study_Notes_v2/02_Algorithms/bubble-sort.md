# Bubble Sort

> **Classification:** Algorithm  
> **Purpose:** Repeatedly swaps adjacent inverted pairs so large elements move toward the end.

---

## 1. Learn this first — in one minute

### What is Bubble Sort?

Repeatedly swaps adjacent inverted pairs so large elements move toward the end.

### Real-world analogy

Bubbles in water rise; here large values “bubble” right through repeated adjacent swaps.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[5 2 4 1]
 5>2 swap -> [2 5 4 1]
   5>4     -> [2 4 5 1]
     5>1   -> [2 4 1 5]
                         ↑ largest fixed
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Educational; nearly sorted small arrays with early-stop optimization.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

After each full pass, the largest unsorted element reaches its final position at the right.

---

## 5. Step-by-step method

Compare neighbors, swap if out of order, repeat passes. Stop early if a pass makes no swaps.

---

## 6. Small example / dry run

One pass over `[5,2,4,1]` moves 5 to the end. Next pass fixes 4, and so on.

---

## 7. Java implementation

```java
for (int end = n - 1; end > 0; end--) {
    boolean swapped = false;

    for (int j = 0; j < end; j++) {
        if (a[j] > a[j + 1]) {
            int t = a[j]; a[j] = a[j + 1]; a[j + 1] = t;
            swapped = true;
        }
    }

    if (!swapped) break;
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
| Time | O(n²) worst; O(n) best with early stop |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting early-stop if claiming best-case O(n).\n- Wrong neighbor bounds.

---

## 10. Real interview / real-world examples

- Teaching adjacent swap mechanics.\n- Small nearly sorted data.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Bubble Sort**?

Write your answer here:

> 

