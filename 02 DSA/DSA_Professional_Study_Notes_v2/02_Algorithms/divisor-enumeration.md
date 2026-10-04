# Divisor Enumeration

> **Classification:** Algorithm  
> **Purpose:** Finds all divisors of n by checking only up to sqrt(n), because divisors come in pairs.

---

## 1. Learn this first — in one minute

### What is Divisor Enumeration?

Finds all divisors of n by checking only up to sqrt(n), because divisors come in pairs.

### Real-world analogy

If 36 seats form a rectangle, every possible row count has a matching column count: 1×36, 2×18, 3×12, 4×9, 6×6.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
36:
1×36
2×18
3×12
4×9
6×6  <- sqrt pair
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

List factors/divisors, factorization, count divisors.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If `i` divides n, then `n/i` is another divisor. Once i passes sqrt(n), its paired divisor has already been found.

---

## 5. Step-by-step method

Loop i=1..sqrt(n); if n%i==0, add i and n/i; avoid adding the same value twice when i*i=n.

---

## 6. Small example / dry run

For 36, i=1 gives 1,36; i=2 gives 2,18; i=3 gives 3,12; i=4 gives 4,9; i=6 gives 6 only once.

---

## 7. Java implementation

```java
List<Integer> divisors = new ArrayList<>();

for (int i = 1; i <= n / i; i++) {
    if (n % i == 0) {
        divisors.add(i);
        if (i != n / i) divisors.add(n / i);
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
| Time | O(sqrt(n)) plus output |
| Extra space | O(number of divisors) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Duplicating sqrt(n).\n- Forgetting paired divisor.\n- Assuming generated divisors are sorted.

---

## 10. Real interview / real-world examples

- Finding factor pairs for packaging.\n- Counting ways to arrange equal groups.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Divisor Enumeration**?

Write your answer here:

> 

