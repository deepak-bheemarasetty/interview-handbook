# Queue and Deque

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** A queue is FIFO; a deque supports insertion/removal from both ends.

---

## 1. Learn this first — in one minute

### What is Queue and Deque?

A queue is FIFO; a deque supports insertion/removal from both ends.

### Real-world analogy

A normal ticket line is FIFO. A deque is like a double-ended line where people can enter/leave from either side.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Queue:
front -> [A][B][C] <- back
poll A

Deque:
front <-> [A][B][C] <-> back
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

BFS, scheduling, sliding windows, monotonic deque.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

FIFO is exactly what level-order BFS needs: nodes discovered earlier are processed earlier.

---

## 5. Step-by-step method

Queue with offer/poll. Deque with offerFirst/offerLast/pollFirst/pollLast.

---

## 6. Small example / dry run

Queue A,B,C: poll A, then B. Deque can remove C from the back.

---

## 7. Java implementation

```java
Queue<Integer> q = new ArrayDeque<>();
q.offer(1);
q.offer(2);
int x = q.poll();

Deque<Integer> dq = new ArrayDeque<>();
dq.offerLast(1);
dq.offerFirst(2);
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
| Time | O(1) for end operations |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using the wrong end for a monotonic deque.\n- Calling remove/peek without checking emptiness.

---

## 10. Real interview / real-world examples

- Print-job scheduling.\n- BFS.\n- Sliding window maximum.

---

## 11. Problems from your roadmap that connect to this

Roadmap Queue/Deque.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Queue and Deque**?

Write your answer here:

> 

