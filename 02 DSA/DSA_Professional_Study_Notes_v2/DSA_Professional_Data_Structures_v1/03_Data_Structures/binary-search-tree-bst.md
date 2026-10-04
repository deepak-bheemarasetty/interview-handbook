# Binary Search Tree (BST)

> **Classification:** Data Structure  
> **Category:** Ordered binary tree  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Binary Search Tree (BST)?

A BST is a binary tree organized by an ordering rule: values in the left subtree are smaller than the node and values in the right subtree are larger, under the chosen duplicate policy.

### The one sentence to remember

**BST invariant. Problems: Validate BST, Kth Smallest in BST, Lowest Common Ancestor variants.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
             8
           /   \
          4     12
         / \   / \
        2   6 10  15

left < node < right

Inorder -> 2,4,6,8,10,12,15
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A sorted filing system where each decision splits the remaining values into 'smaller' and 'larger'.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it for ordered search, insertion/deletion, predecessor/successor, kth smallest, and validating whether a tree obeys BST ordering.

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

The ordering invariant allows a search to discard one entire subtree at every comparison—when the tree is reasonably balanced.

### Core invariant / rule

For every node, its subtree must respect the ancestor bounds, not merely the direct parent-child relationship. Inorder traversal of a valid BST produces sorted order.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- Search → O(h)
- Insert → O(h)
- Delete → O(h)
- Inorder traversal → O(n)
- Balanced h → O(log n)
- Worst-case skewed h → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Suppose root is 10. Its right subtree must contain values >10. If a deeper node contains 7 in that right subtree, checking only its parent may miss the violation; carrying the range catches it immediately.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
boolean isValidBST(TreeNode node, long low, long high) {
    if (node == null) return true;

    if (node.val <= low || node.val >= high) {
        return false;
    }

    return isValidBST(node.left, low, node.val)
        && isValidBST(node.right, node.val, high);
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

**Search/insert/delete:** O(h). Balanced → O(log n); skewed worst case → O(n). **Space:** O(h) for recursive operations.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Checking only direct children.
- Ignoring ancestor bounds.
- Integer overflow when using `Integer.MIN_VALUE/MAX_VALUE`; use `long` bounds when appropriate.
- Forgetting the duplicate policy.

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

- Ordered indexes.
- Symbol tables.
- Sorted sets/maps are commonly implemented with balanced search trees.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Validate a BST using bounds and explain why inorder traversal is sorted.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **BST vs HashMap:** BST maintains order; HashMap prioritizes expected constant-time lookup.
- **BST vs Heap:** BST supports ordered search; heap supports efficient min/max extraction.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Binary Search Tree (BST) solve?
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

**BST invariant. Problems: Validate BST, Kth Smallest in BST, Lowest Common Ancestor variants.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
