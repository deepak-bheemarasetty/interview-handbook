# Sliding Window

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A contiguous-range pattern that maintains a current window and expands/shrinks it instead of recomputing every subarray or substring.

---

## 1. Learn this first — in one minute

### What is Sliding Window?

A contiguous-range pattern that maintains a current window and expands/shrinks it instead of recomputing every subarray or substring.

### Real-world analogy

A camera frame moving across a street: you add what enters from the right and remove what leaves from the left. You never rebuild the whole frame.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
String:  a b c a d
          [-----]
          L     R

add right -> invalid (duplicate a)
move L ->  [---]
             L R
valid again
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Contiguous subarray/substring; longest/shortest window; at most/exactly K; frequency constraints.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Adjacent windows overlap heavily. Reuse the state from the previous window instead of starting from scratch.

---

## 5. Step-by-step method

1. Expand right. 2. Add its contribution to the state. 3. While the window violates the rule, remove `left` and advance left. 4. Update the answer whenever the window is valid.

---

## 6. Small example / dry run

Longest substring without repeating characters for `abcad`: add a,b,c → length 3. Add a → duplicate, remove from left until a is unique → window `bcad`, length 4.

---

## 7. Java implementation

```java
int left = 0, best = 0;
Map<Character, Integer> count = new HashMap<>();

for (int right = 0; right < s.length(); right++) {
    char c = s.charAt(right);
    count.put(c, count.getOrDefault(c, 0) + 1);

    while (count.get(c) > 1) {
        char d = s.charAt(left++);
        count.put(d, count.get(d) - 1);
    }

    best = Math.max(best, right - left + 1);
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
| Time | Usually O(n) because each element enters and leaves the window at most once |
| Extra space | O(alphabet size) or O(n), depending on maintained state |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Shrinking too much or too little.\n- Forgetting to remove the left element from counts/state.\n- Using sliding window when the validity property is not monotonic under shrinking.

---

## 10. Real interview / real-world examples

- A moving average of the last K days.\n- Longest period without exceeding a budget.\n- Longest substring with unique characters.\n- Minimum window containing required characters.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Longest Substring Without Repeating Characters, Minimum Window Substring, Sliding Window Maximum.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Sliding Window**?

Write your answer here:

> 

