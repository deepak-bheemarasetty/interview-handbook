# Classic Binary Search

> **Classification:** Algorithm  
> **Purpose:** Searches a sorted array by halving the candidate interval each step.

---

## 1. Learn this first — in one minute

### What is Classic Binary Search?

Searches a sorted array by halving the candidate interval each step.

### Real-world analogy

Dictionary search.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[1 3 5 7 9 11 13]
        M=7
target 11 -> right half
[9 11 13]
   M=11 ✓
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Sorted array and exact target.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Ordering tells you which half is impossible after one comparison.

---

## 5. Step-by-step method

Maintain `[l,r]`; inspect mid; discard the impossible half; terminate when interval is empty.

---

## 6. Small example / dry run

Search 11: compare 7, then 11.

---

## 7. Java implementation

```java
int l=0, r=a.length-1;
while(l<=r){
    int m=l+(r-l)/2;
    if(a[m]==target) return m;
    if(a[m]<target) l=m+1;
    else r=m-1;
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
| Time | O(log n) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Infinite loops; inconsistent boundaries; unsorted input.

---

## 10. Real interview / real-world examples

- Searching a sorted product catalog.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Binary Search.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Classic Binary Search**?

Write your answer here:

> 

