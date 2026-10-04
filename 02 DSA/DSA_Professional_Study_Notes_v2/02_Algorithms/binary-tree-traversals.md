# Binary Tree Traversals

> **Classification:** Algorithm  
> **Purpose:** Systematic ways to visit every node in a binary tree: preorder, inorder, postorder, and level order.

---

## 1. Learn this first — in one minute

### What is Binary Tree Traversals?

Systematic ways to visit every node in a binary tree: preorder, inorder, postorder, and level order.

### Real-world analogy

Touring a family tree: preorder visits parent before children; inorder visits left branch, parent, right branch; postorder visits children before parent; level order visits by generation.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
      A
     / \
    B   C
   / \
  D   E

Pre:  A B D E C
In:   D B E A C
Post: D E B C A
Level:A B C D E
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Tree traversal, serialization, BST sorted order, height/level problems.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The traversal order is determined by when the current node is processed relative to its left/right subtrees.

---

## 5. Step-by-step method

Choose traversal. Recursively/iteratively visit left/right. For level order use a queue.

---

## 6. Small example / dry run

For the tree shown, inorder produces D,B,E,A,C. In a BST this order is sorted.

---

## 7. Java implementation

```java
void inorder(TreeNode root) {
    if (root == null) return;
    inorder(root.left);
    visit(root);
    inorder(root.right);
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
| Time | O(n) |
| Extra space | O(h) recursion for DFS; O(width) for BFS |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Mixing traversal orders.\n- Stack overflow on deep trees.\n- Assuming inorder is sorted for every binary tree; it is sorted only for BSTs.

---

## 10. Real interview / real-world examples

- Folder hierarchy traversal.\n- Expression trees.\n- BST sorted output.

---

## 11. Problems from your roadmap that connect to this

Roadmap Binary Trees; Problem Bank Level Order.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Binary Tree Traversals**?

Write your answer here:

> 

