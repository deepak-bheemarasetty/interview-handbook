# Matrix Chain Multiplication DP

> **Classification:** Algorithm  
> **Purpose:** Finds the minimum scalar multiplication cost for multiplying a chain of matrices by choosing the best parenthesization.

---

## 1. Learn this first — in one minute

### What is Matrix Chain Multiplication DP?

Finds the minimum scalar multiplication cost for multiplying a chain of matrices by choosing the best parenthesization.

### Real-world analogy

When combining several expensive operations, the order matters. Multiplying small compatible matrices first can dramatically reduce work.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A × B × C

(A×B)×C     vs     A×(B×C)
   cost may differ

dp[i][j] = minimum cost for matrices i..j
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Interval DP; parenthesization/order optimization.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The final multiplication splits the chain at some k. If the best way to compute left and right parts is known, add their costs plus the final multiplication cost.

---

## 5. Step-by-step method

dp[i][j]=0 for one matrix. Increase interval length. Try every split k and minimize.

---

## 6. Small example / dry run

For dimensions 10×20, 20×30, 30×5, compare the two parenthesizations; their scalar multiplication counts differ.

---

## 7. Java implementation

```java
for (int len=2; len<=n; len++) {
    for (int i=0; i+len-1<n; i++) {
        int j=i+len-1;
        dp[i][j]=Integer.MAX_VALUE;

        for (int k=i; k<j; k++) {
            long cost = (long)dp[i][k] + dp[k+1][j]
                + (long)p[i]*p[k+1]*p[j+1];
            dp[i][j] = (int)Math.min(dp[i][j], cost);
        }
    }
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
| Time | O(n³) |
| Extra space | O(n²) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Mixing matrix count with dimension count.\n- Wrong multiplication dimensions in cost formula.

---

## 10. Real interview / real-world examples

- Optimizing chained transformations/operations conceptually.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced DP: Matrix-chain style.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Matrix Chain Multiplication DP**?

Write your answer here:

> 

