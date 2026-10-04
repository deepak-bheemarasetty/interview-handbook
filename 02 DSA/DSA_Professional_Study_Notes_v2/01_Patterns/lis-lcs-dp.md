# LIS / LCS DP

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A family of subsequence algorithms. LIS finds the longest strictly increasing subsequence; LCS finds the longest sequence common to two sequences while preserving order.

---

## 1. Learn this first — in one minute

### What is LIS / LCS DP?

A family of subsequence algorithms. LIS finds the longest strictly increasing subsequence; LCS finds the longest sequence common to two sequences while preserving order.

### Real-world analogy

LIS: choosing an increasing set of heights from a lineup. LCS: comparing two versions of a document and finding the largest sequence of matching lines/characters in order.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
LIS: [10, 9, 2, 5, 3, 7, 101]
                 2 -> 5 -> 7 -> 101

LCS:
A B C D
  B C E
  common: B C
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

“Subsequence” rather than contiguous; compare two strings/sequences; preserve relative order.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A subsequence can skip elements. DP captures the best answer after considering prefixes. LCS uses a two-prefix state; LIS can use O(n²) DP or O(n log n) tails.

---

## 5. Step-by-step method

LCS: compare last elements of two prefixes; if equal extend diagonal, otherwise take the better of dropping one side. LIS: for each index, consider earlier smaller values or use a tails array with binary search.

---

## 6. Small example / dry run

For LCS `ABC` and `BAC`, the longest common subsequence has length 2, such as `AC` or `BC`. For LIS, `[10,9,2,5,3,7]` has length 3, e.g. `2,5,7`.

---

## 7. Java implementation

```java
// LCS core
for (int i = 1; i <= n; i++) {
    for (int j = 1; j <= m; j++) {
        if (a.charAt(i - 1) == b.charAt(j - 1))
            dp[i][j] = dp[i - 1][j - 1] + 1;
        else
            dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
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
| Time | LCS O(nm); LIS O(n²) DP or O(n log n) tails |
| Extra space | O(nm) for standard LCS; O(n) for LIS tails |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Confusing subsequence with substring/subarray.\n- Treating LIS tails as the actual sequence without parent reconstruction.\n- Using wrong inequality for strictly increasing vs non-decreasing LIS.

---

## 10. Real interview / real-world examples

- Version-control style sequence comparison.\n- Finding a trend in measurements.\n- Comparing two DNA/protein sequences conceptually.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Longest Increasing Subsequence, Longest Common Subsequence.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **LIS / LCS DP**?

Write your answer here:

> 

