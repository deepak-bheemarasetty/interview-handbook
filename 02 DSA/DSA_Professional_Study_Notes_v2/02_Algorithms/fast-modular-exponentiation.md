# Fast Modular Exponentiation

> **Classification:** Algorithm  
> **Purpose:** Computes `a^b mod m` in O(log b) using repeated squaring instead of multiplying b times.

---

## 1. Learn this first — in one minute

### What is Fast Modular Exponentiation?

Computes `a^b mod m` in O(log b) using repeated squaring instead of multiplying b times.

### Real-world analogy

To reach a huge distance, use jumps of lengths 1,2,4,8,... rather than taking every single step.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Exponent 13 = 8 + 4 + 1

a^13 = a^8 × a^4 × a^1
       ↑      ↑      ↑
      square repeatedly
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Huge exponent under modulo; power calculations in number theory.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Repeated squaring generates `a, a², a⁴, a⁸,...`. The binary representation of b tells us which powers to multiply.

---

## 5. Step-by-step method

Initialize result=1. While exponent>0: if odd, multiply result by base; square base; divide exponent by 2.

---

## 6. Small example / dry run

13 binary is 1101, so use powers 8,4,1. Only three selected powers are multiplied.

---

## 7. Java implementation

```java
static long modPow(long a, long e, long mod) {
    long result = 1 % mod;
    a %= mod;

    while (e > 0) {
        if ((e & 1) == 1)
            result = (result * a) % mod;
        a = (a * a) % mod;
        e >>= 1;
    }
    return result;
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
| Time | O(log exponent) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting modulo after multiplication.\n- Overflow before `%` when values are too large for long.\n- Negative exponent requires a different mathematical treatment.

---

## 10. Real interview / real-world examples

- Cryptography concepts.\n- Huge combinatorial calculations modulo a number.

---

## 11. Problems from your roadmap that connect to this

Roadmap Basic Math: modular arithmetic.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Fast Modular Exponentiation**?

Write your answer here:

> 

