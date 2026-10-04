# ArrayList / Dynamic Array

> **Classification:** Data Structure  
> **Category:** Java collection / dynamic array  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is ArrayList / Dynamic Array?

ArrayList is Java's resizable-array implementation of the List interface. It provides indexed access like an array while automatically managing a larger backing array when capacity is exceeded.

### The one sentence to remember

**Java Collections / Array Fundamentals. Useful across almost every problem involving a dynamic list.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
ArrayList
size = 4, capacity >= 4

[10][20][30][40]
  0   1   2   3

append -> usually O(1)
resize -> copy elements -> O(n) occasionally
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A row of lockers with a maintenance team that can add a longer row when the current row becomes full. Most additions are cheap, but occasionally the entire row must be moved to a larger location.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when you need a general-purpose ordered collection with frequent reads by index and additions at the end. It is usually a better default than LinkedList when random access matters.

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

The backing array gives fast index access. When capacity is exhausted, Java allocates a larger backing array and copies the old elements. Because resizing is occasional, append is amortized O(1).

### Core invariant / rule

The list preserves insertion order and maintains a `size` distinct from its backing-array capacity. Indexes range from `0` to `size-1`.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- `get(i)` → O(1)
- `set(i,x)` → O(1)
- `add(x)` at end → amortized O(1)
- `add(i,x)` in middle → O(n)
- `remove(i)` → O(n) in general
- `contains(x)` → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Suppose capacity is currently full. Adding one more element may allocate a larger backing array and copy all existing elements. That operation is O(n), but it does not happen on every `add`, so append is amortized O(1).

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
import java.util.ArrayList;
import java.util.List;

List<Integer> list = new ArrayList<>();

list.add(10);
list.add(20);
list.add(30);

int x = list.get(1); // 20
list.set(1, 25);     // [10,25,30]
list.remove(0);      // [25,30]
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

**get/set:** O(1). **append:** amortized O(1). **middle insertion/removal:** O(n). **Search:** O(n). **Space:** O(n), including capacity overhead.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Assuming `remove(1)` removes the value 1; for `List<Integer>`, `remove(1)` removes index 1.
- Treating `ArrayList` as O(1) for arbitrary middle insertion.
- Modifying a list while iterating incorrectly.

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

- Dynamic lists of UI items.
- API response collections.
- Buffers where items are usually appended and occasionally removed.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Know why `get` is O(1), why append is amortized O(1), and why middle insertion is O(n).

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **ArrayList vs LinkedList:** ArrayList usually wins for indexed access and typical append-heavy workloads.
- **ArrayList vs Array:** ArrayList grows automatically but has object/API overhead.
- **ArrayList vs HashSet:** ArrayList preserves order and allows duplicates; HashSet emphasizes membership/uniqueness.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does ArrayList / Dynamic Array solve?
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

**Java Collections / Array Fundamentals. Useful across almost every problem involving a dynamic list.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
