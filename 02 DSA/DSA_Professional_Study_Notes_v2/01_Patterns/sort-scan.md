# Sort + Scan

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A common pattern: sort once to create useful order, then make a linear scan with a simple invariant.

---

## 1. Learn this first — in one minute

### What is Sort + Scan?

A common pattern: sort once to create useful order, then make a linear scan with a simple invariant.

### Real-world analogy

Arrange people by height first; after that, detecting groups or gaps becomes a single walk instead of comparing everyone with everyone.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
unsorted -> sort -> scan

[5,1,4,2] -> [1,2,4,5]
                    ^
                 one pass
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Duplicates, intervals, grouping, greedy choices, pair relationships where order helps.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Sorting costs O(n log n), but it can remove ambiguity and make a later O(n) scan possible.

---

## 5. Step-by-step method

Identify what sorting order exposes. Sort. State the scan invariant. Traverse once and update answer.

---

## 6. Small example / dry run

To merge intervals, sort by start; after that only the current merged end matters.

---

## 7. Java implementation

```java
Arrays.sort(a);
for (int i=1; i<a.length; i++) {
    // exploit sorted relationship
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
| Time | Usually O(n log n) |
| Extra space | Depends on sorting/extra output |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Sorting when original indices matter and aren't preserved.\n- Assuming sorting alone solves the problem.

---

## 10. Real interview / real-world examples

- Grouping anagrams.\n- Interval merging.\n- Removing duplicates.

---

## 11. Problems from your roadmap that connect to this

Roadmap Sorting: Sort + scan.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Sort + Scan**?

Write your answer here:

> 

