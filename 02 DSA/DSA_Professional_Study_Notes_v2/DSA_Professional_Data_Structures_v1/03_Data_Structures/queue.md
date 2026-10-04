# Queue

> **Classification:** Data Structure  
> **Category:** Linear / FIFO  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Queue?

A queue is a First-In-First-Out structure. The earliest inserted element is processed first.

### The one sentence to remember

**Queue & Deque, BFS. Problems: Binary Tree Level Order Traversal, Rotting Oranges, Sliding Window Maximum.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
front                         back
  |                              |
  v                              v
+---+---+---+---+
| A | B | C | D |
+---+---+---+---+
  ^
poll/remove here
              ^
          offer/add here
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A ticket counter line: the person who arrives first should normally be served first.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it for BFS, task scheduling, producer-consumer workflows, and any problem where processing order follows arrival order.

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

FIFO guarantees that earlier-discovered items are processed before later items. This is exactly why BFS explores a graph level by level.

### Core invariant / rule

Elements enter at the rear and leave from the front. A circular queue can reuse freed positions in fixed storage.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- offer/enqueue → O(1)
- poll/dequeue → O(1)
- peek → O(1)
- search → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

After inserting 10,20,30, the front is 10. Poll removes 10, so 20 becomes the next element.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
import java.util.ArrayDeque;
import java.util.Queue;

Queue<Integer> q = new ArrayDeque<>();

q.offer(10);
q.offer(20);
q.offer(30);

System.out.println(q.poll()); // 10
System.out.println(q.peek()); // 20
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

**End operations:** O(1). **Space:** O(n).

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Removing from the wrong end.
- Using an ArrayList and repeatedly removing index 0, which causes O(n) shifts.
- Forgetting the queue may become empty.

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

- Print-job scheduling.
- Message processing.
- BFS in maps and games.
- Request buffering.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Implement BFS using a queue and explain why BFS finds shortest paths in unweighted graphs.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Queue vs Stack:** FIFO vs LIFO.
- **Queue vs PriorityQueue:** Queue follows arrival order; PriorityQueue follows priority.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Queue solve?
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

**Queue & Deque, BFS. Problems: Binary Tree Level Order Traversal, Rotting Oranges, Sliding Window Maximum.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
