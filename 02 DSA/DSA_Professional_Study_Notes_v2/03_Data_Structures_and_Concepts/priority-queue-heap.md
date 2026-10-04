# Priority Queue / Heap

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** A heap-backed structure that efficiently returns the smallest or largest priority element.

---

## 1. Learn this first — in one minute

### What is Priority Queue / Heap?

A heap-backed structure that efficiently returns the smallest or largest priority element.

### Real-world analogy

An emergency room: the next patient is selected by priority, not arrival order.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Min-heap:
        1
      /   \
     3     2
    / \
   7   5

peek -> 1
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Repeated min/max extraction; top K; scheduling; Dijkstra; Prim.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A heap maintains only the parent-child priority relation, not complete sorting. That is enough to guarantee the root is the next best candidate.

---

## 5. Step-by-step method

Insert O(log n), peek O(1), remove root O(log n). Java PriorityQueue is a min-heap.

---

## 6. Small example / dry run

Insert 5,2,7,1 → root becomes 1. Poll removes 1 and restores heap order.

---

## 7. Java implementation

```java
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
minHeap.offer(5);
minHeap.offer(2);
minHeap.offer(7);
int smallest = minHeap.poll();

PriorityQueue<Integer> maxHeap =
    new PriorityQueue<>(Comparator.reverseOrder());
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
| Time | Offer/poll O(log n), peek O(1) |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Assuming heap iteration is sorted.\n- Forgetting Java defaults to min-heap.

---

## 10. Real interview / real-world examples

- Emergency priorities.\n- Task scheduling.\n- Top K selection.

---

## 11. Problems from your roadmap that connect to this

Roadmap Heap / Priority Queue.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Priority Queue / Heap**?

Write your answer here:

> 

