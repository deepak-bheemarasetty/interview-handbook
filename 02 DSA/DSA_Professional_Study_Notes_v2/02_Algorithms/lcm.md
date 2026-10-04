# LCM

> **Classification:** Algorithm  
> **Purpose:** Computes the least common multiple of two integers.

---

## 1. Learn this first — in one minute

### What is LCM?

Computes the least common multiple of two integers.

### Real-world analogy

Two buses leave every 6 and 8 minutes. The LCM tells you the first time their schedules align again.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Multiples of 6:  6 12 18 24 30 36 42 48
Multiples of 8:  8 16 24 32 40 48
                         ↑
                       LCM=24
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Schedule alignment, common multiples, fraction operations.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

`gcd(a,b) × lcm(a,b) = |a×b|`. Divide before multiplying to reduce overflow.

---

## 5. Step-by-step method

1. Compute gcd. 2. Compute `(a/gcd)*b`. 3. Take absolute value.

---

## 6. Small example / dry run

6 and 8 have gcd 2. LCM = (6/2)*8 = 24.

---

## 7. Java implementation

```java
static long lcm(long a, long b) {
    if (a == 0 || b == 0) return 0;
    return Math.abs((a / gcd(a, b)) * b);
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
| Time | O(log min(a,b)) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Multiplying first and overflowing.\n- Incorrect zero handling.

---

## 10. Real interview / real-world examples

- Multiple machine maintenance cycles.\n- Repeating alarms.\n- Synchronizing periodic tasks.

---

## 11. Problems from your roadmap that connect to this

Roadmap Basic Math.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **LCM**?

Write your answer here:

> 

