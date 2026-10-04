# Low-Link Concepts

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A DFS pattern using discovery time (`tin`) and the earliest reachable ancestor (`low`) to identify graph vulnerabilities.

---

## 1. Learn this first — in one minute

### What is Low-Link Concepts?

A DFS pattern using discovery time (`tin`) and the earliest reachable ancestor (`low`) to identify graph vulnerabilities.

### Real-world analogy

A road inspector asks each branch: “How far back toward the main highway can you return without using the road I just came from?”

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
DFS tree:
u
|
v
|
w -- back edge --> ancestor(u)

low[v] tells how high v's subtree can climb back
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Bridges, articulation points, SCC-related graph analysis.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

`low[v]` summarizes whether a DFS subtree has an alternate route back to an ancestor. Comparing low with discovery times reveals whether removing an edge/vertex disconnects the graph.

---

## 5. Step-by-step method

Assign increasing tin. Initialize low=tin. Back edge updates low with ancestor tin. Child completion updates parent low.

---

## 6. Small example / dry run

If child v can return to u through another edge, low[v]≤tin[u], so u-v is not a bridge.

---

## 7. Java implementation

```java
tin[u] = low[u] = timer++;
// on DFS child v:
low[u] = Math.min(low[u], low[v]);
// on back edge to ancestor v:
low[u] = Math.min(low[u], tin[v]);
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

- Mixing bridge and articulation inequalities.\n- Incorrectly skipping parent edges with parallel edges.

---

## 10. Real interview / real-world examples

- Critical network analysis.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced Graphs.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Low-Link Concepts**?

Write your answer here:

> 

