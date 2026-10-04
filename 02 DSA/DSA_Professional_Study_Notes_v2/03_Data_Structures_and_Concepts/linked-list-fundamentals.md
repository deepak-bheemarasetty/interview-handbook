# Linked List Fundamentals

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** A node-based sequence where each node stores a value and a reference to another node.

---

## 1. Learn this first — in one minute

### What is Linked List Fundamentals?

A node-based sequence where each node stores a value and a reference to another node.

### Real-world analogy

A treasure hunt where each clue tells you where the next clue is. You cannot jump directly to clue 50 without following links.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
head
 ↓
[10|•] -> [20|•] -> [30|null]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Pointer manipulation, dynamic insertion/deletion, no random access requirement.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Linked lists make local insertion/deletion cheap when the relevant node pointer is known, but finding an index requires traversal.

---

## 5. Step-by-step method

Maintain references carefully. Save `next` before changing pointers. Use dummy nodes to simplify head insertion/removal.

---

## 6. Small example / dry run

To delete 20, connect 10 directly to 30: `[10] -> [30]`.

---

## 7. Java implementation

```java
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) { this.val = val; }
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
| Time | Access by index O(n); insert/delete after known node O(1) |
| Extra space | O(n) for nodes |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Losing the rest of the list.\n- Null-pointer dereference.\n- Returning wrong head after modification.

---

## 10. Real interview / real-world examples

- Playlists where items point to next item.\n- Browser history concepts (though doubly linked lists are more suitable).

---

## 11. Problems from your roadmap that connect to this

Roadmap Linked List.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Linked List Fundamentals**?

Write your answer here:

> 

