# Deque

> **Classification:** Data Structure  
> **Category:** Double-ended queue  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Deque?

A deque (double-ended queue) supports insertion and removal from both the front and the back.

### The one sentence to remember

**Queue & Deque; Monotonic Queue. Problem: Sliding Window Maximum.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
front                         back
  |                              |
  v                              v
<-> [ A ] <-> [ B ] <-> [ C ] <->
  |                              |
offerFirst                  offerLast
pollFirst                  pollLast
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A hallway with doors at both ends. People/items can enter or leave from either side.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when both ends matter: stack behavior, queue behavior, sliding-window maximum, monotonic deque, or algorithms that need controlled removal from either side.

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

Two-end operations avoid shifting the entire collection. A monotonic deque additionally keeps only candidates that can still become an answer.

### Core invariant / rule

The front and back are independently accessible for insertion/removal. The ordering inside the deque depends on how your algorithm maintains it.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- offerFirst/offerLast → O(1)
- pollFirst/pollLast → O(1)
- peekFirst/peekLast → O(1)
- arbitrary search → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Start empty. Add 10 at the back. Add 20 at the back. Add 5 at the front → `[5,10,20]`. Removing from the front gives 5; removing from the back then gives 20.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<Integer> dq = new ArrayDeque<>();

dq.offerLast(10);
dq.offerLast(20);
dq.offerFirst(5);

System.out.println(dq.pollFirst()); // 5
System.out.println(dq.pollLast());  // 20
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

- Mixing up first and last operations.
- Assuming a deque automatically stays sorted; it does not.
- Forgetting that ArrayDeque does not allow null elements.

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

- Sliding-window candidate storage.
- Double-ended task buffers.
- Implementing both stacks and queues.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Implement Sliding Window Maximum using a monotonic deque and explain why dominated candidates can be removed.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Deque vs Queue:** deque supports both ends; queue conceptually restricts insertion/removal to opposite ends.
- **Deque vs PriorityQueue:** deque has positional ends; priority queue chooses by priority.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Deque solve?
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

**Queue & Deque; Monotonic Queue. Problem: Sliding Window Maximum.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
