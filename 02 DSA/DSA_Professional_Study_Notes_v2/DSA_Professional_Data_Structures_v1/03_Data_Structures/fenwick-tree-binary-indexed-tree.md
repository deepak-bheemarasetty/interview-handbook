# Fenwick Tree (Binary Indexed Tree)

> **Classification:** Data Structure  
> **Category:** Advanced range-query structure  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Fenwick Tree (Binary Indexed Tree)?

A Fenwick Tree maintains prefix aggregates, especially sums, while supporting point updates and prefix/range queries in O(log n).

### The one sentence to remember

**Fenwick/Segment Tree. Advanced range-query structure.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
Array indexes:
1 2 3 4 5 6 7 8

Fenwick nodes store partial ranges:
1
2 -> [1..2]
4 -> [1..4]
8 -> [1..8]

prefix(7):
7 + 6's group + 4's group ...
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** Imagine a cashier system where instead of recounting every previous transaction for each report, selected groups of transactions are stored as reusable partial totals.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when you have many point updates and prefix/range sum queries, especially when O(n) per query is too slow.

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

Each Fenwick index stores a carefully chosen block whose size is determined by the lowest set bit. Prefix queries decompose a prefix into O(log n) such blocks.

### Core invariant / rule

Fenwick Trees are usually implemented with 1-based indexing. Update moves upward by adding the lowest set bit; query moves downward by subtracting it.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- Point update → O(log n)
- Prefix sum query → O(log n)
- Range sum `[l,r]` → O(log n) using prefix(r)-prefix(l-1)
- Space → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

With values `[2,1,3,4]` using indexes 1..4, `sum(3)` combines a few stored blocks rather than adding indexes 1,2,3 individually. A point update then changes only the Fenwick nodes whose stored ranges include that index.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
class Fenwick {
    int n;
    long[] bit;

    Fenwick(int n) {
        this.n = n;
        bit = new long[n + 1];
    }

    void add(int index, long delta) {
        for (; index <= n; index += index & -index) {
            bit[index] += delta;
        }
    }

    long sum(int index) {
        long ans = 0;
        for (; index > 0; index -= index & -index) {
            ans += bit[index];
        }
        return ans;
    }

    long rangeSum(int l, int r) {
        return sum(r) - sum(l - 1);
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

**Update/query:** O(log n). **Space:** O(n).

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Using 0-based indexes without adapting the implementation.
- Forgetting `index += index & -index` for updates.
- Using it for operations that do not support the needed aggregation.

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

- Live score totals.
- Frequency/count tracking over changing positions.
- Competitive-programming range-sum problems.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Implement update, prefix sum, and range sum without looking at the formula.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Fenwick vs Prefix Sum:** prefix sum has O(1) query but cannot efficiently handle arbitrary point updates; Fenwick handles updates in O(log n).
- **Fenwick vs Segment Tree:** Fenwick is simpler and lighter for suitable prefix/range aggregates; segment trees support broader query/update types.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Fenwick Tree (Binary Indexed Tree) solve?
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

**Fenwick/Segment Tree. Advanced range-query structure.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
