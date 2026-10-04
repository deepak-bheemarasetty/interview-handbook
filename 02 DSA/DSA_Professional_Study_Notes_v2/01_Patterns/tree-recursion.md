# Tree Recursion

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A tree-specific recursive pattern where a node asks its left and right subtrees for information and combines their answers.

---

## 1. Learn this first — in one minute

### What is Tree Recursion?

A tree-specific recursive pattern where a node asks its left and right subtrees for information and combines their answers.

### Real-world analogy

A manager asks each team lead for their team's result, then combines those results to report the department result.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
        node
       /    \
   answerL answerR
       \    /
       combine
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Height, diameter, subtree sum, path values, tree DP.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A tree is recursively made of a node plus two smaller trees. Therefore a subtree function can return exactly the information its parent needs.

---

## 5. Step-by-step method

Define return value. Base case null. Recursively solve left/right. Combine. Decide whether the global answer needs a separate variable.

---

## 6. Small example / dry run

Height = 1 + max(leftHeight,rightHeight). A leaf has height 1 (under that convention).

---

## 7. Java implementation

```java
int height(TreeNode node) {
    if (node == null) return 0;
    return 1 + Math.max(
        height(node.left),
        height(node.right)
    );
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
| Extra space | O(h) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Mixing height conventions.\n- Doing repeated subtree traversals causing O(n²).

---

## 10. Real interview / real-world examples

- Folder hierarchy depth.\n- Organization tree metrics.

---

## 11. Problems from your roadmap that connect to this

Roadmap Binary Trees; Problem Bank Maximum Depth, Diameter.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Tree Recursion**?

Write your answer here:

> 

