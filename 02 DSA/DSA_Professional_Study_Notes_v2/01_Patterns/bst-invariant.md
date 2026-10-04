# BST Invariant

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** The ordering rule that all left-subtree keys are smaller and right-subtree keys are larger, under a chosen duplicate policy.

---

## 1. Learn this first — in one minute

### What is BST Invariant?

The ordering rule that all left-subtree keys are smaller and right-subtree keys are larger, under a chosen duplicate policy.

### Real-world analogy

A sorted filing cabinet where every drawer split preserves the rule that everything left is smaller and everything right is larger.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
        8
       / \
   < 8     > 8
   /         \
 <4...      >12...
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

BST validation, search, insertion, kth smallest, predecessor/successor.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The invariant lets search discard an entire subtree. Inorder traversal exposes sorted order.

---

## 5. Step-by-step method

For validation, carry an allowed `(min,max)` range rather than checking only parent-child values. For kth smallest, inorder count gives sorted rank.

---

## 6. Small example / dry run

A node 7 under a 10→right subtree is invalid if it lies in the range requiring values >10.

---

## 7. Java implementation

```java
boolean valid(TreeNode root, long lo, long hi) {
    if (root == null) return true;
    if (root.val <= lo || root.val >= hi) return false;
    return valid(root.left, lo, root.val)
        && valid(root.right, root.val, hi);
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
| Time | O(n) for validation; O(h) for search |
| Extra space | O(h) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Checking only direct children.\n- Integer boundary overflow; use long bounds.

---

## 10. Real interview / real-world examples

- Ordered indexes.\n- Ranked sets.

---

## 11. Problems from your roadmap that connect to this

Roadmap BST.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **BST Invariant**?

Write your answer here:

> 

