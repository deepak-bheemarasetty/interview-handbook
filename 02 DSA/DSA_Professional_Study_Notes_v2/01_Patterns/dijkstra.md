# Dijkstra

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A shortest-path algorithm for graphs with non-negative edge weights. It repeatedly finalizes the currently closest reachable vertex.

---

## 1. Learn this first — in one minute

### What is Dijkstra?

A shortest-path algorithm for graphs with non-negative edge weights. It repeatedly finalizes the currently closest reachable vertex.

### Real-world analogy

Driving from your home when every road has a non-negative travel time. Always expand the currently cheapest known route; once it is the smallest frontier distance, no later route can beat it.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
      2       3
 A -------- B ---- D
 |          |
 5          1
 |          |
 C ----------

Start A:
dist A=0
dist B=2, C=5
pick B (2) -> C=3, D=5
pick C (3) ...
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Weighted shortest path with non-negative weights; network delay; cheapest travel cost.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

With nonnegative edges, extending an already larger path can never make a settled smaller distance smaller. Therefore the smallest heap distance can be finalized.

---

## 5. Step-by-step method

1. Set source distance 0, others infinity. 2. Push source into min-heap. 3. Pop smallest distance. 4. Skip stale entries. 5. Relax outgoing edges. 6. Continue until heap is empty.

---

## 6. Small example / dry run

A→B cost 2, A→C cost 5, B→C cost 1. Initially C=5. After processing B at cost 2, C becomes 3. The cheaper route A→B→C is found automatically.

---

## 7. Java implementation

```java
PriorityQueue<long[]> pq =
    new PriorityQueue<>(Comparator.comparingLong(a -> a[0]));

Arrays.fill(dist, Long.MAX_VALUE / 4);
dist[src] = 0;
pq.offer(new long[]{0, src});

while (!pq.isEmpty()) {
    long[] cur = pq.poll();
    long d = cur[0];
    int u = (int) cur[1];

    if (d != dist[u]) continue;

    for (Edge e : graph[u]) {
        if (dist[e.to] > d + e.weight) {
            dist[e.to] = d + e.weight;
            pq.offer(new long[]{dist[e.to], e.to});
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
| Time | O((V+E) log V) with a binary heap |
| Extra space | O(V+E) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using it with negative edges.\n- Forgetting stale heap entries.\n- Integer overflow in distance sums.\n- Confusing shortest path with minimum spanning tree.

---

## 10. Real interview / real-world examples

- GPS route with nonnegative travel times.\n- Cheapest network latency.\n- Minimum delivery cost.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Dijkstra Shortest Path; roadmap Shortest Paths.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Dijkstra**?

Write your answer here:

> 

