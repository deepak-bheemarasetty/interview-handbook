# Kadane's Algorithm

> **Classification:** Algorithm  
> **Purpose:** Finds the maximum-sum contiguous subarray in one pass.

---

## 1. Learn this first — in one minute

### What is Kadane's Algorithm?

Finds the maximum-sum contiguous subarray in one pass.

### Real-world analogy

Imagine walking through daily profits. At each day, decide whether continuing the current winning streak is better than starting fresh today.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[-2, 3, -1, 5, -6, 4]
       \
current best ending here:
-2 -> 3 -> 2 -> 7 -> 1 -> 4
global best = 7
subarray = [3,-1,5]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Maximum/minimum contiguous subarray sum; one-pass optimization over a sequence.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

For a subarray ending at i, either continue the best subarray ending at i-1 or start at i. Therefore `current=max(a[i], current+a[i])`.

---

## 5. Step-by-step method

Initialize current and global best to first value. For each next value, choose start-new or extend. Update global best.

---

## 6. Small example / dry run

For `[-2,3,-1,5]`: current -2; at 3 start 3; at -1 current 2; at 5 current 7 → best 7.

---

## 7. Java implementation

```java
int current = nums[0];
int best = nums[0];

for (int i = 1; i < nums.length; i++) {
    current = Math.max(nums[i], current + nums[i]);
    best = Math.max(best, current);
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
| Time | O(n) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Initializing to 0 when all values may be negative.\n- Solving a subsequence problem instead of contiguous subarray.

---

## 10. Real interview / real-world examples

- Best profit streak over consecutive days.\n- Maximum scoring run in a game.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Maximum Subarray.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Kadane's Algorithm**?

Write your answer here:

> 

