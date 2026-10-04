# 1D DP

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** Dynamic programming where the state is indexed by one dimension, usually a position, day, amount, or prefix length.

---

## 1. Learn this first — in one minute

### What is 1D DP?

Dynamic programming where the state is indexed by one dimension, usually a position, day, amount, or prefix length.

### Real-world analogy

Planning a staircase climb: the best way to reach step i depends only on smaller steps. Save those answers instead of recalculating every route.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
dp:
step: 0  1  2  3  4
ways: 1  1  2  3  5

ways[i] = ways[i-1] + ways[i-2]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Sequential choices; current answer depends on a small number of previous states; overlapping subproblems.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The same smaller question appears many times in recursion. DP stores it once. The most important skill is defining what `dp[i]` means.

---

## 5. Step-by-step method

1. Define state. 2. Write transition. 3. Set base cases. 4. Compute in dependency order. 5. Compress memory if only recent states are needed.

---

## 6. Small example / dry run

Climbing stairs: ways(1)=1, ways(2)=2, ways(3)=ways(2)+ways(1)=3, ways(4)=5.

---

## 7. Java implementation

```java
int prev2 = 1; // dp[i-2]
int prev1 = 1; // dp[i-1]

for (int i = 2; i <= n; i++) {
    int cur = prev1 + prev2;
    prev2 = prev1;
    prev1 = cur;
}
return prev1;
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
| Time | Usually O(n) |
| Extra space | O(n) table or O(1) when only recent states are needed |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Defining dp ambiguously.\n- Wrong base cases.\n- Using a greedy shortcut without proof.\n- Forgetting whether state represents exact position or best answer up to position.

---

## 10. Real interview / real-world examples

- Number of ways to reach a destination.\n- Maximum money robbed without taking adjacent houses.\n- Best score over sequential days.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Climbing Stairs, House Robber.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **1D DP**?

Write your answer here:

> 

