# Fenwick Tree (Binary Indexed Tree)

> **Classification:** Algorithm  
> **Purpose:** Supports point updates and prefix-sum queries in O(log n) using a compact tree encoded inside an array.

---

## 1. Learn this first — in one minute

### What is Fenwick Tree (Binary Indexed Tree)?

Supports point updates and prefix-sum queries in O(log n) using a compact tree encoded inside an array.

### Real-world analogy

A payroll system where each summary box stores a block of employees. To get a cumulative salary, combine only the few blocks covering the prefix instead of summing every employee.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
index: 1 2 3 4 5 6 7 8
BIT blocks:
1
2 -> [1..2]
4 -> [1..4]
8 -> [1..8]

prefix query jumps downward by lowbit
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Many point updates + prefix/range sums; values change over time.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Each index stores the sum of a specific range determined by its lowest set bit. Query moves backward removing lowbits; update moves forward adding lowbits.

---

## 5. Step-by-step method

Use 1-based indices. Update: `i += i & -i`. Query: `i -= i & -i`. Range sum = prefix(r)-prefix(l-1).

---

## 6. Small example / dry run

To query prefix 7, add BIT[7], then move 7→6→4→0. Only O(log n) stored blocks are needed.

---

## 7. Java implementation

```java
class Fenwick {
    int[] bit;

    Fenwick(int n) { bit = new int[n + 1]; }

    void add(int i, int delta) {
        for (; i < bit.length; i += i & -i)
            bit[i] += delta;
    }

    int sum(int i) {
        int ans = 0;
        for (; i > 0; i -= i & -i)
            ans += bit[i];
        return ans;
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
| Time | O(log n) per point update/query |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting 1-based indexing.\n- Using `i += i & -i` incorrectly.\n- Trying to handle arbitrary range updates without understanding which variant is needed.

---

## 10. Real interview / real-world examples

- Live scoreboard totals.\n- Dynamic frequency counts.\n- Online range-sum queries.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced DS: Fenwick/Segment Tree.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Fenwick Tree (Binary Indexed Tree)**?

Write your answer here:

> 

