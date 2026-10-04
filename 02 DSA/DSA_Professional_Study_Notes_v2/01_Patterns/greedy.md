# Greedy

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** An optimization strategy that makes a locally best choice while relying on a proof that this choice can be part of an optimal global solution.

---

## 1. Learn this first — in one minute

### What is Greedy?

An optimization strategy that makes a locally best choice while relying on a proof that this choice can be part of an optimal global solution.

### Real-world analogy

Choosing the meeting that finishes earliest when you want to attend the maximum number of non-overlapping meetings. Finishing early leaves the most room for future meetings.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Meetings:
A [1---2]
B [2------5]
C [3--4]
D [5---6]

Pick earliest finish:
A -> C -> D
maximum number of compatible meetings
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Optimization where a choice seems locally best and there is a structural reason it cannot hurt the future.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Greedy is not “pick what looks good.” The proof is the important part. For activity selection, replacing the first meeting of any optimal schedule with the earliest-finishing meeting cannot reduce the number of remaining choices.

---

## 5. Step-by-step method

1. Identify candidate choices. 2. Find the ordering/selection rule. 3. Prove it with exchange/staying-ahead/cut reasoning. 4. Implement the one-pass selection.

---

## 6. Small example / dry run

Meetings `[1,2]`, `[2,5]`, `[3,4]`, `[5,6]`: choose `[1,2]`, then `[3,4]`, then `[5,6]` → 3 meetings.

---

## 7. Java implementation

```java
Arrays.sort(activities,
    Comparator.comparingInt(a -> a[1]));

int count = 0;
int lastFinish = Integer.MIN_VALUE;

for (int[] a : activities) {
    if (a[0] >= lastFinish) {
        count++;
        lastFinish = a[1];
    }
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
| Time | Often O(n log n) because of sorting |
| Extra space | O(1) auxiliary depending on sort/output |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Assuming greedy without proof.\n- Choosing earliest start instead of earliest finish for activity selection.\n- Confusing greedy with DP.

---

## 10. Real interview / real-world examples

- Scheduling maximum meetings.\n- Making change only for currency systems where greedy is proven valid.\n- Selecting minimum-cost connections in MST algorithms.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Jump Game; roadmap Greedy stage and MST algorithms.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Greedy**?

Write your answer here:

> 

