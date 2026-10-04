# Multi-Source BFS

> **Classification:** Algorithm  
> **Purpose:** BFS starting simultaneously from multiple sources, giving the minimum distance to the nearest source or simulating simultaneous spread.

---

## 1. Learn this first — in one minute

### What is Multi-Source BFS?

BFS starting simultaneously from multiple sources, giving the minimum distance to the nearest source or simulating simultaneous spread.

### Real-world analogy

Fire starts at several buildings at the same time. The first fire front to reach a house determines when it catches fire.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Sources:
S . . . S
. . . . .
. . X . .

BFS starts from both S cells
at distance 0 simultaneously
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Rotting oranges, nearest facility, distance to nearest 1/source, simultaneous spread.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If all sources start at time 0, putting them all in the initial queue makes BFS expand them in synchronized layers.

---

## 5. Step-by-step method

Enqueue every source and mark distance 0. Process queue level by level. Newly reached cells get distance parent+1.

---

## 6. Small example / dry run

With sources at positions 0 and 4, positions 1 and 3 have distance 1; position 2 has distance 2.

---

## 7. Java implementation

```java
Queue<Integer> q = new ArrayDeque<>();

for (int source : sources) {
    dist[source] = 0;
    q.offer(source);
}

while (!q.isEmpty()) {
    int u = q.poll();

    for (int v : graph[u]) {
        if (dist[v] == -1) {
            dist[v] = dist[u] + 1;
            q.offer(v);
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

- Starting separate BFS runs instead of one multi-source queue.\n- Incorrect time/level counting.

---

## 10. Real interview / real-world examples

- Nearest hospital.\n- Fire/infection spread.\n- Nearest charging station.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Rotting Oranges.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Multi-Source BFS**?

Write your answer here:

> 

