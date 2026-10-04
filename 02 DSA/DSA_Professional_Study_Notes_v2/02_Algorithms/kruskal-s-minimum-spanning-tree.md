# Kruskal's Minimum Spanning Tree

> **Classification:** Algorithm  
> **Purpose:** Builds an MST by sorting all edges by weight and accepting an edge only if it connects two different components.

---

## 1. Learn this first — in one minute

### What is Kruskal's Minimum Spanning Tree?

Builds an MST by sorting all edges by weight and accepting an edge only if it connects two different components.

### Real-world analogy

List every possible cable from cheapest to most expensive. Install the cheapest cable unless the two offices are already connected indirectly.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Edges sorted:
1: A-B ✓
2: B-C ✓
3: A-C ✗ cycle
4: C-D ✓

DSU decides ✓ / ✗
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Minimum spanning tree; edge list naturally available; cycle detection via DSU.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The cheapest edge crossing two different components is safe. DSU makes the “are these already connected?” question almost constant time.

---

## 5. Step-by-step method

Sort edges. For each edge `(u,v,w)`, if find(u) != find(v), union them and add weight. Stop after V-1 accepted edges.

---

## 6. Small example / dry run

After A-B and B-C, A and C share a root. Therefore A-C would form a cycle and is skipped.

---

## 7. Java implementation

```java
edges.sort(Comparator.comparingInt(e -> e.weight));

int total = 0, used = 0;
DSU dsu = new DSU(n);

for (Edge e : edges) {
    if (dsu.find(e.u) != dsu.find(e.v)) {
        dsu.union(e.u, e.v);
        total += e.weight;
        used++;
        if (used == n - 1) break;
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
| Time | O(E log E) |
| Extra space | O(V) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting to sort edges.\n- Adding edges within the same component.\n- Confusing MST with shortest path.

---

## 10. Real interview / real-world examples

- Cheapest network design.\n- Connecting towns with minimum total road construction.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Kruskal MST.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Kruskal's Minimum Spanning Tree**?

Write your answer here:

> 

