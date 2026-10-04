# HashMap and HashSet

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** Java data structures for expected O(1) key lookup, insertion, deletion, and membership under normal hashing behavior.

---

## 1. Learn this first — in one minute

### What is HashMap and HashSet?

Java data structures for expected O(1) key lookup, insertion, deletion, and membership under normal hashing behavior.

### Real-world analogy

A labeled cabinet: the label tells you which drawer to open instead of searching every drawer.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
HashMap:
"apple" -> 3
"banana" -> 5

HashSet:
apple ✓
orange ✗
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Frequency, membership, duplicate detection, key→value relationships.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A hash function maps a key to a bucket. Java handles collisions internally, allowing efficient expected lookup.

---

## 5. Step-by-step method

Use HashSet for membership/uniqueness. Use HashMap for associated values such as counts, indices, or lists.

---

## 6. Small example / dry run

Insert `apple` twice into a set: it still appears once. Put it into a map with value count → increment from 1 to 2.

---

## 7. Java implementation

```java
Map<String,Integer> map = new HashMap<>();
map.put("apple", map.getOrDefault("apple", 0) + 1);

Set<String> seen = new HashSet<>();
if (!seen.add("apple")) {
    // duplicate
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
| Time | Expected O(1) basic operations |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Assuming ordering; HashMap does not promise sorted order.\n- Mutating keys in ways that change hash/equality semantics.

---

## 10. Real interview / real-world examples

- Word frequency.\n- Inventory lookup.\n- Duplicate transaction IDs.

---

## 11. Problems from your roadmap that connect to this

Roadmap Hashing.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **HashMap and HashSet**?

Write your answer here:

> 

