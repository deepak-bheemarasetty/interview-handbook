# Search in Rotated Sorted Array

> **Classification:** Algorithm  
> **Purpose:** Binary search on a sorted array that has been rotated, using the fact that at least one half is normally sorted.

---

## 1. Learn this first — in one minute

### What is Search in Rotated Sorted Array?

Binary search on a sorted array that has been rotated, using the fact that at least one half is normally sorted.

### Real-world analogy

A circularly shifted phonebook: even though the whole sequence wraps around, one side of the midpoint is still in normal sorted order.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[4 5 6 7 0 1 2]
 L     M       R
left half [4,5,6,7] is sorted
target 0 lies in right half
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Sorted array rotated once; exact search.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

At any midpoint, either left half or right half is sorted. Check whether target lies inside that sorted range; otherwise search the other half.

---

## 5. Step-by-step method

1. Compute mid. 2. If found, return. 3. Detect sorted half. 4. Check target range. 5. Discard the impossible half.

---

## 6. Small example / dry run

For `[4,5,6,7,0,1,2]`, mid=7; left half is sorted. Target 0 is not between 4 and 7, so search right.

---

## 7. Java implementation

```java
int l=0,r=a.length-1;
while(l<=r){
    int m=l+(r-l)/2;
    if(a[m]==target) return m;

    if(a[l] <= a[m]) { // left sorted
        if(a[l] <= target && target < a[m]) r=m-1;
        else l=m+1;
    } else { // right sorted
        if(a[m] < target && target <= a[r]) l=m+1;
        else r=m-1;
    }
}
return -1;
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
| Time | O(log n) without problematic duplicates |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Incorrect inclusive comparisons.\n- Ignoring duplicate-value complications.

---

## 10. Real interview / real-world examples

- Searching a rotated database index.\n- Circularly shifted sorted records.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Search in Rotated Sorted Array.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Search in Rotated Sorted Array**?

Write your answer here:

> 

