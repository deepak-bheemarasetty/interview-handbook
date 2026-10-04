# Counting Sort

> **Classification:** Algorithm  
> **Purpose:** Sorts integer keys by counting how often each value occurs rather than comparing pairs.

---

## 1. Learn this first — in one minute

### What is Counting Sort?

Sorts integer keys by counting how often each value occurs rather than comparing pairs.

### Real-world analogy

Instead of comparing every student’s score, put each score into its numbered bucket and then read the buckets from smallest to largest.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Values: [2,1,2,0,3,1]

counts:
0 -> 1
1 -> 2
2 -> 2
3 -> 1

read buckets:
0,1,1,2,2,3
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Integer keys in a small known range.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Comparison sorting asks which pair is smaller. Counting sort avoids comparisons entirely by using the key as an array index.

---

## 5. Step-by-step method

Find range. Count each value. Reconstruct values in increasing key order. For stable variants, use prefix counts and an output array.

---

## 6. Small example / dry run

Counts for `[2,1,2,0,3,1]` are `[1,2,2,1]`; reading them gives sorted order.

---

## 7. Java implementation

```java
int[] count = new int[maxValue + 1];

for (int x : nums) count[x]++;

int k = 0;
for (int value = 0; value < count.length; value++) {
    while (count[value]-- > 0)
        nums[k++] = value;
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
| Time | O(n+k) |
| Extra space | O(k) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using it when k is enormous compared with n.\n- Forgetting negative values require offset/range handling.

---

## 10. Real interview / real-world examples

- Sorting exam scores 0–100.\n- Sorting small integer IDs.

---

## 11. Problems from your roadmap that connect to this

Roadmap Sorting Algorithms.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Counting Sort**?

Write your answer here:

> 

