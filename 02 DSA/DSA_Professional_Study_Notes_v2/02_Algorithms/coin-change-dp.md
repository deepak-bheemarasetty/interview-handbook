# Coin Change DP

> **Classification:** Algorithm  
> **Purpose:** Finds the minimum number of coins needed to form an amount when coins can usually be reused.

---

## 1. Learn this first — in one minute

### What is Coin Change DP?

Finds the minimum number of coins needed to form an amount when coins can usually be reused.

### Real-world analogy

Making ₹11 using denominations 1, 5, 7: for each amount, ask which coin could be the last coin added.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
amount: 0 1 2 3 4 5 6 7
dp:     0 1 2 3 4 1 2 1

dp[x] = 1 + min(dp[x-coin])
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Minimum coins / number of ways to make an amount; unlimited reuse.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If coin c is the last coin, the remaining amount is `x-c`, whose optimal answer is already known.

---

## 5. Step-by-step method

Initialize dp[0]=0 and others infinity. For each amount, try every coin and take the minimum.

---

## 6. Small example / dry run

For coins `[1,5,7]`, amount 7 can use one 7-coin, so dp[7]=1.

---

## 7. Java implementation

```java
int[] dp = new int[amount + 1];
Arrays.fill(dp, amount + 1);
dp[0] = 0;

for (int x=1; x<=amount; x++) {
    for (int coin : coins) {
        if (coin <= x)
            dp[x] = Math.min(dp[x], dp[x-coin] + 1);
    }
}
return dp[amount] > amount ? -1 : dp[amount];
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
| Time | O(amount × number of coins) |
| Extra space | O(amount) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Confusing unlimited coin reuse with 0/1 knapsack.\n- Forgetting impossible amounts.

---

## 10. Real interview / real-world examples

- Making change.\n- Minimizing number of resource units.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Coin Change DP**?

Write your answer here:

> 

