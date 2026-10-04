# Boyer-Moore Majority Vote

> **Classification:** Algorithm  
> **Purpose:** Finds a value occurring more than n/2 times using cancellation and O(1) extra space.

---

## 1. Learn this first — in one minute

### What is Boyer-Moore Majority Vote?

Finds a value occurring more than n/2 times using cancellation and O(1) extra space.

### Real-world analogy

In a vote where one candidate has an absolute majority, pair each vote for that candidate with a vote for someone else; the majority candidate still has votes left over.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
A A B A C A A
candidate=A

A(+1)
A(+2)
B -> cancel
A(+1)
C -> cancel
A(+1)
A(+2)

candidate A survives
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Guaranteed majority element > n/2; need O(1) extra space.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Every non-majority vote can cancel one majority vote. Since the majority has more votes than all others combined, it cannot be completely canceled.

---

## 5. Step-by-step method

Maintain candidate and count. If count=0, current becomes candidate. If current==candidate increment, else decrement. If majority is not guaranteed, verify candidate in a second pass.

---

## 6. Small example / dry run

`[2,2,1,1,1,2,2]`: candidate changes/loses counts, but 2 survives because it appears 4/7 times.

---

## 7. Java implementation

```java
int candidate = 0, count = 0;

for (int x : nums) {
    if (count == 0) candidate = x;
    count += (x == candidate) ? 1 : -1;
}
return candidate;
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
| Time | O(n) |
| Extra space | O(1) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting the majority guarantee or verification requirement.\n- Confusing majority (>n/2) with mode (most frequent).

---

## 10. Real interview / real-world examples

- Majority vote counting.\n- Finding dominant label in a stream when a strict majority is guaranteed.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Majority Element.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Boyer-Moore Majority Vote**?

Write your answer here:

> 

