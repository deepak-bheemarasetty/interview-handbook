# Stack

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** A LIFO structure: the most recently inserted element is removed first.

---

## 1. Learn this first — in one minute

### What is Stack?

A LIFO structure: the most recently inserted element is removed first.

### Real-world analogy

A stack of plates: you take the top plate first.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
push 1
push 2
push 3

top -> [3]
       [2]
       [1]

pop -> 3
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Nested structure, undo, expression parsing, DFS, monotonic stack.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

LIFO exactly models nested decisions and “most recent unresolved item” problems.

---

## 5. Step-by-step method

Use push, pop, peek. In Java, prefer `ArrayDeque` for stack behavior.

---

## 6. Small example / dry run

Push A,B,C → pop returns C, then B.

---

## 7. Java implementation

```java
Deque<Integer> stack = new ArrayDeque<>();
stack.push(10);
stack.push(20);
int top = stack.peek();
int x = stack.pop();
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
| Time | O(1) push/pop/peek |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Calling pop on an empty stack.\n- Using Stack unnecessarily when ArrayDeque is preferable.

---

## 10. Real interview / real-world examples

- Undo history.\n- Browser back navigation conceptually.\n- Bracket matching.

---

## 11. Problems from your roadmap that connect to this

Roadmap Stack.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Stack**?

Write your answer here:

> 

