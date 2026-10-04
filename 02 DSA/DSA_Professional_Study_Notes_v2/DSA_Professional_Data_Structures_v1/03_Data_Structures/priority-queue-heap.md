# Priority Queue / Heap

> **Classification:** Data Structure  
> **Category:** Heap-based priority structure  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Priority Queue / Heap?

A priority queue returns the element with the highest priority according to a comparator. Java's PriorityQueue is heap-backed and is a min-heap by default.

### The one sentence to remember

**Priority Queue, Heap / Top-K. Problems: Kth Largest Element, Top K Frequent Elements, Dijkstra.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
Min-heap shape

          1
        /   \
       3     2
      / \
     7   5

Parent <= children
peek() -> 1
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** An emergency room: the next person treated is determined by urgency, not simply by who arrived first.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when you repeatedly need the smallest/largest item, top K results, scheduling by priority, Dijkstra, merging sorted streams, or streaming median variants.

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

A heap does not fully sort all elements. It maintains just enough order so the root is the best-priority element and insertion/removal can restore the heap property efficiently.

### Core invariant / rule

For a min-heap, every parent is <= its children. For a max-heap, every parent is >= its children. The root is the minimum/maximum.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- peek → O(1)
- offer/insert → O(log n)
- poll/remove root → O(log n)
- build heap from n items → commonly O(n)
- arbitrary search → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Insert 5,2,7,1. The heap reorganizes itself so 1 reaches the root. Poll removes 1, then the remaining elements are rearranged to restore the heap property.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
import java.util.PriorityQueue;
import java.util.Comparator;

PriorityQueue<Integer> minHeap = new PriorityQueue<>();

minHeap.offer(5);
minHeap.offer(2);
minHeap.offer(7);
minHeap.offer(1);

System.out.println(minHeap.peek()); // 1
System.out.println(minHeap.poll()); // 1

PriorityQueue<Integer> maxHeap =
    new PriorityQueue<>(Comparator.reverseOrder());
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

**peek:** O(1). **insert/poll:** O(log n). **Space:** O(n).

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Assuming iterating PriorityQueue gives sorted order.
- Forgetting Java's default is a min-heap.
- Using a heap when a simple sort or prefix structure is enough.

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

- CPU/task scheduling.
- Emergency priority handling.
- Dijkstra's frontier.
- Top K analytics.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Build min/max heaps, solve Kth Largest and Top K Frequent, and explain O(log n) insertion.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **PriorityQueue vs Queue:** priority determines next item; FIFO determines next item in a normal queue.
- **Heap vs BST:** heap gives fast root priority; BST maintains ordered relationships useful for search/range operations.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Priority Queue / Heap solve?
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

**Priority Queue, Heap / Top-K. Problems: Kth Largest Element, Top K Frequent Elements, Dijkstra.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
