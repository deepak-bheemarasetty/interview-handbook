# Meet in the Middle

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** An exponential-time strategy that splits a problem into two halves so 2^n work becomes roughly 2^(n/2) enumeration plus combination.

---

## 1. Learn this first — in one minute

### What is Meet in the Middle?

An exponential-time strategy that splits a problem into two halves so 2^n work becomes roughly 2^(n/2) enumeration plus combination.

### Real-world analogy

If a team of 40 people creates too many possible subsets, split the team into two groups of 20, list possibilities for each side, and combine matching totals.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
n items
   |
split
 /   \
n/2  n/2
 |     |
2^(n/2) possibilities each
 \     /
  combine with search/hash
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

n is too large for 2^n but small enough that 2^(n/2) is feasible; subset sum/closest sum.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The exponential exponent is halved. Instead of enumerating every full subset directly, enumerate subsets of each half and match their contributions.

---

## 5. Step-by-step method

1. Split input. 2. Generate all subset states for each half. 3. Sort/hash one side. 4. For each state on the other side, search for the best complement.

---

## 6. Small example / dry run

For target 10, left sums `{0,3,5}`, right sums `{0,2,4,7}`. For left 3, search right 7; total 10.

---

## 7. Java implementation

```java
// Conceptual subset-sum generation
List<Long> sums = new ArrayList<>();

void generate(int[] a, int i, long sum) {
    if (i == a.length) {
        sums.add(sum);
        return;
    }
    generate(a, i + 1, sum);
    generate(a, i + 1, sum + a[i]);
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
| Time | O(2^(n/2) × poly(n)) depending on combination method |
| Extra space | O(2^(n/2)) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using it when n is still too large.\n- Forgetting that the method remains exponential.\n- Generating duplicate states unnecessarily.

---

## 10. Real interview / real-world examples

- Choosing a subset of projects whose cost is closest to a budget.\n- Splitting a group of items to find a target sum.

---

## 11. Problems from your roadmap that connect to this

Pattern sheet Meet in the Middle.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Meet in the Middle**?

Write your answer here:

> 

