# 2D / Grid DP

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** Dynamic programming where each cell/state depends on neighboring cells or previous rows/columns.

---

## 1. Learn this first — in one minute

### What is 2D / Grid DP?

Dynamic programming where each cell/state depends on neighboring cells or previous rows/columns.

### Real-world analogy

Finding the cheapest route through a warehouse grid. The cheapest way to reach a cell is based on the cheapest ways to reach the cells immediately before it.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
     c0 c1 c2
r0   [1][1][1]
r1   [1][2][3]
r2   [1][3][6]

dp[r][c] depends on valid predecessors
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Matrix paths, obstacles, minimum/maximum path cost, two-dimensional state.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A grid gives a natural DAG if movement is restricted, such as right/down. Therefore each cell can be solved after its predecessors.

---

## 5. Step-by-step method

1. Define dp[r][c]. 2. Identify predecessor cells. 3. Initialize first row/column. 4. Apply transition. 5. Optionally compress to one row.

---

## 6. Small example / dry run

For unique paths moving right/down, `dp[r][c]=dp[r-1][c]+dp[r][c-1]`; every path reaches the cell from one of those two directions.

---

## 7. Java implementation

```java
int[] dp = new int[cols];
dp[0] = 1;

for (int r = 0; r < rows; r++) {
    for (int c = 0; c < cols; c++) {
        if (blocked[r][c]) {
            dp[c] = 0;
        } else if (c > 0) {
            dp[c] += dp[c - 1];
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
| Time | O(rows × cols) |
| Extra space | O(rows × cols) or O(cols) compressed |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Wrong first-row/first-column initialization.\n- Allowing illegal movement.\n- Forgetting obstacles reset reachability.

---

## 10. Real interview / real-world examples

- Robot moving through warehouse aisles.\n- Minimum-cost route through a grid.\n- Counting ways through a city block layout.

---

## 11. Problems from your roadmap that connect to this

Roadmap 2D/Grid DP; Problem Bank Edit Distance is also 2D DP but uses a different state.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **2D / Grid DP**?

Write your answer here:

> 

