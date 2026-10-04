# Binary Tree

> **Classification:** Data Structure  
> **Category:** Hierarchical / tree  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Binary Tree?

A binary tree is a hierarchical structure in which each node has at most two children, usually called left and right.

### The one sentence to remember

**Binary Trees, Tree recursion. Problems: Binary Tree Level Order Traversal, Maximum Depth, Diameter, Lowest Common Ancestor.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
          8
        /   \
       4     12
      / \      \
     2   6      15

Each node:
 value + left + right
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A family or organization chart where each person can have up to two direct branches. To inspect a department, you recursively inspect its subdepartments.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when data is hierarchical, when recursive subtree reasoning is natural, or when problems mention depth, height, paths, levels, ancestors, or traversals.

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

A tree contains smaller trees inside it. This recursive structure makes DFS and tree DP natural. BFS processes nodes by level.

### Core invariant / rule

There is one root in a non-empty tree, every non-root node has one parent, and there is exactly one path from the root to each node in a tree.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- DFS traversals → O(n)
- BFS level traversal → O(n)
- Height → O(n)
- Search in an arbitrary binary tree → O(n)
- Space for recursive DFS → O(h), where h is height

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

For a leaf, both children are null, so height is 1 under this convention. For node 4, height is 1 + max(height(2), height(6)) = 2. The root combines the heights of both subtrees.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;

    TreeNode(int val) {
        this.val = val;
    }
}

int height(TreeNode node) {
    if (node == null) return 0;

    return 1 + Math.max(
        height(node.left),
        height(node.right)
    );
}
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

**Traversal/height:** O(n). **Recursive auxiliary space:** O(h). A balanced tree has h≈log n; a completely skewed tree can have h≈n.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Mixing height measured in nodes vs edges.
- Forgetting null base cases.
- Accidentally traversing the same subtree repeatedly, causing O(n²).

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

- File/folder hierarchies.
- Organization structures.
- Expression trees.
- Decision trees.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Perform preorder/inorder/postorder/level-order traversal and derive height recursively.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Binary Tree vs BST:** a binary tree has no inherent ordering; a BST has an ordering invariant.
- **Tree vs Graph:** a tree is a connected acyclic graph with a hierarchical interpretation.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Binary Tree solve?
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

**Binary Trees, Tree recursion. Problems: Binary Tree Level Order Traversal, Maximum Depth, Diameter, Lowest Common Ancestor.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
