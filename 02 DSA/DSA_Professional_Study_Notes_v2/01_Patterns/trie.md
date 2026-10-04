# Trie

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A tree-shaped data structure that stores strings character-by-character so common prefixes are shared.

---

## 1. Learn this first — in one minute

### What is Trie?

A tree-shaped data structure that stores strings character-by-character so common prefixes are shared.

### Real-world analogy

A physical dictionary organized by folders: first choose the first letter, then second letter, and so on. Words with the same beginning share the same path.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
root
 ├─ c
 │  └─ a
 │     ├─ t *
 │     └─ r *
 └─ d
    └─ o
       └─ g *

* = complete word
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Prefix search, autocomplete, dictionary membership, words beginning with a prefix, many string queries.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Hashing a whole word helps exact lookup, but a trie makes every prefix an explicit node. That makes prefix queries natural.

---

## 5. Step-by-step method

1. Start at root. 2. For each character, follow/create a child. 3. Mark terminal nodes for complete words. 4. Search walks the same path and checks terminal/prefix conditions.

---

## 6. Small example / dry run

Insert `cat` and `car`: both share `c→a`; only the third character differs. Searching prefix `ca` succeeds without caring whether `ca` itself is a complete word.

---

## 7. Java implementation

```java
class TrieNode {
    TrieNode[] child = new TrieNode[26];
    boolean end;
}

void insert(String word) {
    TrieNode cur = root;
    for (char ch : word.toCharArray()) {
        int i = ch - 'a';
        if (cur.child[i] == null) cur.child[i] = new TrieNode();
        cur = cur.child[i];
    }
    cur.end = true;
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
| Time | O(L) per insert/search, where L is word length |
| Extra space | O(total characters) in the worst case |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting terminal markers.\n- Assuming every input is lowercase English letters when it is not.\n- Using a huge child array when the alphabet is sparse.

---

## 10. Real interview / real-world examples

- Search autocomplete.\n- Phone keyboard suggestions.\n- Spell checking.\n- Prefix filtering of product names.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Longest Common Prefix; roadmap Trie.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Trie**?

Write your answer here:

> 

