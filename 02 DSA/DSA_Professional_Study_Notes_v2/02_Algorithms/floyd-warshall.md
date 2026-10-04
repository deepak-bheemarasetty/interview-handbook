# Floyd-Warshall

> **Classification:** Algorithm  
> **Purpose:** Computes shortest paths between every pair of vertices using DP over allowed intermediate vertices.

---

## 1. Learn this first — in one minute

### What is Floyd-Warshall?

Computes shortest paths between every pair of vertices using DP over allowed intermediate vertices.

### Real-world analogy

For every pair of cities, ask: “Is the route shorter if I allow city K as a stop?” Gradually allow more possible intermediate cities.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
dist[i][j]
   |
allow k=0
   |
allow k=1
   |
...
allow k=V-1
   |
all-pairs shortest paths
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

All-pairs shortest paths; graph small enough for O(V³).

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

After processing k, `dist[i][j]` is the shortest route from i to j whose intermediate vertices are among 0..k.

---

## 5. Step-by-step method

Initialize direct edge weights, diagonal 0, infinity otherwise. For each k, try `i→k→j`. Skip infinity arithmetic.

---

## 6. Small example / dry run

If A→B=5, B→C=2, and A→C=10, allowing B as intermediate changes A→C to 7.

---

## 7. Java implementation

```java
for (int k = 0; k < n; k++) {
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            if (dist[i][k] < INF && dist[k][j] < INF) {
                dist[i][j] = Math.min(
                    dist[i][j],
                    dist[i][k] + dist[k][j]
                );
            }
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
| Time | O(V³) |
| Extra space | O(V²) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Wrong loop order; k must be outermost.\n- Adding infinity.\n- Confusing with Dijkstra, which is single-source.

---

## 10. Real interview / real-world examples

- All-pairs network latency.\n- Small transportation networks.

---

## 11. Problems from your roadmap that connect to this

Roadmap Shortest Paths.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Floyd-Warshall**?

Write your answer here:

> 

