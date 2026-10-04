# Reverse Linked List

> **Classification:** Algorithm  
> **Purpose:** Reverses the direction of every linked-list pointer.

---

## 1. Learn this first — in one minute

### What is Reverse Linked List?

Reverses the direction of every linked-list pointer.

### Real-world analogy

Reverse a line of people holding hands: each person must let go of the person ahead and hold the previous person instead.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Before: 1 -> 2 -> 3 -> null
After:  null <- 1 <- 2 <- 3
                    ^
                  head
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Reverse whole list or reverse a segment.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

At each node, save the original next node before redirecting `curr.next` to `prev`.

---

## 5. Step-by-step method

Keep `prev=null`, `curr=head`. Save next; reverse pointer; advance prev/curr.

---

## 6. Small example / dry run

At node 2, save node 3, set 2.next=1, then continue to 3.

---

## 7. Java implementation

```java
ListNode prev = null, curr = head;

while (curr != null) {
    ListNode next = curr.next;
    curr.next = prev;
    prev = curr;
    curr = next;
}
return prev;
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

- Losing the rest of the list by not saving next.\n- Returning old head instead of prev.

---

## 10. Real interview / real-world examples

- Reversing a sequence of linked records.\n- Used inside palindrome/list manipulation problems.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Reverse Linked List.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Reverse Linked List**?

Write your answer here:

> 

