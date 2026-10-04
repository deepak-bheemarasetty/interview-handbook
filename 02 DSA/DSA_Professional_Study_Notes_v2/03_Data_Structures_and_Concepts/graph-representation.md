# Graph Representation

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** Ways to store graph vertices and edges so traversal and algorithms can access neighbors efficiently.

---

## 1. Learn this first — in one minute

### What is Graph Representation?

Ways to store graph vertices and edges so traversal and algorithms can access neighbors efficiently.

### Real-world analogy

A city map can be stored as a list of roads for each city (adjacency list) or a giant table saying whether every pair has a direct road (adjacency matrix).

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Edges: A-B, A-C, B-D

Adjacency list:
A -> B,C
B -> A,D
C -> A
D -> B
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Any graph problem; choose representation based on V/E density and required operations.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Adjacency lists use O(V+E) memory and are ideal for sparse graphs. Matrices use O(V²) memory but make edge-existence checks O(1).

---

## 5. Step-by-step method

For sparse graphs, create `List<Integer>[]`. For weighted graphs, store Edge objects. For dense small graphs, a matrix may be simpler.

---

## 6. Small example / dry run

A-B and A-C means A's list contains B,C; undirected graphs store both directions.

---

## 7. Java implementation

```java
List<Integer>[] graph = new ArrayList[n];
for (int i=0;i<n;i++) graph[i]=new ArrayList<>();

graph[0].add(1);
graph[1].add(0); // undirected
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
| Time | Adjacency list traversal O(V+E); matrix edge lookup O(1) |
| Extra space | List O(V+E); matrix O(V²) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting reverse edges in undirected graphs.\n- Using matrix for huge sparse graphs.

---

## 10. Real interview / real-world examples

- Road maps.\n- Social networks.\n- Dependency graphs.

---

## 11. Problems from your roadmap that connect to this

Roadmap Graph Fundamentals.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Graph Representation**?

Write your answer here:

> 

