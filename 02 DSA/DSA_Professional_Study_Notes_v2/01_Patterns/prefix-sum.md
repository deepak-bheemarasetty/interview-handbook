# Prefix Sum

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A reusable pattern for turning repeated range/subarray sum calculations into constant-time lookups after one linear preprocessing pass.

---

## 1. Learn this first — in one minute

### What is Prefix Sum?

A reusable pattern for turning repeated range/subarray sum calculations into constant-time lookups after one linear preprocessing pass.

### Real-world analogy

Think of a bank statement where you keep a running balance after every transaction. To know how much changed between two dates, subtract the earlier balance from the later balance instead of adding every transaction again.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Array:       [ 3,  2,  5, -1,  4 ]
Prefix:      [ 3,  5, 10,  9, 13 ]
                         ↑       ↑
sum(2..4) = prefix[4] - prefix[1] = 13 - 5 = 8
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Repeated range sums; subarray sums; count subarrays with a target sum; questions about cumulative totals.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The same elements appear in many range queries. Store the cumulative work once. For a range [l,r], everything before l appears in both prefix sums and cancels.

---

## 5. Step-by-step method

1. Build or maintain a running prefix value. 2. For a direct range query use `prefix[r] - prefix[l-1]`. 3. For counting target-sum subarrays, maintain frequencies of previous prefix sums and look for `current - target`.

---

## 6. Small example / dry run

For `[1,2,3]`, target `3`: prefixes are 1,3,6. At prefix 3, a previous prefix 0 gives sum 3. At prefix 6, previous prefix 3 gives another sum 3. The initial frequency `{0:1}` is what lets subarrays beginning at index 0 work.

---

## 7. Java implementation

```java
long prefix = 0;
Map<Long, Integer> freq = new HashMap<>();
freq.put(0L, 1);
long answer = 0;

for (int x : nums) {
    prefix += x;
    answer += freq.getOrDefault(prefix - k, 0);
    freq.put(prefix, freq.getOrDefault(prefix, 0) + 1);
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
| Time | O(n) for one pass / O(1) per range query after O(n) preprocessing |
| Extra space | O(n) for a prefix array or frequency map; O(1) if only one running sum is needed |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting the initial prefix 0.\n- Mixing inclusive/exclusive indices.\n- Using `int` when sums can overflow.\n- Confusing subarray (contiguous) with subsequence.

---

## 10. Real interview / real-world examples

- Electricity meter readings accumulated over days.\n- Sales revenue between two dates.\n- Number of subarrays whose sum equals K.\n- Running score in a game.

---

## 11. Problems from your roadmap that connect to this

Your roadmap: Array Fundamentals, Subarray Sum Equals K, Product of Array Except Self (prefix/suffix).

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Prefix Sum**?

Write your answer here:

> 

