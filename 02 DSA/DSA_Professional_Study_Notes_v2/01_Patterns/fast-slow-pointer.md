# Fast & Slow Pointer

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pointer pattern where two pointers move at different speeds, commonly used for linked-list cycles and finding the middle.

---

## 1. Learn this first — in one minute

### What is Fast & Slow Pointer?

A pointer pattern where two pointers move at different speeds, commonly used for linked-list cycles and finding the middle.

### Real-world analogy

Two runners on a circular track: one runs twice as fast. If a loop exists, the faster runner eventually catches the slower runner.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
1 -> 2 -> 3 -> 4 -> 5
          ↑         |
          |---------|

slow: 1 -> 2 -> 3 -> 4
fast: 1 -> 3 -> 5 -> 3 -> ...
                     ↑ meets slow
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Cycle detection, middle of linked list, repeated-state processes, O(1)-space requirement.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Different speeds amplify relative movement. In a cycle, the fast pointer gains one node per iteration relative to slow, so a meeting is inevitable.

---

## 5. Step-by-step method

1. Initialize both at head/start. 2. Move slow by one and fast by two. 3. If fast reaches null, no cycle. 4. If they meet, a cycle exists. 5. To find cycle entry, reset one pointer to head and move both one step.

---

## 6. Small example / dry run

For a list whose tail points back to node 3, slow moves 1→2→3→4..., fast moves 1→3→5→3..., eventually both occupy the same node.

---

## 7. Java implementation

```java
ListNode slow = head, fast = head;

while (fast != null && fast.next != null) {
    slow = slow.next;
    fast = fast.next.next;

    if (slow == fast) return true;
}
return false;
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

- Dereferencing `fast.next.next` without checking.\n- Comparing node values instead of node references for cycle detection.\n- Returning the wrong middle for even-sized lists without understanding the required convention.

---

## 10. Real interview / real-world examples

- Two runners on a circular track.\n- Detecting a repeated state in a simulation when extra memory is forbidden.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Middle of Linked List, Linked List Cycle; roadmap Linked List stage.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Fast & Slow Pointer**?

Write your answer here:

> 

