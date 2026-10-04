# Graph Traversal

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pattern for systematically visiting reachable graph vertices using BFS or DFS while tracking visited state.

---

## 1. Learn this first — in one minute

### What is Graph Traversal?

A pattern for systematically visiting reachable graph vertices using BFS or DFS while tracking visited state.

### Real-world analogy

Exploring a city map without visiting the same intersection repeatedly.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A -- B -- D
|    |
C    E

start A:
visited -> A,B,C,D,E
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Connected components, reachability, islands, graph copying, cycle exploration.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Graphs may contain cycles, so unlike a tree, you must remember which vertices have already been processed.

---

## 5. Step-by-step method

Choose BFS for levels/unweighted shortest path; DFS for recursive structure/components. Mark visited at the correct time.

---

## 6. Small example / dry run

From A, BFS explores B,C first; DFS may follow A→B→D before returning.

---

## 7. Java implementation

```java
boolean[] visited = new boolean[n];

void dfs(int u) {
    visited[u] = true;
    for (int v : graph[u])
        if (!visited[v]) dfs(v);
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

- Forgetting visited.\n- Wrong graph representation.

---

## 10. Real interview / real-world examples

- Social-network reachability.\n- Road-network exploration.

---

## 11. Problems from your roadmap that connect to this

Roadmap Graph Fundamentals.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Graph Traversal**?

Write your answer here:

> 

