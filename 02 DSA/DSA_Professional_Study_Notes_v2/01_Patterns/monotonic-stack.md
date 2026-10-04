# Monotonic Stack

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A stack maintained in increasing or decreasing order so each element is pushed and popped at most once, resolving next/previous greater or smaller relationships.

---

## 1. Learn this first — in one minute

### What is Monotonic Stack?

A stack maintained in increasing or decreasing order so each element is pushed and popped at most once, resolving next/previous greater or smaller relationships.

### Real-world analogy

People standing in a queue where a taller person makes shorter people behind them irrelevant for the next-taller question. When a taller person arrives, shorter candidates are resolved and removed.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Current values:  2  1  4

stack indices:
2
2,1

see 4:
pop 1 -> next greater = 4
pop 2 -> next greater = 4
push 4
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Next greater/smaller; previous greater/smaller; spans; histogram; temperature waits; nearest boundary.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If a new value dominates the stack top, that top can never be the answer for future positions requiring a stronger candidate. Resolve it now and remove it.

---

## 5. Step-by-step method

1. Decide increasing/decreasing invariant. 2. Scan. 3. While current element violates the invariant, pop and assign its answer. 4. Push current index. 5. Clean remaining stack if needed.

---

## 6. Small example / dry run

Daily temperatures `[73,74,75,71]`: when 74 arrives, 73's next warmer day is today. When 75 arrives, both 74 and then 73 can be resolved.

---

## 7. Java implementation

```java
Deque<Integer> st = new ArrayDeque<>();
int[] next = new int[nums.length];

for (int i = 0; i < nums.length; i++) {
    while (!st.isEmpty() && nums[st.peek()] < nums[i]) {
        int j = st.pop();
        next[j] = nums[i];
    }
    st.push(i);
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
| Time | O(n) amortized |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Choosing the wrong monotonic direction.\n- Storing values when indices are needed for distance/span.\n- Mishandling equal values.\n- Forgetting final stack cleanup.

---

## 10. Real interview / real-world examples

- Next warmer day.\n- Nearest greater price.\n- Largest rectangle in a histogram.\n- Nearest road/building boundary.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Next Greater Element, Daily Temperatures, Largest Rectangle in Histogram.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Monotonic Stack**?

Write your answer here:

> 

