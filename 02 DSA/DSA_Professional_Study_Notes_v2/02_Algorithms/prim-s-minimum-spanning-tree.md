# Prim's Minimum Spanning Tree

> **Classification:** Algorithm  
> **Purpose:** Builds a minimum spanning tree by repeatedly adding the cheapest edge from the current tree to an unvisited vertex.

---

## 1. Learn this first — in one minute

### What is Prim's Minimum Spanning Tree?

Builds a minimum spanning tree by repeatedly adding the cheapest edge from the current tree to an unvisited vertex.

### Real-world analogy

Connecting all offices with the least total cable cost. Start from one office and always add the cheapest cable that reaches a new office.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Start A
A --2-- B
|       |
5       1
|       |
C --3-- D

Pick AB(2), then BD(1), then DC(3)
total = 6
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Minimum spanning tree on weighted undirected graph; connect all vertices cheaply.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

At every stage, the cheapest edge crossing from the current connected set to the outside is safe by the cut property.

---

## 5. Step-by-step method

1. Start from any vertex. 2. Put outgoing edges in min-heap. 3. Pick cheapest edge to unvisited vertex. 4. Add vertex and its edges. 5. Repeat V-1 times.

---

## 6. Small example / dry run

From A, choose AB=2 over AC=5. From {A,B}, choose BD=1. Then choose the cheapest edge reaching remaining C.

---

## 7. Java implementation

```java
PriorityQueue<Edge> pq =
    new PriorityQueue<>(Comparator.comparingInt(e -> e.weight));

boolean[] used = new boolean[n];
pq.offer(new Edge(0, 0)); // weight, vertex
int total = 0, edges = 0;

while (!pq.isEmpty() && edges < n) {
    Edge e = pq.poll();
    if (used[e.to]) continue;

    used[e.to] = true;
    total += e.weight;
    edges++;

    for (Edge next : graph[e.to])
        if (!used[next.to]) pq.offer(next);
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
| Time | O(E log V) with heap |
| Extra space | O(V+E) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Confusing MST with shortest path from a source.\n- Adding an edge to an already visited vertex.\n- Ignoring disconnected graphs.

---

## 10. Real interview / real-world examples

- Cheapest network cable.\n- Connecting cities with minimum total road cost.

---

## 11. Problems from your roadmap that connect to this

Roadmap MST & DSU; compare with Kruskal.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Prim's Minimum Spanning Tree**?

Write your answer here:

> 

