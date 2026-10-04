# Bellman-Ford

> **Classification:** Algorithm  
> **Purpose:** Finds single-source shortest paths even when edges can have negative weights, and can detect reachable negative cycles.

---

## 1. Learn this first — in one minute

### What is Bellman-Ford?

Finds single-source shortest paths even when edges can have negative weights, and can detect reachable negative cycles.

### Real-world analogy

Repeatedly tell every road, “If you know a cheaper way to reach this road's start, update its destination.” After V-1 rounds, every simple shortest path has had enough opportunities to propagate.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A --4--> B --(-2)--> C
 \----------------5-----> C

rounds:
A=0
B=4
C=min(5,4-2)=2
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Negative edge weights; need negative-cycle detection.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A simple shortest path uses at most V-1 edges. Relaxing every edge V-1 times guarantees every such path can propagate its best distance.

---

## 5. Step-by-step method

Initialize source=0. Repeat V-1 times: relax every edge. If no change, stop early. One more full pass with a successful relaxation means a reachable negative cycle.

---

## 6. Small example / dry run

A→B=4, B→C=-2, A→C=5. First pass gets B=4 and C=5; another relaxation updates C to 2.

---

## 7. Java implementation

```java
Arrays.fill(dist, INF);
dist[src] = 0;

for (int i = 1; i <= V - 1; i++) {
    boolean changed = false;

    for (Edge e : edges) {
        if (dist[e.u] < INF &&
            dist[e.v] > dist[e.u] + e.w) {
            dist[e.v] = dist[e.u] + e.w;
            changed = true;
        }
    }

    if (!changed) break;
}

// Extra pass detects a reachable negative cycle.
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
| Time | O(VE) |
| Extra space | O(V) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using INF in arithmetic without checking.\n- Claiming every negative cycle is reachable; only reachable cycles affect source distances.\n- Forgetting the V-th relaxation check.

---

## 10. Real interview / real-world examples

- Currency/financial graphs with possible negative adjustments conceptually.\n- Network graphs with rebates/credits represented as negative edges.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Bellman-Ford**?

Write your answer here:

> 

