# Kahn's Topological Sort

> **Classification:** Algorithm  
> **Purpose:** A BFS-style topological sorting algorithm based on indegrees.

---

## 1. Learn this first — in one minute

### What is Kahn's Topological Sort?

A BFS-style topological sorting algorithm based on indegrees.

### Real-world analogy

In a project, start tasks that have no remaining prerequisites. Completing one task may unlock others.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A -> C
B -> C -> D

indegree:
A=0 B=0 C=2 D=1

queue: A,B
remove A -> C=1
remove B -> C=0 -> queue C
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Prerequisites, DAG, dependency scheduling.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Zero-indegree vertices have no unresolved prerequisites, so they can safely be placed next.

---

## 5. Step-by-step method

Compute indegrees. Queue zeros. Repeatedly remove, output, decrement neighbors. If fewer than V nodes are output, cycle exists.

---

## 6. Small example / dry run

A and B are prerequisites of C. Both must be processed before C reaches indegree 0.

---

## 7. Java implementation

```java
Queue<Integer> q = new ArrayDeque<>();
for (int i=0;i<n;i++)
    if (indegree[i]==0) q.offer(i);

List<Integer> order = new ArrayList<>();

while(!q.isEmpty()){
    int u=q.poll();
    order.add(u);
    for(int v: graph[u])
        if(--indegree[v]==0) q.offer(v);
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

- Not detecting cycles.\n- Forgetting to decrement all outgoing edges.

---

## 10. Real interview / real-world examples

- Course scheduling.\n- Build systems.\n- CI/CD dependency ordering.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Course Schedule.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Kahn's Topological Sort**?

Write your answer here:

> 

