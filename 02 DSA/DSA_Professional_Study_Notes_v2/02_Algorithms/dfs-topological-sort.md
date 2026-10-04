# DFS Topological Sort

> **Classification:** Algorithm  
> **Purpose:** Produces a topological ordering using DFS postorder: a node is added after all its outgoing dependencies are processed.

---

## 1. Learn this first — in one minute

### What is DFS Topological Sort?

Produces a topological ordering using DFS postorder: a node is added after all its outgoing dependencies are processed.

### Real-world analogy

Finish all tasks needed by a task before writing that task onto the completed stack.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A -> B -> C

DFS A
  DFS B
    DFS C
    push C
  push B
push A

reverse stack = A,B,C
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

DAG ordering where DFS recursion is convenient; cycle detection with 3 states.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If all outgoing neighbors of u finish before u, then u can appear before them in the reversed finishing order.

---

## 5. Step-by-step method

Use states 0=unvisited, 1=visiting, 2=done. DFS neighbors. A visiting neighbor means a cycle. Push node after neighbors; reverse result.

---

## 6. Small example / dry run

C finishes first, then B, then A. Reversing gives A,B,C.

---

## 7. Java implementation

```java
boolean dfs(int u) {
    state[u] = 1;

    for (int v : graph[u]) {
        if (state[v] == 1) return false; // cycle
        if (state[v] == 0 && !dfs(v)) return false;
    }

    state[u] = 2;
    order.push(u);
    return true;
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

- Using only boolean visited and missing back edges.\n- Forgetting postorder/reversal.

---

## 10. Real interview / real-world examples

- Dependency resolution.\n- Build order.

---

## 11. Problems from your roadmap that connect to this

Roadmap Topological Sort.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **DFS Topological Sort**?

Write your answer here:

> 

