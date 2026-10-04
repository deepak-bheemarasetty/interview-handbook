# Sweep Line

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pattern that converts interval overlap into ordered start/end events and scans them from left to right.

---

## 1. Learn this first — in one minute

### What is Sweep Line?

A pattern that converts interval overlap into ordered start/end events and scans them from left to right.

### Real-world analogy

Imagine walking along a timeline with a counter. Every time a meeting starts, the room occupancy increases; every time one ends, occupancy decreases.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Time:    1   2   3   4   5
events:  +       +   -   -
active:  1   1   2   1   0
             ↑ maximum overlap = 2
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Concurrent intervals, maximum overlap, room allocation, active objects over time.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Only changes in the active set matter. Between two event coordinates, the active count is constant, so we can ignore every point in between.

---

## 5. Step-by-step method

1. Convert each interval into events. 2. Sort events with a deliberate tie rule. 3. Maintain active count/state. 4. Update the answer at each event.

---

## 6. Small example / dry run

Meetings `[1,4]` and `[2,5]`: at 1 active=1; at 2 active=2; at 4 one ends; at 5 the second ends. Maximum rooms needed is 2.

---

## 7. Java implementation

```java
List<int[]> events = new ArrayList<>();
for (int[] in : intervals) {
    events.add(new int[]{in[0], +1});
    events.add(new int[]{in[1], -1});
}
events.sort((a,b) -> a[0] != b[0]
        ? Integer.compare(a[0], b[0])
        : Integer.compare(a[1], b[1]));

int active = 0, best = 0;
for (int[] e : events) {
    active += e[1];
    best = Math.max(best, active);
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
| Time | O(n log n) |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Incorrect tie ordering when a start and end occur at the same time.\n- Treating closed intervals as open or vice versa.\n- Using sweep line when only merged coverage is required.

---

## 10. Real interview / real-world examples

- Number of meeting rooms.\n- Maximum concurrent calls in a call center.\n- Peak server load.\n- Maximum number of customers inside a store.

---

## 11. Problems from your roadmap that connect to this

Pattern sheet: Sweep Line; roadmap Intervals stage.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Sweep Line**?

Write your answer here:

> 

