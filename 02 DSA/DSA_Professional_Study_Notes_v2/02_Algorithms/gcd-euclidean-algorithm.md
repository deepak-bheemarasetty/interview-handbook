# GCD (Euclidean Algorithm)

> **Classification:** Algorithm  
> **Purpose:** Computes the greatest common divisor of two integers using repeated remainders.

---

## 1. Learn this first — in one minute

### What is GCD (Euclidean Algorithm)?

Computes the greatest common divisor of two integers using repeated remainders.

### Real-world analogy

To find the largest tile size that can exactly cover two rectangular lengths, repeatedly replace the larger length with the remainder after cutting equal pieces.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
48, 18
48 = 2×18 + 12
18 = 1×12 + 6
12 = 2×6  + 0
             ↑
           GCD = 6
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

GCD, common divisor, simplifying fractions, repeating cycles, divisibility.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Any common divisor of `a` and `b` also divides `a % b`. Therefore `gcd(a,b)=gcd(b,a%b)`. Each remainder becomes smaller, so the process terminates.

---

## 5. Step-by-step method

1. Take `(a,b)`. 2. While b≠0, replace `(a,b)` by `(b,a%b)`. 3. When b=0, a is the GCD.

---

## 6. Small example / dry run

For 48 and 18: 48%18=12; 18%12=6; 12%6=0. Answer 6.

---

## 7. Java implementation

```java
static long gcd(long a, long b) {
    a = Math.abs(a);
    b = Math.abs(b);
    while (b != 0) {
        long t = a % b;
        a = b;
        b = t;
    }
    return a;
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

- Forgetting absolute values for negatives.\n- Treating LCM as simply a*b and overflowing.\n- Not handling zero correctly.

---

## 10. Real interview / real-world examples

- Simplifying fractions.\n- Finding repeating schedule alignment.\n- Largest square tile fitting exact dimensions.

---

## 11. Problems from your roadmap that connect to this

Roadmap Basic Math: GCD/LCM.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **GCD (Euclidean Algorithm)**?

Write your answer here:

> 

