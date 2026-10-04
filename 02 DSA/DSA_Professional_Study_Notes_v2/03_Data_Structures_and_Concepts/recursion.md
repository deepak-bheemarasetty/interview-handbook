# Recursion

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** A technique where a function solves a problem by calling itself on a smaller instance until a base case is reached.

---

## 1. Learn this first — in one minute

### What is Recursion?

A technique where a function solves a problem by calling itself on a smaller instance until a base case is reached.

### Real-world analogy

Opening nested boxes: open one box, find a smaller box, continue until there is no smaller box, then return outward.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
factorial(4)
  -> 4 * factorial(3)
       -> 3 * factorial(2)
            -> 2 * factorial(1)
                 -> 1
returns outward
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Tree structure, divide-and-conquer, backtracking, naturally self-similar problems.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Recursion works when a problem can be expressed using a smaller version of itself. The base case prevents infinite calls.

---

## 5. Step-by-step method

Define base case. Define progress toward it. Solve smaller instance. Combine with current result.

---

## 6. Small example / dry run

factorial(4)=4×factorial(3)=4×3×2×1=24.

---

## 7. Java implementation

```java
static int factorial(int n) {
    if (n <= 1) return 1; // base case
    return n * factorial(n - 1);
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
| Time | Depends on recurrence |
| Extra space | Recursion depth; often O(depth) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Missing base case.\n- Not reducing input size.\n- Excessive recursion depth in Java.

---

## 10. Real interview / real-world examples

- Folder traversal.\n- Tree algorithms.\n- Divide-and-conquer sorting.

---

## 11. Problems from your roadmap that connect to this

Roadmap Recursion & Backtracking.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Recursion**?

Write your answer here:

> 

