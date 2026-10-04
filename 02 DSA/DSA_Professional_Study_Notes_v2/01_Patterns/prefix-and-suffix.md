# Prefix and Suffix

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** Precompute information from the left and right so each position can answer a question about everything except/around itself.

---

## 1. Learn this first — in one minute

### What is Prefix and Suffix?

Precompute information from the left and right so each position can answer a question about everything except/around itself.

### Real-world analogy

For a road, keep the total traffic before a checkpoint and after it; then a checkpoint can answer global context without rescanning the road.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A:      [1 2 3 4]
prefix: [1 3 6 10]
suffix: [10 9 7 4]

For index 2:
left = prefix[1]
right = suffix[3]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Product/sum except self; left/right maximum; range context.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Many “everything except current” questions split naturally into information before and after the current index.

---

## 5. Step-by-step method

Build prefix and/or suffix arrays, or do a two-pass O(1)-extra-space version.

---

## 6. Small example / dry run

Product Except Self at index 2 uses product of elements left of 2 multiplied by product right of 2.

---

## 7. Java implementation

```java
int[] prefix = new int[n];
prefix[0] = a[0];
for(int i=1;i<n;i++) prefix[i]=prefix[i-1]+a[i];
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
| Extra space | O(n), often reducible to O(1) auxiliary |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Including current element when the problem says except self.\n- Off-by-one around edges.

---

## 10. Real interview / real-world examples

- Product except self.\n- Left/right maximum buildings.

---

## 11. Problems from your roadmap that connect to this

Roadmap Array Fundamentals; Problem Bank Product of Array Except Self.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Prefix and Suffix**?

Write your answer here:

> 

