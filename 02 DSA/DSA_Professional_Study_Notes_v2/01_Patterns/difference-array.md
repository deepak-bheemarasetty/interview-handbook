# Difference Array

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A range-update pattern that records only where an interval update starts and stops, then reconstructs the final values with a prefix sum.

---

## 1. Learn this first — in one minute

### What is Difference Array?

A range-update pattern that records only where an interval update starts and stops, then reconstructs the final values with a prefix sum.

### Real-world analogy

Imagine increasing the salary of everyone from employee 20 through employee 50. Instead of editing 31 records, write “+₹X starting at 20” and “stop +₹X after 50”; one later pass applies the changes.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Initial:  [10 10 10 10 10 10]
Update +5 on indices 1..4
diff:     [ 0 +5  0  0  0 -5]
prefix:   [ 0  5  5  5  5  0]
final:    [10 15 15 15 15 10]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Many range increments/decrements followed by a final array; interval updates are far more numerous than final reconstruction.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A range update is constant over an interval. Only two boundaries matter: where the effect begins and where it stops. Prefix accumulation spreads those boundary changes across the interval.

---

## 5. Step-by-step method

1. Create `diff`. 2. For `[l,r] += x`, do `diff[l] += x` and `diff[r+1] -= x` when valid. 3. Prefix-sum `diff` to recover the changes. 4. Add changes to the original array if necessary.

---

## 6. Small example / dry run

Start with six 10s. Add 5 to positions 1–4. Only positions 1 and 5 change in `diff`; the prefix sum automatically carries +5 through positions 1–4.

---

## 7. Java implementation

```java
long[] diff = new long[n + 1];
diff[l] += delta;
if (r + 1 < n) diff[r + 1] -= delta;

long running = 0;
for (int i = 0; i < n; i++) {
    running += diff[i];
    result[i] = original[i] + running;
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
| Time | O(1) per update + O(n) final reconstruction |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Putting the negative marker at r instead of r+1.\n- Forgetting that intervals may be inclusive.\n- Applying the technique when you need answers after every update; then a Fenwick/segment tree may be needed.

---

## 10. Real interview / real-world examples

- Bulk salary/price adjustments.\n- Adding traffic to every road segment in a continuous section.\n- Applying many range score bonuses in a game.

---

## 11. Problems from your roadmap that connect to this

Your Patterns sheet explicitly lists Difference Array under Core Interview Patterns.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Difference Array**?

Write your answer here:

> 

