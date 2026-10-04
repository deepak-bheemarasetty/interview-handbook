# Graph

> **Classification:** Data Structure  
> **Category:** Non-linear / relationship structure  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Graph?

A graph represents entities as vertices and relationships as edges. Edges may be directed/undirected and weighted/unweighted.

### The one sentence to remember

**Graph Fundamentals, Shortest Paths, MST & DSU, Topological Sort, Advanced Graphs.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
A ---- B ---- D
|      |
|      |
C ---- E

Vertices: A B C D E
Edges: relationships between them
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A road map: cities are vertices and roads are edges. A social network is another example: people are vertices and relationships are edges.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use graphs whenever the problem describes connections, routes, dependencies, friendships, transformations, networks, or states connected by transitions.

### Recognition checklist

- What operation needs to be fast?
- Do I need random/indexed access?
- Do I need key → value lookup?
- Do I need membership/duplicate checking?
- Do I need first-in-first-out or last-in-first-out behavior?
- Do I repeatedly need the smallest/largest item?
- Is the data hierarchical?
- Is the data connected by relationships?
- Do I need dynamic connectivity or range queries?

The exact questions depend on the structure, but this checklist prevents choosing a data structure just because it is familiar.

---

## 5. Why does it work?

Graphs model relationships directly. Algorithms such as BFS, DFS, Dijkstra, MST, and topological sorting exploit different graph properties.

### Core invariant / rule

You must know whether edges are directed, weighted, and whether the graph can contain cycles. For undirected graphs, an edge usually appears in both adjacency lists.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

Adjacency list:
- Memory → O(V + E)
- Traverse all neighbors → O(V + E) overall

Adjacency matrix:
- Memory → O(V²)
- Check whether edge (u,v) exists → O(1)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

For an undirected edge A-B, store B in A's neighbor list and A in B's neighbor list. Starting from A, BFS/DFS can then discover B and continue through B's neighbors.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
// Undirected adjacency list
List<Integer>[] graph = new ArrayList[n];

for (int i = 0; i < n; i++) {
    graph[i] = new ArrayList<>();
}

graph[0].add(1);
graph[1].add(0); // reverse edge
```

### Code walkthrough

1. Identify the object/array/node that stores the actual data.
2. Identify the references/indexes that connect or organize the data.
3. Identify the operation being performed.
4. Check which invariant must remain true.
5. Check whether Java's built-in implementation already provides the required behavior.

For interviews, you should understand both the **concept** and the Java API commonly used for it.

---

## 9. Complexity

**Adjacency list:** O(V+E) memory and traversal. **Matrix:** O(V²) memory, O(1) edge lookup. Choice depends on density and operations.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Forgetting reverse edges in undirected graphs.
- Forgetting visited state in cyclic graphs.
- Confusing vertex count V with edge count E.
- Using an adjacency matrix for a huge sparse graph.

### Always test

- Empty structure
- One element
- Duplicate values
- Minimum/maximum values
- Removing the first/last element
- Removing a missing element
- Very large input
- Null references where applicable

---

## 11. Real-world applications

- Maps and navigation.
- Social networks.
- Computer networks.
- Build/dependency systems.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Build both representations, identify directed/undirected/weighted graphs, and choose BFS/DFS from the problem structure.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Graph vs Tree:** every tree is a special graph; general graphs can have cycles and multiple paths.
- **Adjacency list vs matrix:** sparse vs dense/access-pattern trade-off.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Graph solve?
2. What is its core invariant?
3. What are its main operations?
4. Why is each operation fast or slow?
5. What is the time complexity?
6. What is the space complexity?
7. When would you choose it over another structure?
8. What happens on empty input?
9. Can you implement the basic version in Java?
10. Can you recognize a problem that needs it from the wording alone?

### Mastery test

**Graph Fundamentals, Shortest Paths, MST & DSU, Topological Sort, Advanced Graphs.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
