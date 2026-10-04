# Binary Search on Answer

> **Classification:** Algorithm  
> **Purpose:** Uses binary search over possible answer values when a feasibility test is monotonic.

---

## 1. Learn this first — in one minute

### What is Binary Search on Answer?

Uses binary search over possible answer values when a feasibility test is monotonic.

### Real-world analogy

Finding the minimum number of delivery trucks needed: if 10 trucks are enough, 11,12,... are also enough. So search the threshold.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
candidate answer:
1 2 3 4 5 6 7 8 9
F F F F T T T T T
        ↑
   first feasible
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

“Minimum possible X”, “maximum possible X”, and you can write `can(X)` returning true/false with monotonic behavior.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The answer space itself is ordered. Instead of searching an array, search the smallest/largest value for which the feasibility condition becomes true.

---

## 5. Step-by-step method

1. Find low/high possible answers. 2. Prove monotonicity. 3. Write `can(mid)`. 4. Search the first true/last true boundary.

---

## 6. Small example / dry run

Koko eating bananas: if speed 4 is enough to finish in H hours, any speed >4 is also enough. Search speed, not piles.

---

## 7. Java implementation

```java
long lo = 1, hi = maxPile;

while (lo < hi) {
    long mid = lo + (hi - lo) / 2;

    if (canFinish(mid))
        hi = mid;
    else
        lo = mid + 1;
}
return lo;
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
| Time | O(log(answer range) × feasibility cost) |
| Extra space | Depends on feasibility check |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- No monotonicity proof.\n- Wrong low/high bounds.\n- Overflow in feasibility arithmetic.

---

## 10. Real interview / real-world examples

- Minimum machine speed.\n- Minimum capacity to ship packages in D days.\n- Maximum minimum distance placement.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Koko Eating Bananas.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Binary Search on Answer**?

Write your answer here:

> 

