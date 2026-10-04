# Linked List

> **Classification:** Data Structure  
> **Category:** Linked / node-based linear structure  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Linked List?

A linked list stores elements in nodes connected by references. A singly linked list has a `next` reference; a doubly linked list adds a `prev` reference.

### The one sentence to remember

**Singly/Doubly LL. Problems: Reverse Linked List, Middle of Linked List, Linked List Cycle, Merge Two Sorted Lists, Remove Nth Node From End.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
head
  |
  v
+----+------+    +----+------+    +----+------+
| 10 | next | -> | 20 | next | -> | 30 | null |
+----+------+    +----+------+    +----+------+

Doubly linked:
prev <-> node <-> next
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A treasure hunt where each clue tells you where the next clue is. You can follow links, but you cannot jump directly to clue number 50.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when nodes must be inserted/removed through references and random indexed access is not the main requirement. It is especially important for pointer-manipulation interview problems.

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

No shifting of all later elements is required when inserting/removing at a known location. The trade-off is that reaching an index requires following links one by one.

### Core invariant / rule

A singly linked list node points forward. A doubly linked list node points both directions. Losing a reference can disconnect the remaining list.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- Access index → O(n)
- Search → O(n)
- Insert after known node → O(1)
- Delete after known predecessor → O(1)
- Insert at head → O(1)
- Find middle with fast/slow → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

For `1 → 2 → 3`, save node 2 before changing node 1's `next`. Point 1 back to null. Move forward. Then point 2 to 1, then 3 to 2. Final list is `3 → 2 → 1`.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
class ListNode {
    int val;
    ListNode next;

    ListNode(int val) {
        this.val = val;
    }
}

// Reverse a singly linked list
ListNode prev = null;
ListNode cur = head;

while (cur != null) {
    ListNode next = cur.next;
    cur.next = prev;
    prev = cur;
    cur = next;
}

head = prev;
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

**Index access/search:** O(n). **Known-node insertion/deletion:** O(1). **Traversal/reversal:** O(n). **Space:** O(n) for nodes; iterative reverse uses O(1) auxiliary space.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Losing `cur.next` before changing it.
- Returning the old head after reversal.
- Forgetting null cases.
- Mixing up `prev`, `cur`, and `next`.

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

- Music playlists with explicit links.
- LRU cache implementations often use a doubly linked list plus HashMap.
- Browser/history-style navigation can use linked structures.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Reverse a list on paper with three pointers and explain why random access is O(n).

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Linked List vs ArrayList:** linked list favors local pointer changes; ArrayList favors indexed access.
- **Singly vs Doubly:** doubly supports backward navigation but uses more memory.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Linked List solve?
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

**Singly/Doubly LL. Problems: Reverse Linked List, Middle of Linked List, Linked List Cycle, Merge Two Sorted Lists, Remove Nth Node From End.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
