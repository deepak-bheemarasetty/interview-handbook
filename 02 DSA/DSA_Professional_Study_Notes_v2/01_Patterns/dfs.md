# DFS

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A traversal pattern that explores one branch as deeply as possible before returning and exploring another branch.

---

## 1. Learn this first — in one minute

### What is DFS?

A traversal pattern that explores one branch as deeply as possible before returning and exploring another branch.

### Real-world analogy

Exploring a building: follow one corridor to the end, return to the last junction, then take the next corridor.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
        A
      /   \
     B     C
    / \     \
   D   E     F

DFS example:
A -> B -> D -> back -> E -> back -> C -> F
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Connected components, islands, tree recursion, path existence, graph exploration.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

DFS naturally represents nested structure: solve the current node, then recursively solve each child/subproblem.

---

## 5. Step-by-step method

1. Visit node. 2. Mark visited. 3. Explore each unvisited neighbor recursively/with stack. 4. Return when branch is exhausted.

---

## 6. Small example / dry run

Starting A, go A→B→D. D has no unvisited neighbor, so return to B and explore E, then return to A and explore C.

---

## 7. Java implementation

```java
void dfs(int u) {
    visited[u] = true;

    for (int v : graph[u]) {
        if (!visited[v]) {
            dfs(v);
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
| Extra space | O(V) for visited + recursion/stack |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting visited in cyclic graphs.\n- Recursion stack overflow on very deep graphs.\n- Marking after recursive call instead of before.

---

## 10. Real interview / real-world examples

- Exploring all rooms reachable from an entrance.\n- Flood fill in an image.\n- Finding connected groups in a social network.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Number of Islands, Clone Graph, Maximum Depth of Binary Tree.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **DFS**?

Write your answer here:

> 

