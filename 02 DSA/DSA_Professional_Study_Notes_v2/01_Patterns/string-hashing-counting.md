# String Hashing / Counting

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A string-specific pattern of converting characters or normalized character counts into fast-comparison keys.

---

## 1. Learn this first — in one minute

### What is String Hashing / Counting?

A string-specific pattern of converting characters or normalized character counts into fast-comparison keys.

### Real-world analogy

Instead of comparing every letter of two word bags repeatedly, count how many of each letter each bag contains.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
anagram:
listen -> a:0 b:0 ... e:1 i:1 l:1 n:1 s:1 t:1
silent -> same signature
=> same counts
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Anagrams, character frequencies, grouping strings, repeated equality checks.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

If order does not matter, a frequency signature is enough. If order matters, use a rolling/hash representation only when the problem permits probabilistic/hash reasoning.

---

## 5. Step-by-step method

Normalize input if needed. Count characters. Use a canonical key such as frequency vector or sorted string.

---

## 6. Small example / dry run

`eat`, `tea`, `ate` all have the same 26-count vector, so they can be grouped.

---

## 7. Java implementation

```java
int[] count = new int[26];
for(char c : s.toCharArray()) count[c-'a']++;

String key = Arrays.toString(count);
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
| Time | O(n) per string with fixed alphabet |
| Extra space | O(alphabet) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using a key that loses necessary information.\n- Assuming lowercase English only.

---

## 10. Real interview / real-world examples

- Group anagrams.\n- Detect duplicate normalized words.

---

## 11. Problems from your roadmap that connect to this

Roadmap String Patterns; Problem Bank Valid Anagram, Group Anagrams.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **String Hashing / Counting**?

Write your answer here:

> 

