# Disjoint Set Union (DSU / Union-Find)

> **Classification:** Data Structure  
> **Category:** Set-partition / connectivity  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Disjoint Set Union (DSU / Union-Find)?

DSU maintains a collection of disjoint groups and supports finding which group an element belongs to and merging two groups efficiently.

### The one sentence to remember

**MST & DSU, Disjoint Set. Problems: Kruskal MST, Number of Provinces-style connectivity.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
Initial:
1   2   3   4

union(1,2):
  1
  |
  2

union(3,4):
  3
  |
  4

find(1) == find(2) -> same group
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A set of friend groups. Initially everyone is separate. When two people become connected, merge their groups. You repeatedly ask whether two people belong to the same group.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it for dynamic connectivity, grouping, cycle detection in undirected graphs, Kruskal's MST, and problems where components repeatedly merge.

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

Path compression makes future `find` operations very short. Union by rank/size prevents the parent tree from becoming unnecessarily deep.

### Core invariant / rule

Each element points toward a representative/root. `find(x)` returns the representative. `union(a,b)` connects the two components if they are different.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

With path compression + union by size/rank:
- `find` → amortized nearly O(1), formally O(α(n))
- `union` → amortized nearly O(1)
- Space → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Start with 1,2,3 separate. `union(1,2)` makes them one component. `find(1)` and `find(2)` now return the same root. If you attempt another edge connecting 1 and 2, DSU detects that it would stay inside the same component.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
class DSU {
    int[] parent;
    int[] size;

    DSU(int n) {
        parent = new int[n];
        size = new int[n];

        for (int i = 0; i < n; i++) {
            parent[i] = i;
            size[i] = 1;
        }
    }

    int find(int x) {
        if (parent[x] == x) return x;
        return parent[x] = find(parent[x]); // path compression
    }

    boolean union(int a, int b) {
        int ra = find(a);
        int rb = find(b);

        if (ra == rb) return false;

        if (size[ra] < size[rb]) {
            int t = ra; ra = rb; rb = t;
        }

        parent[rb] = ra;
        size[ra] += size[rb];
        return true;
    }
}
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

**Amortized:** O(α(n)) per operation with both optimizations. **Space:** O(n). α(n) grows so slowly that it is effectively constant for practical input sizes.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Forgetting path compression.
- Unioning raw nodes instead of their roots.
- Confusing DSU with a general graph traversal structure.
- Using DSU when you need actual shortest paths.

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

- Network connectivity.
- Friend/community grouping.
- Kruskal's minimum spanning tree.
- Image/component merging.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Implement find + union with both optimizations and explain why Kruskal needs DSU.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **DSU vs DFS/BFS:** DSU excels when components repeatedly merge; BFS/DFS is better for exploring current graph structure.
- **DSU vs graph adjacency list:** DSU does not preserve all neighbor relationships.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Disjoint Set Union (DSU / Union-Find) solve?
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

**MST & DSU, Disjoint Set. Problems: Kruskal MST, Number of Provinces-style connectivity.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
