# Segment Tree

> **Classification:** Algorithm  
> **Purpose:** A tree structure for range queries and updates, typically O(log n) per operation, by storing answers for intervals.

---

## 1. Learn this first — in one minute

### What is Segment Tree?

A tree structure for range queries and updates, typically O(log n) per operation, by storing answers for intervals.

### Real-world analogy

A warehouse manager stores totals for large sections, then smaller subsections. A query combines only the sections needed to cover the requested range.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[0..7]
 /     \
[0..3] [4..7]
 / \      / \
[0..1][2..3]...

range [2..6] uses a few tree nodes
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Range min/max/sum/gcd queries with updates; need more flexibility than prefix sums.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Every range can be decomposed into O(log n) tree segments. An update changes only the O(log n) nodes whose intervals contain the changed position.

---

## 5. Step-by-step method

Build recursively. Query: if node interval fully inside, use stored value; if disjoint, return identity; otherwise combine children. Update follows the path to the leaf and recomputes ancestors.

---

## 6. Small example / dry run

For range sum [2,6], do not add all five values individually; combine the stored nodes that exactly cover the requested interval.

---

## 7. Java implementation

```java
void update(int node, int l, int r, int idx, int value) {
    if (l == r) {
        tree[node] = value;
        return;
    }

    int mid = (l + r) / 2;
    if (idx <= mid) update(node*2,l,mid,idx,value);
    else update(node*2+1,mid+1,r,idx,value);

    tree[node] = tree[node*2] + tree[node*2+1];
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
| Time | Build O(n); point update/query O(log n) |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Wrong interval boundaries.\n- Wrong identity for min/max/sum.\n- Confusing point update with lazy range update.

---

## 10. Real interview / real-world examples

- Dynamic leaderboard range statistics.\n- Sensor ranges with changing readings.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced DS: Fenwick/Segment Tree; lazy propagation overview.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Segment Tree**?

Write your answer here:

> 

