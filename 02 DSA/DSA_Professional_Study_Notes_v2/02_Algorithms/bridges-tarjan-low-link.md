# Bridges (Tarjan Low-Link)

> **Classification:** Algorithm  
> **Purpose:** Finds edges whose removal disconnects an undirected graph.

---

## 1. Learn this first — in one minute

### What is Bridges (Tarjan Low-Link)?

Finds edges whose removal disconnects an undirected graph.

### Real-world analogy

In a road network, a bridge is a road that, if closed, separates one region from another.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A -- B -- C
     |
     D

Edge A-B may be a bridge if B's side
has no alternate route back to A.
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Critical edges; network vulnerability; undirected graph.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

During DFS, `low[v]` is the earliest discovery time reachable from v using tree edges plus at most one back edge. If `low[v] > tin[u]`, child v cannot reach u or an ancestor without edge (u,v), so that edge is a bridge.

---

## 5. Step-by-step method

DFS with discovery time `tin` and low-link. For child v, update low[u]. If `low[v] > tin[u]`, record (u,v). Skip only the actual parent edge appropriately.

---

## 6. Small example / dry run

If B's subtree has no edge back to A or an ancestor of A, removing A-B isolates B's region.

---

## 7. Java implementation

```java
void dfs(int u, int parent) {
    tin[u] = low[u] = timer++;

    for (int v : graph[u]) {
        if (v == parent) continue;

        if (tin[v] != -1) {
            low[u] = Math.min(low[u], tin[v]);
        } else {
            dfs(v, u);
            low[u] = Math.min(low[u], low[v]);

            if (low[v] > tin[u])
                bridges.add(new int[]{u, v});
        }
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
| Time | O(V+E) |
| Extra space | O(V) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using `low[v] >= tin[u]` for bridges; strict `>` is required.\n- Incorrect parent handling with parallel edges.

---

## 10. Real interview / real-world examples

- Critical roads/cables.\n- Network vulnerability analysis.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced Graphs.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Bridges (Tarjan Low-Link)**?

Write your answer here:

> 

