# Heap / Top-K

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pattern for repeatedly keeping the best K candidates or extracting the current minimum/maximum efficiently.

---

## 1. Learn this first — in one minute

### What is Heap / Top-K?

A pattern for repeatedly keeping the best K candidates or extracting the current minimum/maximum efficiently.

### Real-world analogy

A competition organizer who only needs the top 10 players. Instead of sorting millions of players completely, keep a small top-10 shortlist and remove the weakest whenever a new candidate enters.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Need top 3 largest:

7  -> [7]
2  -> [2,7]
9  -> [2,7,9]
4  -> [4,7,9]  (2 removed)

min-heap root = weakest among retained top 3
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Kth largest/smallest; top K; streaming data; repeatedly choose current min/max; merge K sorted sources.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A size-K min-heap for top-K largest stores exactly the K strongest seen so far. Its root is the weakest member of that shortlist, so it is the first one to remove when a better candidate arrives.

---

## 5. Step-by-step method

1. Pick heap orientation. 2. Insert candidate. 3. If size > K, remove the least useful candidate. 4. At the end, the heap contains the desired K.

---

## 6. Small example / dry run

For `[7,2,9,4]`, K=3: keep 7,2,9; when 4 arrives, remove 2 because it is the smallest among the four.

---

## 7. Java implementation

```java
PriorityQueue<Integer> pq = new PriorityQueue<>();

for (int x : nums) {
    pq.offer(x);
    if (pq.size() > k) pq.poll();
}

int kthLargest = pq.peek();
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
| Time | O(n log k) for bounded heap |
| Extra space | O(k) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using max-heap when min-heap is needed for top-K largest.\n- Forgetting to bound heap size.\n- Assuming the heap contents are fully sorted.

---

## 10. Real interview / real-world examples

- Top K salaries.\n- K most frequent search terms.\n- K nearest delivery locations.\n- Streaming leaderboard.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Kth Largest Element, Top K Frequent Elements.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Heap / Top-K**?

Write your answer here:

> 

