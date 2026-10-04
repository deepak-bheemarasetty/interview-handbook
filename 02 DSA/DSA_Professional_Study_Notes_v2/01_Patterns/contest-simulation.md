# Contest Simulation

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A practice pattern for solving mixed problems under a time limit, emphasizing triage, constraints, correctness, and post-contest review.

---

## 1. Learn this first — in one minute

### What is Contest Simulation?

A practice pattern for solving mixed problems under a time limit, emphasizing triage, constraints, correctness, and post-contest review.

### Real-world analogy

A fire drill: the goal is not merely to know individual tools but to decide quickly which problem to solve first and how to avoid repeated mistakes.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Read all
  ↓
classify difficulty
  ↓
easy/core first
  ↓
solve + test
  ↓
review stuck problem
  ↓
analyze mistakes
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Timed assessment, Infosys coding round, mixed problem set.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Assessment performance depends on decision-making as much as raw algorithm knowledge. Correctly identifying a known pattern early saves time.

---

## 5. Step-by-step method

Read all questions. Check constraints. Solve guaranteed/easy wins first. For a hard problem, time-box exploration. Test edge cases. Review after the timer.

---

## 6. Small example / dry run

In a 60-minute mock: spend first 5 minutes scanning; solve the easiest confidently; reserve a block for the harder problem; leave time to test.

---

## 7. Java implementation

```java
// No single algorithm.
// Your checklist before submit:
// 1. constraints
// 2. edge cases
// 3. complexity
// 4. sample + custom test
// 5. integer overflow
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
| Time | Assessment-dependent |
| Extra space | Assessment-dependent |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Spending 40 minutes stuck on one problem.\n- Coding before reading constraints.\n- Not testing empty/minimum/max inputs.

---

## 10. Real interview / real-world examples

- Infosys coding assessment.\n- Timed interview coding.

---

## 11. Problems from your roadmap that connect to this

Roadmap Assessment: Mixed Practice.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Contest Simulation**?

Write your answer here:

> 

