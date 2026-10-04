# Monotonic Queue

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A deque pattern that keeps only candidates that can still become the minimum/maximum of a moving window.

---

## 1. Learn this first — in one minute

### What is Monotonic Queue?

A deque pattern that keeps only candidates that can still become the minimum/maximum of a moving window.

### Real-world analogy

A sports leaderboard for a moving time window: once a newer player is at least as strong as an older player, the older player will never become the maximum while both remain eligible.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Window size = 3
values:  1  3  -1  -3  5

deque values for max:
1
3          -> 1 removed
3,-1
3,-1,-3
5          -> all smaller dominated
front = window maximum
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Sliding window maximum/minimum; dynamic range optimum.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The deque removes two useless categories: expired indices from the front and dominated candidates from the back.

---

## 5. Step-by-step method

1. Remove expired front indices. 2. Remove back indices whose values are worse than the new candidate. 3. Add the new index. 4. Once the window is full, the front is the answer.

---

## 6. Small example / dry run

For window `[1,3,-1]`, 1 is removed when 3 arrives because 3 is newer and larger. The deque front is therefore 3, the maximum.

---

## 7. Java implementation

```java
Deque<Integer> dq = new ArrayDeque<>();
int[] ans = new int[nums.length - k + 1];

for (int r = 0; r < nums.length; r++) {
    while (!dq.isEmpty() && dq.peekFirst() <= r - k)
        dq.pollFirst();

    while (!dq.isEmpty() && nums[dq.peekLast()] <= nums[r])
        dq.pollLast();

    dq.offerLast(r);

    if (r >= k - 1)
        ans[r - k + 1] = nums[dq.peekFirst()];
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
| Time | O(n) |
| Extra space | O(k) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Storing values instead of indices.\n- Forgetting expired indices.\n- Removing from the wrong end.\n- Using a heap without considering the extra log k cost.

---

## 10. Real interview / real-world examples

- Maximum temperature in every 7-day period.\n- Maximum stock price over the last K minutes.\n- Best sensor reading in a moving time interval.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Sliding Window Maximum.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Monotonic Queue**?

Write your answer here:

> 

