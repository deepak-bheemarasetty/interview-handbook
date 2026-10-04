# DAG Ordering

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** The pattern of recognizing a directed acyclic graph and converting dependencies into a valid execution order.

---

## 1. Learn this first — in one minute

### What is DAG Ordering?

The pattern of recognizing a directed acyclic graph and converting dependencies into a valid execution order.

### Real-world analogy

Cooking a recipe: chop vegetables before cooking them; boil water before adding pasta. Dependencies determine order.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Prep -> Cook -> Serve
  \               ^
   -> Plate -------
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Prerequisite, dependency, must happen before, build order.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Every edge `u→v` is a rule that u must appear before v. Topological sorting satisfies all such rules if no cycle exists.

---

## 5. Step-by-step method

Build directed graph. Detect cycle. Use Kahn or DFS topo. If cycle exists, no valid ordering.

---

## 6. Small example / dry run

A→B, A→C, B→D, C→D allows A first, then B/C in either order, then D.

---

## 7. Java implementation

```java
// Kahn's algorithm is the most direct implementation
// when dependency counts are easy to maintain.
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
| Time | O(V+E) |
| Extra space | O(V) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Treating arbitrary graphs as topologically sortable.\n- Ignoring cycles.

---

## 10. Real interview / real-world examples

- Course scheduling.\n- Build pipelines.

---

## 11. Problems from your roadmap that connect to this

Roadmap Topological Sort.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **DAG Ordering**?

Write your answer here:

> 

