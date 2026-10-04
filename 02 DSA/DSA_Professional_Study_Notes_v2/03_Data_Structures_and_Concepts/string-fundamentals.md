# String Fundamentals

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** Techniques for character traversal, frequency counting, palindrome checks, anagrams, parsing, and building output efficiently.

---

## 1. Learn this first — in one minute

### What is String Fundamentals?

Techniques for character traversal, frequency counting, palindrome checks, anagrams, parsing, and building output efficiently.

### Real-world analogy

A string is like a row of letter tiles. Some problems care about each tile; others care about contiguous sections or counts.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
"level"
 ^   ^
 compare ends

"listen" -> frequency map -> "silent"
same counts => anagram
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Character frequency, palindrome, substring, anagram, parsing.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Strings are often arrays of characters with additional constraints. Decide whether the problem is about exact order, counts, contiguous ranges, or subsequences.

---

## 5. Step-by-step method

Choose char array, frequency array/map, two pointers, or StringBuilder based on the operation.

---

## 6. Small example / dry run

`level`: compare l/l, e/e, center v → palindrome.

---

## 7. Java implementation

```java
int[] freq = new int[26];
for (char c : s.toCharArray()) {
    freq[c - 'a']++;
}

StringBuilder sb = new StringBuilder();
for (char c : s.toCharArray())
    sb.append(c);
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
| Time | Usually O(n) for one scan |
| Extra space | O(alphabet) for fixed alphabet or O(n) for general maps |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using `==` for String content comparison in Java.\n- Assuming lowercase ASCII when input may contain Unicode.\n- Repeated string concatenation in loops causing avoidable O(n²) behavior.

---

## 10. Real interview / real-world examples

- Log parsing.\n- Usernames/anagrams.\n- Text validation.

---

## 11. Problems from your roadmap that connect to this

Roadmap String Patterns; Problem Bank string problems.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **String Fundamentals**?

Write your answer here:

> 

