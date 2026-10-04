# Shortest Path Selection

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A decision pattern for choosing the correct shortest-path algorithm from edge weights and graph size.

---

## 1. Learn this first — in one minute

### What is Shortest Path Selection?

A decision pattern for choosing the correct shortest-path algorithm from edge weights and graph size.

### Real-world analogy

Choosing a navigation method: if every street costs one stop, BFS works; if roads have positive travel times, Dijkstra works; if negative costs exist, Bellman-Ford is safer.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Edge costs?
  |
  +-- all equal -> BFS
  |
  +-- nonnegative -> Dijkstra
  |
  +-- negative -> Bellman-Ford
  |
  +-- all pairs, small V -> Floyd-Warshall
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Shortest path questions; pay attention to edge weights and whether you need one source or all pairs.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The weight model determines which assumptions are valid. BFS relies on equal edge cost; Dijkstra relies on nonnegative weights.

---

## 5. Step-by-step method

Identify source scope, edge weights, graph size, and whether negative cycles matter. Then choose algorithm.

---

## 6. Small example / dry run

A grid where every move costs 1 → BFS. Road travel times → Dijkstra. Currency graph with negative adjustments → Bellman-Ford.

---

## 7. Java implementation

```java
// Selection is conceptual:
// BFS -> Queue
// Dijkstra -> PriorityQueue
// Bellman-Ford -> repeated edge relaxation
// Floyd-Warshall -> V x V DP
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
| Time | Depends on chosen algorithm |
| Extra space | Depends on chosen algorithm |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using Dijkstra with negative edges.\n- Using Floyd-Warshall for huge V.

---

## 10. Real interview / real-world examples

- Navigation systems.\n- Network latency.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Shortest Path Selection**?

Write your answer here:

> 

