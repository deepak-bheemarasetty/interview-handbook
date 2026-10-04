# HashMap

> **Classification:** Data Structure  
> **Category:** Hash table / key-value  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is HashMap?

HashMap stores key-value pairs and uses hashing to locate a key's bucket. Under normal conditions it provides expected O(1) insertion, lookup, and deletion.

### The one sentence to remember

**Hashing. Problems: Two Sum, Subarray Sum Equals K, Valid Anagram, Group Anagrams, Majority Element.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
HashMap
key       value
"apple" -> 3
"banana"-> 7
"orange"-> 2

hash(key) -> bucket -> entry
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A dictionary with labeled drawers. Instead of checking every word to find 'apple', a rule maps the word to the drawer where it should be stored.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Think of it when a problem asks for frequency, lookup by a value/key, complement lookup, grouping, or remembering the index/answer associated with an item.

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

Hashing converts a key into a bucket location. Collisions are handled internally. The structure avoids scanning all stored elements for most lookups.

### Core invariant / rule

Keys are unique within the map. A new `put` for an existing key replaces its old value. Correct key equality and hashing are essential.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- `put` → expected O(1)
- `get` → expected O(1)
- `containsKey` → expected O(1)
- `remove` → expected O(1)
- Iterate all entries → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Read `2`: map has no 2 → store 1. Read another 2 → get 1 and store 2. Continue → final count for 2 is 3.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
import java.util.HashMap;
import java.util.Map;

Map<Integer, Integer> freq = new HashMap<>();

for (int x : new int[]{2, 2, 3, 2}) {
    freq.put(x, freq.getOrDefault(x, 0) + 1);
}

System.out.println(freq.get(2)); // 3
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

**Expected:** O(1) put/get/remove. **Worst-case details:** depend on collisions and implementation. **Space:** O(n).

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Assuming HashMap keeps sorted order.
- Forgetting `getOrDefault` or null handling.
- Using mutable objects as keys without understanding equals/hashCode.
- Saying O(1) is guaranteed in every theoretical situation.

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

- Caching database results by ID.
- Counting events by type.
- Mapping user IDs to profiles.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Solve Two Sum with a map, build frequency maps, and explain why lookup is expected O(1).

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **HashMap vs TreeMap:** HashMap expected O(1); TreeMap keeps sorted keys with O(log n) operations.
- **HashMap vs HashSet:** HashMap stores key-value pairs; HashSet stores membership keys.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does HashMap solve?
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

**Hashing. Problems: Two Sum, Subarray Sum Equals K, Valid Anagram, Group Anagrams, Majority Element.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
