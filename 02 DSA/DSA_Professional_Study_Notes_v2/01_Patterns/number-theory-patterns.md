# Number Theory Patterns

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A collection of mathematical problem-solving patterns built around divisibility, factors, primes, GCD/LCM, modular arithmetic, and periodicity.

---

## 1. Learn this first — in one minute

### What is Number Theory Patterns?

A collection of mathematical problem-solving patterns built around divisibility, factors, primes, GCD/LCM, modular arithmetic, and periodicity.

### Real-world analogy

Like solving a timetable problem by noticing cycles instead of simulating every minute.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
GCD/LCM -> divisibility
Prime -> factors
Sieve -> many primes
Modulo -> repeating remainder
Cycle/period -> reduce huge values
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Words like divisible, prime, factor, remainder, common multiple, modulo, huge exponent.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Many apparently large mathematical searches collapse when you use number properties instead of brute force.

---

## 5. Step-by-step method

Check divisibility structure first; reduce with gcd; use sieve for many prime queries; use modular arithmetic for huge values; look for periodicity.

---

## 6. Small example / dry run

If two events repeat every 6 and 8 units, you do not simulate forever: their alignment repeats every LCM(6,8)=24.

---

## 7. Java implementation

```java
long g = gcd(a,b);
long l = lcm(a,b);
long remainder = x % mod;
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
| Time | Depends on the mathematical operation |
| Extra space | Usually O(1), or O(n) for preprocessing such as sieve |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Brute-forcing huge ranges.\n- Overflow in multiplication.\n- Forgetting modulo normalization.

---

## 10. Real interview / real-world examples

- Scheduling cycles.\n- Prime preprocessing.\n- Modular combinatorics.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Number Theory Patterns**?

Write your answer here:

> 

