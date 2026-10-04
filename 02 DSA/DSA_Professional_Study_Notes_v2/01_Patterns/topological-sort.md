# Topological Sort

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** An ordering of vertices in a directed acyclic graph where every prerequisite appears before the task that depends on it.

---

## 1. Learn this first — in one minute

### What is Topological Sort?

An ordering of vertices in a directed acyclic graph where every prerequisite appears before the task that depends on it.

### Real-world analogy

Course registration: you cannot take Advanced Algorithms until its prerequisite courses have been completed.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Maths -> DSA -> Algorithms
   \          |
    -> Java -> Interview

Valid order:
Maths, Java, DSA, Algorithms, Interview
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Prerequisites, dependencies, build order, course scheduling, DAG.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A node with no remaining prerequisites is safe to do next. Kahn's algorithm repeatedly takes such nodes. If none are available before all nodes are processed, a cycle exists.

---

## 5. Step-by-step method

1. Compute indegree. 2. Queue all zero-indegree nodes. 3. Remove one. 4. Decrease neighbor indegrees. 5. Queue newly zero nodes. 6. If processed count < V, cycle exists.

---

## 6. Small example / dry run

If A→B and B→C, A has indegree 0. Process A → B becomes 0 → process B → C becomes 0.

---

## 7. Java implementation

```java
Queue<Integer> q = new ArrayDeque<>();
for (int u = 0; u < n; u++)
    if (indegree[u] == 0) q.offer(u);

int count = 0;
while (!q.isEmpty()) {
    int u = q.poll();
    count++;

    for (int v : graph[u]) {
        if (--indegree[v] == 0)
            q.offer(v);
    }
}

boolean hasCycle = count != n;
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

- Forgetting cycle detection.\n- Confusing directed and undirected graphs.\n- Reducing indegree of the wrong node.

---

## 10. Real interview / real-world examples

- Course prerequisites.\n- Software build dependencies.\n- Job/task scheduling.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Course Schedule; roadmap Topological Sort.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Topological Sort**?

Write your answer here:

> 

