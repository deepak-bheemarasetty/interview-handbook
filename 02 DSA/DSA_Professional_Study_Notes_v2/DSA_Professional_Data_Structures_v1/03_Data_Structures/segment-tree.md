# Segment Tree

> **Classification:** Data Structure  
> **Category:** Advanced range-query tree  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Segment Tree?

A segment tree recursively divides an array into intervals and stores an aggregate for each interval, allowing range queries and point updates in O(log n).

### The one sentence to remember

**Fenwick/Segment Tree. Advanced DS. Range sum/query, point update, lazy propagation overview.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
Array: [2 1 3 4 5 6]

             [1..6]
            /      \
        [1..3]    [4..6]
        /   \      /   \
      [1..2][3] [4..5][6]

Each node summarizes its interval.
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A manager divides a warehouse into sections, each section stores a summary, and larger sections summarize smaller sections. A query only visits the sections needed for its requested range.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when many range queries and updates are required, especially for sum/min/max/gcd or other mergeable operations where prefix sums/Fenwick are insufficient.

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

A query range can be decomposed into a small number of segment nodes. Updates modify only nodes whose intervals contain the changed index.

### Core invariant / rule

Each node represents an interval. The parent value is obtained by merging its children's values. The merge operation should match the query operation.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- Build → O(n)
- Point update → O(log n)
- Range query → O(log n)
- Space → O(n), commonly about 4n in a recursive implementation

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

For a query `[2,5]`, the tree does not scan every element blindly. It combines complete stored intervals that fit inside the query and recursively explores only partially overlapping intervals.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
class SegmentTree {
    int n;
    long[] tree;

    SegmentTree(int[] a) {
        n = a.length;
        tree = new long[4 * n];
        build(1, 0, n - 1, a);
    }

    void build(int node, int l, int r, int[] a) {
        if (l == r) {
            tree[node] = a[l];
            return;
        }

        int mid = (l + r) / 2;
        build(node * 2, l, mid, a);
        build(node * 2 + 1, mid + 1, r, a);
        tree[node] = tree[node * 2] + tree[node * 2 + 1];
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

**Build:** O(n). **Point update:** O(log n). **Range query:** O(log n). **Space:** O(n), often implemented with an array of size around 4n.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Wrong overlap conditions.
- Forgetting to update parent nodes after changing a child.
- Mixing inclusive/exclusive interval conventions.
- Building a segment tree when prefix sum/Fenwick is sufficient.

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

- Live dashboards with changing range statistics.
- Competitive programming range queries.
- Scheduling/resource aggregation.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Draw the interval decomposition and explain why only O(log n) nodes are visited along each relevant boundary.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Segment Tree vs Fenwick:** segment tree is more general; Fenwick is simpler for suitable prefix/range aggregates.
- **Segment Tree vs Prefix Sum:** segment tree supports updates efficiently; prefix sum is simpler for static data.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Segment Tree solve?
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

**Fenwick/Segment Tree. Advanced DS. Range sum/query, point update, lazy propagation overview.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
