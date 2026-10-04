# Merge Two Sorted Linked Lists

> **Classification:** Algorithm  
> **Purpose:** Combines two sorted linked lists into one sorted linked list by repeatedly choosing the smaller current node.

---

## 1. Learn this first — in one minute

### What is Merge Two Sorted Linked Lists?

Combines two sorted linked lists into one sorted linked list by repeatedly choosing the smaller current node.

### Real-world analogy

Two checkout lines are each already ordered by arrival time; merge them by always taking the person who arrived earlier.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A: 1 -> 4 -> 7
B: 2 -> 3 -> 8

take 1
take 2
take 3
take 4
...
=> 1 -> 2 -> 3 -> 4 -> 7 -> 8
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Two sorted linked lists; merge step of merge sort.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Because both heads are the smallest remaining values in their lists, the smaller head must be the next global smallest.

---

## 5. Step-by-step method

Use dummy node. Compare heads. Attach smaller. Advance chosen list. Append remainder.

---

## 6. Small example / dry run

Compare 1 and 2 → take 1; compare 4 and 2 → take 2; continue.

---

## 7. Java implementation

```java
ListNode dummy = new ListNode(0);
ListNode tail = dummy;

while (a != null && b != null) {
    if (a.val <= b.val) {
        tail.next = a;
        a = a.next;
    } else {
        tail.next = b;
        b = b.next;
    }
    tail = tail.next;
}
tail.next = (a != null) ? a : b;

return dummy.next;
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
| Time | O(n+m) |
| Extra space | O(1) auxiliary |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting to move chosen pointer.\n- Returning dummy instead of dummy.next.

---

## 10. Real interview / real-world examples

- Merging sorted event streams.\n- Merge sort on linked lists.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Merge Two Sorted Lists.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Merge Two Sorted Linked Lists**?

Write your answer here:

> 

