# Range Query Pattern

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pattern for answering many range queries efficiently, choosing between prefix sums, Fenwick trees, segment trees, or sparse-style preprocessing based on update requirements.

---

## 1. Learn this first — in one minute

### What is Range Query Pattern?

A pattern for answering many range queries efficiently, choosing between prefix sums, Fenwick trees, segment trees, or sparse-style preprocessing based on update requirements.

### Real-world analogy

A supermarket manager stores aisle totals. If prices never change, prefix totals are enough; if prices change frequently, a tree of partial totals is better.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Need range [l,r]

static data -> Prefix
point updates -> Fenwick
complex range queries -> Segment Tree
range updates -> Lazy Segment Tree
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Many queries over intervals; updates may or may not exist.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The correct data structure depends on whether the underlying array changes and what operation is queried.

---

## 5. Step-by-step method

Ask: static or dynamic? point or range updates? sum/min/max/gcd? Then choose the lightest structure that meets complexity needs.

---

## 6. Small example / dry run

Static range sum → prefix. If point updates happen → Fenwick. If range min and updates → segment tree.

---

## 7. Java implementation

```java
// Prefix:
sum(l,r) = prefix[r] - prefix[l-1];

// Dynamic:
Fenwick / Segment Tree
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
| Time | Depends on structure: prefix O(1) query; Fenwick/segment tree usually O(log n) |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using segment tree for a simple static prefix problem.\n- Choosing a structure without considering update type.

---

## 10. Real interview / real-world examples

- Live scoreboard range totals.\n- Sensor statistics.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced DS.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Range Query Pattern**?

Write your answer here:

> 

