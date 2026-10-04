# Bit / XOR

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A bit-manipulation pattern that uses binary properties to solve parity, uniqueness, masks, and power-of-two problems efficiently.

---

## 1. Learn this first — in one minute

### What is Bit / XOR?

A bit-manipulation pattern that uses binary properties to solve parity, uniqueness, masks, and power-of-two problems efficiently.

### Real-world analogy

Imagine each bit is an on/off switch. XOR is a switch that toggles: applying the same toggle twice returns it to the original state.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
5 = 101
3 = 011

5 XOR 3:
  101
^ 011
-----
  110 = 6

x ^ x = 0
x ^ 0 = x
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Every value appears twice except one; parity; subset masks; powers of two; set/unset/test a bit.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

XOR is associative and commutative, and identical values cancel. Therefore paired values disappear while the unpaired value remains.

---

## 5. Step-by-step method

For a unique element, XOR all values. For masks, use `&`, `|`, `^`, shifts to test/set/clear bits. For power of two, exploit `x & (x-1)` removing the lowest set bit.

---

## 6. Small example / dry run

`[4,1,2,1,2]`: XOR sequence `0^4^1^2^1^2 = 4`, because each pair cancels.

---

## 7. Java implementation

```java
int unique = 0;
for (int x : nums) {
    unique ^= x;
}

// power of two:
boolean isPowerOfTwo =
    x > 0 && (x & (x - 1)) == 0;
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
| Time | Usually O(n) or O(1) per bit operation |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Confusing `^` with exponentiation (Java has no exponent operator).\n- Ignoring signed integer behavior.\n- Using bit tricks without checking constraints/types.

---

## 10. Real interview / real-world examples

- Toggle feature flags.\n- Represent subsets with bit masks.\n- Find a unique ID when all other IDs occur twice.

---

## 11. Problems from your roadmap that connect to this

Roadmap Bits; Pattern sheet Bit/XOR.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Bit / XOR**?

Write your answer here:

> 

