# Kosaraju SCC

> **Classification:** Algorithm  
> **Purpose:** Finds strongly connected components in a directed graph using two DFS passes and a reversed graph.

---

## 1. Learn this first — in one minute

### What is Kosaraju SCC?

Finds strongly connected components in a directed graph using two DFS passes and a reversed graph.

### Real-world analogy

A set of cities is strongly connected if every city can reach every other. Reverse all one-way roads and use finishing order to isolate these mutually reachable groups.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Original:       Reverse:
A -> B           A <- B
^    |           ^    |
|    v           |    v
D <- C           D -> C

1) finish-time DFS
2) reverse graph
3) DFS in decreasing finish time
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Strongly connected components in directed graphs.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The first DFS gives an order where SCC “source/sink” structure is exposed. Reversing edges and processing nodes in decreasing finish time makes each DFS stay within one SCC before crossing outward.

---

## 5. Step-by-step method

1. DFS original graph and push vertices on finish. 2. Reverse every edge. 3. Pop vertices by decreasing finish time. 4. DFS reversed graph; each traversal is one SCC.

---

## 6. Small example / dry run

For a cycle A→B→C→A, every node reaches every other, so the second-pass DFS groups all three together.

---

## 7. Java implementation

```java
void dfs1(int u) {
    seen[u] = true;
    for (int v : g[u])
        if (!seen[v]) dfs1(v);
    order.push(u);
}

void dfs2(int u) {
    comp[u] = componentId;
    for (int v : rev[u])
        if (comp[v] == -1) dfs2(v);
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
| Time | O(V+E) |
| Extra space | O(V+E) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting to reverse edges.\n- Processing second DFS in wrong order.\n- Using this for undirected connected components unnecessarily.

---

## 10. Real interview / real-world examples

- Mutual dependency groups.\n- Web pages/users with two-way reachability.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced Graphs: SCC overview.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Kosaraju SCC**?

Write your answer here:

> 

