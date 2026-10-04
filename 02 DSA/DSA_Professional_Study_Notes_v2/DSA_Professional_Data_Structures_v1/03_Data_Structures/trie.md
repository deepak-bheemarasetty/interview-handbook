# Trie

> **Classification:** Data Structure  
> **Category:** Prefix tree / string index  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Trie?

A trie stores strings character by character in a tree. Paths from the root represent prefixes, and terminal markers indicate complete stored words.

### The one sentence to remember

**Trie. Problems: Longest Common Prefix, Word Search II-style prefix pruning, autocomplete-style questions.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
                 root
              /    |    \
             c     d     t
             |     |     |
             a     o     h
             |     |     |
             t*    g*    e
                         |
                         n*
* = complete word
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** An autocomplete dictionary where you first choose the first letter, then the second, then the third, instead of searching every whole word.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it for prefix search, autocomplete, dictionary lookup, word replacement, and problems involving many strings sharing prefixes.

### Recognition checklist

- What operation needs to be fast?
- Do I need random/indexed access?
- Do I need key → value lookup?
- Do I need membership/duplicate checking?
- Do I need first-in-first-out or last-in-first-out behavior?
- Do I repeatedly need the smallest/largest item?
- Is the data hierarchical?
- Is the data connected by relationships?
- Do I need dynamic connectivity or range queries?

The exact questions depend on the structure, but this checklist prevents choosing a data structure just because it is familiar.

---

## 5. Why does it work?

Words with common prefixes share the same path, so prefix queries inspect only the prefix characters instead of comparing against every word.

### Core invariant / rule

Each node has links to child characters and usually a boolean `isWord` marker. A node can represent a prefix without representing a complete word.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

For alphabet size σ:
- Insert word → O(L)
- Search word → O(L)
- Prefix search → O(L)
where L = word length.
Space → O(total stored characters), with node overhead.

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Insert `cat`: create/follow c → a → t and mark t as a complete word. Insert `car`: reuse c → a, then create r. The shared `ca` prefix is stored once.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
class TrieNode {
    TrieNode[] child = new TrieNode[26];
    boolean isWord;
}

class Trie {
    TrieNode root = new TrieNode();

    void insert(String s) {
        TrieNode cur = root;
        for (char c : s.toCharArray()) {
            int i = c - 'a';
            if (cur.child[i] == null) {
                cur.child[i] = new TrieNode();
            }
            cur = cur.child[i];
        }
        cur.isWord = true;
    }
}
```

### Code walkthrough

1. Identify the object/array/node that stores the actual data.
2. Identify the references/indexes that connect or organize the data.
3. Identify the operation being performed.
4. Check which invariant must remain true.
5. Check whether Java's built-in implementation already provides the required behavior.

For interviews, you should understand both the **concept** and the Java API commonly used for it.

---

## 9. Complexity

**Insert/search/prefix:** O(L), where L is the word/prefix length. **Space:** proportional to stored characters, potentially large because each node can contain many child references.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Forgetting `isWord`; a prefix is not necessarily a complete word.
- Assuming every character is lowercase English.
- Using a huge fixed child array when the alphabet is large and sparse.

### Always test

- Empty structure
- One element
- Duplicate values
- Minimum/maximum values
- Removing the first/last element
- Removing a missing element
- Very large input
- Null references where applicable

---

## 11. Real-world applications

- Search autocomplete.
- Dictionary and spell-check systems.
- IP routing concepts use related prefix structures.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Implement insert/search/startsWith and explain why complexity depends on word length, not number of stored words.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Trie vs HashSet:** HashSet is excellent for whole-word membership; Trie naturally supports prefix queries.
- **Trie vs sorting:** sorting can answer some prefix tasks, but Trie gives direct character-by-character navigation.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Trie solve?
2. What is its core invariant?
3. What are its main operations?
4. Why is each operation fast or slow?
5. What is the time complexity?
6. What is the space complexity?
7. When would you choose it over another structure?
8. What happens on empty input?
9. Can you implement the basic version in Java?
10. Can you recognize a problem that needs it from the wording alone?

### Mastery test

**Trie. Problems: Longest Common Prefix, Word Search II-style prefix pruning, autocomplete-style questions.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
