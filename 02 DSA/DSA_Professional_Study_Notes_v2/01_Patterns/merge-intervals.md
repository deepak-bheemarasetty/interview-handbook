# Merge Intervals

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** An interval pattern that sorts ranges by start and merges overlapping ranges into maximal non-overlapping ranges.

---

## 1. Learn this first — in one minute

### What is Merge Intervals?

An interval pattern that sorts ranges by start and merges overlapping ranges into maximal non-overlapping ranges.

### Real-world analogy

Combining overlapping booking reservations. If one reservation ends after the next one starts, they belong to the same occupied block.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[1-----4]
    [3--------6]
                 [8---10]

merge first two:
[1----------6]    [8---10]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Ranges, schedules, meetings, occupied/free time, overlapping segments.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

After sorting by start, no later interval can start before the current interval. Therefore only the current merged end determines whether the next interval overlaps.

---

## 5. Step-by-step method

1. Sort by start. 2. Keep current `[start,end]`. 3. If next.start <= end, extend end. 4. Otherwise output current and start a new interval.

---

## 6. Small example / dry run

`[1,4]` and `[3,6]` overlap because 3≤4 → `[1,6]`. `[8,10]` does not overlap → finalize `[1,6]`.

---

## 7. Java implementation

```java
Arrays.sort(intervals, Comparator.comparingInt(a -> a[0]));

List<int[]> merged = new ArrayList<>();
int start = intervals[0][0], end = intervals[0][1];

for (int i = 1; i < intervals.length; i++) {
    if (intervals[i][0] <= end) {
        end = Math.max(end, intervals[i][1]);
    } else {
        merged.add(new int[]{start, end});
        start = intervals[i][0];
        end = intervals[i][1];
    }
}
merged.add(new int[]{start, end});
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
| Time | O(n log n) due to sorting |
| Extra space | O(n) for output; O(1) auxiliary depending on implementation |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Not sorting first.\n- Using `<` instead of `<=` when touching intervals should merge.\n- Forgetting the last interval.\n- Confusing merge intervals with counting concurrent meetings.

---

## 10. Real interview / real-world examples

- Calendar bookings.\n- Network maintenance windows.\n- Merging occupied land segments.\n- Consolidating delivery time ranges.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Merge Intervals; roadmap Intervals stage.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Merge Intervals**?

Write your answer here:

> 

