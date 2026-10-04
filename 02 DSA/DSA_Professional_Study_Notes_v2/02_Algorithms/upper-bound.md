# Upper Bound

> **Classification:** Algorithm  
> **Purpose:** Finds the first position whose value is strictly greater than a target.

---

## 1. Learn this first — in one minute

### What is Upper Bound?

Finds the first position whose value is strictly greater than a target.

### Real-world analogy

In a sorted score list, find where scores above 70 begin.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[10 20 20 30 40]
 target=20
          ^
 first >20 = index 3
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Last occurrence; count of values ≤ target; range frequency.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Treat `a[mid] > target` as true and find the first true position.

---

## 5. Step-by-step method

Use half-open `[0,n)`. If a[mid] > target, move right to mid; otherwise move left.

---

## 6. Small example / dry run

Upper bound of 20 in `[10,20,20,30]` is 3. Occurrences = 3-1=2.

---

## 7. Java implementation

```java
int l=0,r=a.length;
while(l<r){
    int m=l+(r-l)/2;
    if(a[m]>target) r=m;
    else l=m+1;
}
return l;
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

- Using `>=` instead of `>`.\n- Off-by-one at n.

---

## 10. Real interview / real-world examples

- Count all scores up to a threshold.\n- Find insertion point after duplicates.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: First and Last Position.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Upper Bound**?

Write your answer here:

> 

