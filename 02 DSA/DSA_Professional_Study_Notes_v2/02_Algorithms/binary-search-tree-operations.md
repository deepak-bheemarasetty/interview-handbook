# Binary Search Tree Operations

> **Classification:** Algorithm  
> **Purpose:** Uses the BST invariant: every key in the left subtree is smaller and every key in the right subtree is larger (under the chosen duplicate policy).

---

## 1. Learn this first — in one minute

### What is Binary Search Tree Operations?

Uses the BST invariant: every key in the left subtree is smaller and every key in the right subtree is larger (under the chosen duplicate policy).

### Real-world analogy

A sorted filing cabinet where each decision sends you to the left or right section, eliminating half of the remaining search path in a balanced tree.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
        8
       / \
      4   12
     / \  / \
    2  6 10 14

search 10:
8 -> right -> 12 -> left -> 10
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Search/insert/delete in BST; validate BST; kth smallest.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The ordering invariant tells you which subtree can contain a target. Inorder traversal visits keys in sorted order.

---

## 5. Step-by-step method

Search/insert: compare and descend. Delete: leaf → remove; one child → replace by child; two children → replace with inorder successor/predecessor, then delete it.

---

## 6. Small example / dry run

Delete 8 from the example: choose successor 10, put 10 at root, then delete original 10.

---

## 7. Java implementation

```java
TreeNode insert(TreeNode root, int x) {
    if (root == null) return new TreeNode(x);

    if (x < root.val) root.left = insert(root.left, x);
    else if (x > root.val) root.right = insert(root.right, x);

    return root;
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
| Time | O(h); O(log n) average if balanced, O(n) worst |
| Extra space | O(h) recursive |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Assuming every BST is balanced.\n- Wrong duplicate policy.\n- Incorrect two-child deletion.

---

## 10. Real interview / real-world examples

- Ordered indexes.\n- Maintaining sorted sets conceptually.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Validate BST, Kth Smallest in BST; roadmap BST.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Binary Search Tree Operations**?

Write your answer here:

> 

