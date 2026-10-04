# DSU / Union-Find

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A data structure for maintaining groups that merge over time, with very fast connectivity checks using `find` and `union`.

---

## 1. Learn this first — in one minute

### What is DSU / Union-Find?

A data structure for maintaining groups that merge over time, with very fast connectivity checks using `find` and `union`.

### Real-world analogy

A school where students belong to clubs. When two clubs merge, all members become one group. You need to quickly answer whether two students are now in the same club.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Initially:
1   2   3   4

union(1,2):  1
              |
              2

union(3,4):  3
              |
              4

union(2,3):
      1
      |
      2
      |
      3
      |
      4
All same component.
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Dynamic connectivity, merging components, cycle detection in undirected graphs, Kruskal MST.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Each component is represented by a root. `find(x)` returns its root. If two roots differ, joining them merges two components. Path compression and union by size/rank keep the trees extremely shallow.

---

## 5. Step-by-step method

1. Initialize parent[i]=i. 2. `find` follows parents to root and compresses the path. 3. `union` finds two roots. 4. If different, attach the smaller tree to the larger.

---

## 6. Small example / dry run

For edges (1,2), (2,3), (1,3): first two edges merge components. The third finds both endpoints already have the same root, so it would create a cycle.

---

## 7. Java implementation

```java
int find(int x) {
    if (parent[x] != x)
        parent[x] = find(parent[x]);
    return parent[x];
}

void union(int a, int b) {
    a = find(a);
    b = find(b);
    if (a == b) return;

    if (size[a] < size[b]) {
        int t = a; a = b; b = t;
    }
    parent[b] = a;
    size[a] += size[b];
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
| Time | Amortized O(alpha(n)) per operation |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Unioning original nodes instead of roots.\n- Forgetting path compression.\n- Forgetting size/rank balancing.\n- Using DSU for problems requiring actual shortest paths or tree traversal.

---

## 10. Real interview / real-world examples

- Friend groups merging.\n- Network components becoming connected.\n- Detecting whether adding a cable creates a cycle.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Kruskal MST; roadmap MST & DSU and Disjoint Set.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **DSU / Union-Find**?

Write your answer here:

> 

