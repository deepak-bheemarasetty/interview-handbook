# HashSet

> **Classification:** Data Structure  
> **Category:** Hash table / unique membership  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is HashSet?

HashSet stores unique elements and is optimized for membership testing, insertion, and deletion using hashing.

### The one sentence to remember

**Hashing. Problems: Longest Consecutive Sequence, duplicate detection, graph visited sets.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
HashSet
+---------+
| apple   |
| banana  |
| mango   |
+---------+

"banana" -> already present
"grape"  -> absent
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A guest list where each person's name can appear only once. To check whether someone has already entered, you look them up instead of scanning the entire list.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it for duplicate detection, membership, visited values, and problems where you need to know whether something has appeared before.

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

The set cares about whether a value exists, not about an associated value. Hashing makes expected membership checks fast.

### Core invariant / rule

Each element is unique according to `equals`/`hashCode`. Order is not guaranteed by HashSet.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- `add` → expected O(1)
- `contains` → expected O(1)
- `remove` → expected O(1)
- size → O(1)
- iteration → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

The first 4 is added. When the second 4 arrives, `add(4)` returns false because 4 already exists. That makes duplicate detection concise.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
import java.util.HashSet;
import java.util.Set;

Set<Integer> seen = new HashSet<>();

for (int x : new int[]{4, 7, 4}) {
    if (!seen.add(x)) {
        System.out.println("Duplicate: " + x);
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

**Expected:** O(1) add/contains/remove. **Space:** O(n).

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Expecting sorted order.
- Using a set when you actually need counts; use HashMap for frequencies.
- Forgetting that uniqueness follows equality/hashCode.

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

- Unique visitor tracking.
- Duplicate transaction detection.
- Visited nodes in graph traversal.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Explain why `add` returning false detects duplicates and solve Longest Consecutive Sequence.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **HashSet vs HashMap:** use HashSet for membership; HashMap for key→value relationships.
- **HashSet vs TreeSet:** TreeSet maintains sorted order but operations are O(log n).

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does HashSet solve?
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

**Hashing. Problems: Longest Consecutive Sequence, duplicate detection, graph visited sets.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
