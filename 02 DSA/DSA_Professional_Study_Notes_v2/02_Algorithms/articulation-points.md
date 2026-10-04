# Articulation Points

> **Classification:** Algorithm  
> **Purpose:** Finds vertices whose removal increases the number of connected components.

---

## 1. Learn this first — in one minute

### What is Articulation Points?

Finds vertices whose removal increases the number of connected components.

### Real-world analogy

In a transportation network, an articulation point is a central junction whose closure splits the network into disconnected regions.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A -- B -- C
     |
     D

Remove B:
A     C
      |
      D
network splits
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Critical vertices; network failure; undirected graph.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

For a non-root DFS vertex u, if a child subtree v cannot reach an ancestor of u (`low[v] >= tin[u]`), then removing u separates that subtree. A DFS root is special and is an articulation point only with at least two DFS children.

---

## 5. Step-by-step method

Compute tin/low. For each DFS child, update low. Mark non-root u if `low[v] >= tin[u]`. Mark root if it has ≥2 DFS children.

---

## 6. Small example / dry run

B connects A to the C-D side. Removing B separates A, so B is an articulation point.

---

## 7. Java implementation

```java
void dfs(int u, int parent) {
    tin[u] = low[u] = timer++;
    int children = 0;

    for (int v : graph[u]) {
        if (v == parent) continue;

        if (tin[v] != -1) {
            low[u] = Math.min(low[u], tin[v]);
        } else {
            dfs(v, u);
            low[u] = Math.min(low[u], low[v]);

            if (parent != -1 && low[v] >= tin[u])
                isCut[u] = true;

            children++;
        }
    }

    if (parent == -1 && children > 1)
        isCut[u] = true;
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

- Applying the root rule incorrectly.\n- Using `>` instead of `>=` for non-root articulation points.

---

## 10. Real interview / real-world examples

- Critical routers.\n- Bridge/junction failure analysis.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Articulation Points**?

Write your answer here:

> 

