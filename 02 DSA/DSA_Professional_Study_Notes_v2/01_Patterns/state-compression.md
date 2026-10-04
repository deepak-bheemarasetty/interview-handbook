# State Compression

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pattern of representing a large DP state compactly when only a small amount of previous information is actually needed.

---

## 1. Learn this first — in one minute

### What is State Compression?

A pattern of representing a large DP state compactly when only a small amount of previous information is actually needed.

### Real-world analogy

Instead of keeping every previous day's weather report, keep only yesterday's and today's values if tomorrow depends only on those.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
full DP:
dp[0][0] ... dp[i-2]
dp[i-1]  -> dp[i]

compressed:
prev2 -> prev1 -> current
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

DP transition depends only on recent rows/states; bitmask can encode a set of boolean choices.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If future computation never reads older states, storing them wastes memory. Keep only the dependency frontier.

---

## 5. Step-by-step method

Inspect transition. Identify oldest state read. Replace table with rolling variables/rows. For subsets of n small features, use n-bit integer masks.

---

## 6. Small example / dry run

House Robber only needs best through i-1 and i-2, so an O(n) table becomes two variables.

---

## 7. Java implementation

```java
int prev2=0, prev1=0;
for(int x: nums){
    int cur=Math.max(prev1,prev2+x);
    prev2=prev1;
    prev1=cur;
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
| Time | Often same as original DP |
| Extra space | Can reduce O(n) or O(nm) to O(1) or O(m) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Compressing when the transition still needs older states.\n- Updating variables in the wrong order.

---

## 10. Real interview / real-world examples

- Memory-efficient DP.\n- Bitmask subset representation.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced DP: state compression.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **State Compression**?

Write your answer here:

> 

