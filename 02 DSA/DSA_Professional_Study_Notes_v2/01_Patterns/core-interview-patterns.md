# Core Interview Patterns

> **Classification:** Pattern recognition guide  
> **Purpose:** A recognition map for the highest-frequency patterns in your roadmap. It is not a single algorithm; it is a decision framework for identifying the right technique.

---

## 1. Learn this first — in one minute

### What is Core Interview Patterns?

A recognition map for the highest-frequency patterns in your roadmap. It is not a single algorithm; it is a decision framework for identifying the right technique.

### Real-world analogy

Think of a mechanic's diagnostic chart. The symptom is the problem statement; the pattern is the tool you choose before opening the engine.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Problem shape
   |
   +-- contiguous range -> Sliding Window / Prefix Sum
   +-- sorted pair/range -> Two Pointer / Binary Search
   +-- next greater -> Monotonic Stack
   +-- window max/min -> Monotonic Queue
   +-- top K -> Heap
   +-- overlap -> Merge Intervals / Sweep Line
   +-- choices -> Backtracking / DP
   +-- unweighted shortest -> BFS
   +-- weighted nonnegative -> Dijkstra
   +-- dependencies -> Topological Sort
   +-- connectivity merges -> DSU
   +-- repeated subproblems -> DP
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Use this file when you read a new problem and do not know where to start.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Expert DSA solving is largely pattern recognition plus proof. The goal is not memorizing 500 solutions; it is recognizing the reusable structure behind them.

---

## 5. Step-by-step method

1. Read constraints. 2. Identify data shape. 3. Identify what the question asks. 4. Match a pattern candidate. 5. State the invariant. 6. Reject patterns whose assumptions do not hold. 7. Implement and test.

---

## 6. Small example / dry run

“Longest substring without repeating characters” → contiguous substring + dynamic constraint → Sliding Window. “Kth largest” → rank/top-K → Heap or Quickselect. “Prerequisites” → dependency graph → Topological Sort.

---

## 7. Java implementation

```java
// There is no single implementation.
// The skill is selecting the correct implementation
// after identifying the problem structure.
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
| Time | Depends on selected technique |
| Extra space | Depends on selected technique |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Pattern matching from one keyword without checking constraints.\n- Using Dijkstra just because the problem says shortest path.\n- Using sliding window when the window property is not maintainable.

---

## 10. Real interview / real-world examples

- Infosys coding assessments.\n- Technical interviews.\n- Competitive programming.

---

## 11. Problems from your roadmap that connect to this

Workbook Patterns sheet + Roadmap Core Interview Patterns.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Core Interview Patterns**?

Write your answer here:

> 

