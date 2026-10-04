# Sieve of Eratosthenes

> **Classification:** Algorithm  
> **Purpose:** Finds all primes up to N by repeatedly marking multiples of each discovered prime as composite.

---

## 1. Learn this first — in one minute

### What is Sieve of Eratosthenes?

Finds all primes up to N by repeatedly marking multiples of each discovered prime as composite.

### Real-world analogy

At a school assembly, once you know a student is a multiple of a prime number, you can cross out all their matching multiples in one batch instead of testing each number independently.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
2 3 4 5 6 7 8 9 10 11 12
^     x   x   x  ^   x   x
prime 2 marks 4,6,8,10,12
prime 3 marks 6,9,12
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Many prime queries up to a limit; need primes for preprocessing.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Every composite number has a smallest prime factor ≤ sqrt(n). Therefore marking multiples from p² is enough.

---

## 5. Step-by-step method

1. Assume 2..N are prime. 2. For p≤sqrt(N), if prime[p], mark p²,p²+p,... composite. 3. Remaining true values are primes.

---

## 6. Small example / dry run

For N=12: 2 marks 4,6,8,10,12; 3 marks 9,12. Remaining 2,3,5,7,11 are prime.

---

## 7. Java implementation

```java
static boolean[] sieve(int n) {
    boolean[] prime = new boolean[n + 1];
    if (n >= 2) Arrays.fill(prime, true);
    if (n >= 0) prime[0] = false;
    if (n >= 1) prime[1] = false;

    for (int p = 2; p <= n / p; p++) {
        if (!prime[p]) continue;
        for (int x = p * p; x <= n; x += p)
            prime[x] = false;
    }
    return prime;
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
| Time | O(n log log n) |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Starting from 2p instead of p² is correct but does redundant work.\n- Forgetting 0 and 1 are not prime.\n- Out-of-bounds at p².

---

## 10. Real interview / real-world examples

- Precomputing prime numbers for many test cases.\n- Generating prime factors in competitive programming.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Sieve of Eratosthenes**?

Write your answer here:

> 

