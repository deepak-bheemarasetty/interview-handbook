# Knapsack DP

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A DP family for take/not-take decisions under a capacity, target sum, or resource constraint.

---

## 1. Learn this first — in one minute

### What is Knapsack DP?

A DP family for take/not-take decisions under a capacity, target sum, or resource constraint.

### Real-world analogy

Packing a suitcase with limited weight: every item asks the same question—take it or leave it—while respecting the remaining capacity.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Capacity = 7

item A: weight 3, value 4
item B: weight 4, value 5

             take B -> capacity 3 -> take A
best value = 9
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Capacity, budget, target sum, choose subset, each item may be used once or repeatedly.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

For each item, there are usually two choices. DP remembers the best result for every smaller capacity/target so the same subproblem is not solved repeatedly.

---

## 5. Step-by-step method

1. Define `dp[capacity]` or `dp[i][capacity]`. 2. Decide take/not-take transition. 3. For 0/1 items, iterate capacity downward when compressing to one dimension. 4. Handle impossible states.

---

## 6. Small example / dry run

Capacity 7: item A (3,4), item B (4,5). Taking both fits exactly and gives 9, better than taking either alone.

---

## 7. Java implementation

```java
int[] dp = new int[capacity + 1];

for (int i = 0; i < n; i++) {
    for (int c = capacity; c >= weight[i]; c--) {
        dp[c] = Math.max(
            dp[c],
            dp[c - weight[i]] + value[i]
        );
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
| Time | O(n × capacity) for standard 0/1 knapsack |
| Extra space | O(capacity) compressed |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using upward capacity iteration for 0/1 knapsack, which can reuse the same item.\n- Confusing exact target with at-most capacity.\n- Forgetting impossible states in minimum/boolean variants.

---

## 10. Real interview / real-world examples

- Packing a suitcase.\n- Selecting projects under a budget.\n- Choosing advertisements under limited time.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Coin Change; roadmap Knapsack/Partition.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Knapsack DP**?

Write your answer here:

> 

