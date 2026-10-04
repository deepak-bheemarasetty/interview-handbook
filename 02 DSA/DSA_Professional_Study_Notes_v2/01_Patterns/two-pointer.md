# Two Pointer

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pattern using two indices to eliminate unnecessary comparisons, especially in sorted arrays, partitions, and sequence problems.

---

## 1. Learn this first — in one minute

### What is Two Pointer?

A pattern using two indices to eliminate unnecessary comparisons, especially in sorted arrays, partitions, and sequence problems.

### Real-world analogy

Two people searching a sorted shelf from opposite ends. If the current pair is too small, the left person moves right; if too large, the right person moves left.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Sorted: [1, 2, 3, 5, 8, 10]
          L           R

sum = 11, target = 13
too small -> move L

              L       R
             3 + 10 = 13 ✓
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Sorted array; pair/triplet; partition; remove duplicates; compare from both ends; linked-list slow/fast variants.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Sorting creates an ordering that tells you which whole group of candidates can be discarded after one comparison.

---

## 5. Step-by-step method

1. Sort if allowed/necessary. 2. Place pointers. 3. Evaluate the invariant. 4. Move the pointer that can make progress. 5. Skip duplicates where required.

---

## 6. Small example / dry run

For target 13 in `[1,2,3,5,8,10]`: 1+10=11, too small → move left. 2+10=12 → move left. 3+10=13 → found.

---

## 7. Java implementation

```java
int left = 0, right = nums.length - 1;

while (left < right) {
    int sum = nums[left] + nums[right];

    if (sum == target) break;
    if (sum < target) left++;
    else right--;
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
| Time | Usually O(n) after sorting; O(n log n) if sorting is required |
| Extra space | O(1) auxiliary for pointer scan, excluding sorting/output |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Moving the wrong pointer.\n- Forgetting to sort when the proof requires sorted order.\n- Mishandling duplicates in 3Sum/4Sum.\n- Using two pointers when the sequence has no property that justifies movement.

---

## 10. Real interview / real-world examples

- Two people meeting from opposite ends of a sorted queue.\n- Finding two products whose prices fit a budget.\n- Removing duplicate values from sorted data.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: 3Sum, Container With Most Water, Valid Palindrome, Remove Nth Node From End.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Two Pointer**?

Write your answer here:

> 

