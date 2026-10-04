# Floyd Cycle Detection

> **Classification:** Algorithm  
> **Purpose:** Detects a cycle in a linked list using slow/fast pointers and can locate the cycle entry.

---

## 1. Learn this first — in one minute

### What is Floyd Cycle Detection?

Detects a cycle in a linked list using slow/fast pointers and can locate the cycle entry.

### Real-world analogy

Two runners on a circular track; the faster runner catches the slower one only if a loop exists.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
1 -> 2 -> 3 -> 4 -> 5
          ^         |
          |---------|

slow: 1,2,3,4,5...
fast: 1,3,5,4,3...
             ↑ meet
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Cycle detection without extra memory; find cycle start.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Inside a cycle, fast gains one node per iteration relative to slow, so they must meet. After meeting, equal-distance reasoning identifies the entry.

---

## 5. Step-by-step method

Move slow one and fast two until meeting/null. For entry, reset one to head and move both one step until they meet.

---

## 6. Small example / dry run

If tail points to node 3, the pointers eventually meet inside the loop. Resetting one to head makes their next meeting node 3.

---

## 7. Java implementation

```java
ListNode slow=head, fast=head;

do {
    if (fast == null || fast.next == null) return false;
    slow = slow.next;
    fast = fast.next.next;
} while (slow != fast);

return true;
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
| Time | O(n) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Comparing values instead of node references.\n- Unsafe fast-pointer access.

---

## 10. Real interview / real-world examples

- Detecting repeated states in deterministic processes.\n- Cycle detection in linked data.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Linked List Cycle.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Floyd Cycle Detection**?

Write your answer here:

> 

