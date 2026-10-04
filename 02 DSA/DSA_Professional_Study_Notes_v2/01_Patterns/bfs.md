# BFS

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A graph/tree traversal that explores nodes level by level using a queue; in unweighted graphs it gives shortest distance in number of edges.

---

## 1. Learn this first — in one minute

### What is BFS?

A graph/tree traversal that explores nodes level by level using a queue; in unweighted graphs it gives shortest distance in number of edges.

### Real-world analogy

A ripple spreading through water: first everything one step away, then everything two steps away, and so on.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
        A
      / | \
     B  C  D
    / \    |
   E   F   G

BFS: A -> B,C,D -> E,F,G
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Unweighted shortest path, minimum number of moves, level order, spreading processes.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Every edge has equal cost. Therefore the first time BFS reaches a node, it has used the fewest possible edges.

---

## 5. Step-by-step method

1. Put source(s) in queue. 2. Mark visited on enqueue. 3. Pop front. 4. Add unvisited neighbors. 5. Process by queue layers when distance/time matters.

---

## 6. Small example / dry run

From A, process A first; enqueue B,C,D. Only after all three are processed do E,F,G get reached. That is why BFS naturally measures levels.

---

## 7. Java implementation

```java
Queue<Integer> q = new ArrayDeque<>();
boolean[] visited = new boolean[n];

q.offer(src);
visited[src] = true;

while (!q.isEmpty()) {
    int u = q.poll();

    for (int v : graph[u]) {
        if (!visited[v]) {
            visited[v] = true;
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
| Time | O(V+E) with adjacency lists |
| Extra space | O(V) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Marking visited too late and inserting duplicates.\n- Using BFS for weighted edges without adapting the model.\n- Forgetting level boundaries for time-step problems.

---

## 10. Real interview / real-world examples

- Minimum number of subway stops.\n- Fewest moves in a maze where every move costs 1.\n- Infection/spread simulation.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Binary Tree Level Order Traversal, Number of Islands, Rotting Oranges.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **BFS**?

Write your answer here:

> 

