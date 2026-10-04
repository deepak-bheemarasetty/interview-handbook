# Hashing

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A pattern of storing information in a hash table so membership, frequency, complement lookup, or grouping is expected O(1).

---

## 1. Learn this first — in one minute

### What is Hashing?

A pattern of storing information in a hash table so membership, frequency, complement lookup, or grouping is expected O(1).

### Real-world analogy

A library index: instead of scanning every book to find all copies of a title, you use a catalog keyed by title.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Input:       [2, 7, 11, 15]
target = 9

seen:
2 -> index 0
7 -> index 1

At 7: target - 7 = 2
                 ↑
             already seen
Answer: [0,1]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Frequency, duplicates, “have I seen this?”, complements, grouping, first/last occurrence.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Turn a repeated search into a direct lookup. The key should represent exactly the information needed to answer the current element.

---

## 5. Step-by-step method

1. Decide what key to store. 2. Decide whether the value should be a count, index, boolean, or list. 3. Scan once. 4. Query/update the map as you go.

---

## 6. Small example / dry run

Two Sum with `[2,7,11,15]`, target 9: store 2. At 7, look for 2; it exists, so return its index and the current index.

---

## 7. Java implementation

```java
Map<Integer, Integer> firstIndex = new HashMap<>();

for (int i = 0; i < nums.length; i++) {
    int need = target - nums[i];
    if (firstIndex.containsKey(need)) {
        return new int[]{firstIndex.get(need), i};
    }
    firstIndex.put(nums[i], i);
}
return new int[0];
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
| Time | Expected O(n) for one scan with hash lookups |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Storing the wrong information (value instead of index/count).\n- Assuming hashing is guaranteed O(1).\n- Forgetting duplicates matter.\n- Updating the map before checking when the problem forbids using the same element twice.

---

## 10. Real interview / real-world examples

- Phone contacts indexed by name.\n- Inventory count by product ID.\n- Counting votes by candidate.\n- Finding two transactions whose total equals a target.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Two Sum, Valid Anagram, Group Anagrams, Longest Consecutive Sequence, Subarray Sum Equals K.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Hashing**?

Write your answer here:

> 

