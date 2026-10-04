# Lazy Propagation Segment Tree

> **Classification:** Algorithm  
> **Purpose:** Extends a segment tree so whole range updates can be deferred and applied to nodes only when necessary.

---

## 1. Learn this first — in one minute

### What is Lazy Propagation Segment Tree?

Extends a segment tree so whole range updates can be deferred and applied to nodes only when necessary.

### Real-world analogy

Instead of updating every employee record in a department immediately, record “everyone in this department gets +₹500” at the department level and push the instruction to smaller teams only when needed.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Range update [2..6] += 5

        [0..7]
       /      \
   [0..3]    [4..7]
      \       /
       affected nodes
store pending +5 as lazy tag
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Both range updates and range queries where O(n) per update is too slow.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A whole segment can receive the same update without immediately visiting every leaf. Store the pending operation in a lazy tag and push it down only when a child needs accurate information.

---

## 5. Step-by-step method

If update fully covers node, apply to node and mark lazy. For partial overlap, push pending tag to children, recurse, then recompute parent. Query similarly pushes when descending.

---

## 6. Small example / dry run

Adding 5 to positions 2–6 updates several large segments directly instead of all five leaves.

---

## 7. Java implementation

```java
// Conceptual range-add segment tree
void apply(int node, int l, int r, long delta) {
    tree[node] += delta * (r - l + 1);
    lazy[node] += delta;
}

void push(int node, int l, int r) {
    if (lazy[node] == 0 || l == r) return;
    int mid=(l+r)/2;
    apply(node*2,l,mid,lazy[node]);
    apply(node*2+1,mid+1,r,lazy[node]);
    lazy[node]=0;
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
| Time | Typically O(log n) per range update/query |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting to push before descending.\n- Applying range delta as if it affected only one element.

---

## 10. Real interview / real-world examples

- Bulk salary updates plus range reporting.\n- Batch sensor adjustments.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced DS: lazy propagation overview.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Lazy Propagation Segment Tree**?

Write your answer here:

> 

