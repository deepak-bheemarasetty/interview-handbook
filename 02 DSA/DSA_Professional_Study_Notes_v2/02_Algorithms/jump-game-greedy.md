# Jump Game Greedy

> **Classification:** Algorithm  
> **Purpose:** Determines whether the last index is reachable by maintaining the farthest index reachable so far.

---

## 1. Learn this first — in one minute

### What is Jump Game Greedy?

Determines whether the last index is reachable by maintaining the farthest index reachable so far.

### Real-world analogy

You are crossing stepping stones; from every stone, update how far your current fuel/jump ability can take you.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
index: 0 1 2 3 4
jump:  2 3 1 0 4
reach: 2 -> max(2,1+3)=4 -> success
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Can reach end; each position gives maximum jump length; no cost/complexity requiring DP.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

You do not need to know every route. Only the farthest reachable position matters. If current index ever exceeds it, the end is impossible.

---

## 5. Step-by-step method

Set farthest=0. Scan indices. If i>farthest, fail. Update `farthest=max(farthest,i+nums[i])`. If farthest≥last, success.

---

## 6. Small example / dry run

`[2,3,1,1,4]`: from index 0 reach 2; index 1 extends reach to 4; last index is reachable.

---

## 7. Java implementation

```java
int farthest = 0;

for (int i = 0; i < nums.length; i++) {
    if (i > farthest) return false;
    farthest = Math.max(farthest, i + nums[i]);
    if (farthest >= nums.length - 1) return true;
}
return true;
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

- Confusing reachability with minimum number of jumps (a different greedy state/problem).

---

## 10. Real interview / real-world examples

- Battery/range reachability.\n- Minimum fuel/energy range conceptually.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Jump Game.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Jump Game Greedy**?

Write your answer here:

> 

