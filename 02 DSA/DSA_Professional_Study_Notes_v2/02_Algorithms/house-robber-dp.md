# House Robber DP

> **Classification:** Algorithm  
> **Purpose:** Finds maximum sum from non-adjacent values.

---

## 1. Learn this first — in one minute

### What is House Robber DP?

Finds maximum sum from non-adjacent values.

### Real-world analogy

Rob houses along a street, but security alarms trigger if two adjacent houses are robbed. At each house, choose skip or rob.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
money: [2, 7, 9, 3, 1]
best:   2  7 11 11 12
choices: 2+9+1 = 12
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Maximum sum with adjacent choices forbidden; take/skip.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

At house i, either skip it and keep previous best, or rob it and add its money to the best from i-2.

---

## 5. Step-by-step method

`dp[i]=max(dp[i-1], dp[i-2]+money[i])`; compress to two variables.

---

## 6. Small example / dry run

For `[2,7,9,3,1]`: best progresses 2,7,11,11,12.

---

## 7. Java implementation

```java
int prev2=0, prev1=0;
for(int money: nums){
    int cur=Math.max(prev1, prev2+money);
    prev2=prev1;
    prev1=cur;
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
| Time | O(n) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Taking adjacent houses.\n- Misdefining prev2/prev1.

---

## 10. Real interview / real-world examples

- Selecting non-adjacent projects.\n- Choosing maximum-value advertisements with adjacency restrictions.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: House Robber.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **House Robber DP**?

Write your answer here:

> 

