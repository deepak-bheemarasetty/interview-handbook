# Climbing Stairs DP

> **Classification:** Algorithm  
> **Purpose:** Counts ways to reach step n when each move is 1 or 2 steps.

---

## 1. Learn this first — in one minute

### What is Climbing Stairs DP?

Counts ways to reach step n when each move is 1 or 2 steps.

### Real-world analogy

If you can climb one or two stairs at a time, every route to stair n comes from stair n-1 or n-2.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
step: 0 1 2 3 4 5
ways: 1 1 2 3 5 8
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Count paths where the current state depends on previous fixed-size states.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The final move is either one step from n-1 or two steps from n-2, so `dp[n]=dp[n-1]+dp[n-2]`.

---

## 5. Step-by-step method

Set dp0=1, dp1=1. Iterate to n.

---

## 6. Small example / dry run

For n=4: 1,1,2,3,5 → 5 ways.

---

## 7. Java implementation

```java
int a=1,b=1;
for(int i=2;i<=n;i++){
    int c=a+b;
    a=b;
    b=c;
}
return b;
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

- Wrong base case for n=0.

---

## 10. Real interview / real-world examples

- Number of ways to reach a destination with 1/2-step moves.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Climbing Stairs.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Climbing Stairs DP**?

Write your answer here:

> 

