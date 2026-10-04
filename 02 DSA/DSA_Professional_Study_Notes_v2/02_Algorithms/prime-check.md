# Prime Check

> **Classification:** Algorithm  
> **Purpose:** Determines whether an integer greater than 1 has exactly two positive divisors.

---

## 1. Learn this first — in one minute

### What is Prime Check?

Determines whether an integer greater than 1 has exactly two positive divisors.

### Real-world analogy

Checking whether a group of objects can be split evenly into more than one nontrivial rectangular arrangement. A composite number has a factor pair; a prime has none.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
n = 29
try divisors only up to sqrt(29) ≈ 5.38:
2 ✗
3 ✗
4 ✗
5 ✗
=> prime
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Prime validation for individual numbers; factorization preprocessing.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If n = a×b and both a,b were greater than sqrt(n), their product would exceed n. So every composite number has a factor at or below sqrt(n).

---

## 5. Step-by-step method

1. Reject n<2. 2. Test 2. 3. Test odd i up to sqrt(n). 4. If none divide, prime.

---

## 6. Small example / dry run

For 29, test 2,3,5; none divide, so 29 is prime.

---

## 7. Java implementation

```java
static boolean isPrime(int n) {
    if (n < 2) return false;
    if (n % 2 == 0) return n == 2;

    for (int i = 3; i <= n / i; i += 2) {
        if (n % i == 0) return false;
    }
    return true;
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
| Time | O(sqrt(n)) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Treating 1 as prime.\n- Testing all numbers to n unnecessarily.\n- Overflow in i*i.

---

## 10. Real interview / real-world examples

- Cryptographic concepts.\n- Checking whether an ID is prime in math problems.\n- Generating primes before other computations.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Prime Check**?

Write your answer here:

> 

