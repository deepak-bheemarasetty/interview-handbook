# Insertion Sort

> **Classification:** Algorithm  
> **Purpose:** Builds a sorted prefix by taking the next element and inserting it into the correct place.

---

## 1. Learn this first — in one minute

### What is Insertion Sort?

Builds a sorted prefix by taking the next element and inserting it into the correct place.

### Real-world analogy

Sorting playing cards in your hand: draw one card and slide it left until it reaches the correct position.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
[2 5 7 | 3 6]
  sorted   next=3

shift 7 -> [2 5 _ 7 6]
shift 5 -> [2 _ 5 7 6]
insert 3 -> [2 3 5 7 6]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Small arrays, nearly sorted arrays, online insertion of items.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

At each iteration, the prefix is already sorted. Insert the next value without disturbing that invariant.

---

## 5. Step-by-step method

Store key. Shift larger prefix elements right. Put key in the empty position.

---

## 6. Small example / dry run

Cards `[2,5,7]`; new card 3 goes before 5 and 7. Only those larger cards shift.

---

## 7. Java implementation

```java
for (int i = 1; i < n; i++) {
    int key = a[i];
    int j = i - 1;

    while (j >= 0 && a[j] > key) {
        a[j + 1] = a[j];
        j--;
    }
    a[j + 1] = key;
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
| Time | O(n²) worst; O(n) best |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Overwriting key before saving it.\n- Wrong final insertion index.

---

## 10. Real interview / real-world examples

- Maintaining a sorted stream of a small number of items.\n- Sorting nearly sorted logs.

---

## 11. Problems from your roadmap that connect to this

Roadmap Sorting Algorithms.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Insertion Sort**?

Write your answer here:

> 

