# Array

> **Classification:** Data Structure  
> **Category:** Linear / contiguous  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Array?

An array stores elements in indexed positions in contiguous logical storage. Its biggest strength is direct random access: given index `i`, the element can be reached without scanning all earlier elements.

### The one sentence to remember

**Array Fundamentals, Two Pointer, Sliding Window, Intervals, Prefix/Suffix, Kadane. Problems: Two Sum, Maximum Subarray, Product of Array Except Self, Merge Intervals.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
index:    0     1     2     3
          +-----+-----+-----+-----+
array:    |  10 |  20 |  30 |  40 |
          +-----+-----+-----+-----+
             ↑
          a[0] = 10

Access a[2] -> 30 in O(1)
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A row of numbered lockers. If locker 37 is requested, you can go directly to locker 37. But inserting a new locker in the middle means shifting later lockers.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it when you need frequent indexed access, sequential scans, in-place transformations, prefix/suffix processing, or fixed-size storage. It is the foundation for many array patterns such as two pointers, sliding window, prefix sum, and Kadane.

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

The elements are organized by index. Because the location of an element is determined directly from its index, random access is O(1). The trade-off is that insertion/deletion in the middle usually requires shifting elements.

### Core invariant / rule

The central invariant is the relationship between valid indexes and the stored elements: for length `n`, valid indexes are `0 ... n-1`. A Java array also has fixed length after creation.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- `a[i]`: access → O(1)
- Traverse → O(n)
- Search unsorted → O(n)
- Update by index → O(1)
- Insert/delete at end of a fixed array → depends on available space
- Insert/delete in the middle → O(n) because elements may shift

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

For `[10,20,30,40]`, reverse starts with indexes 0 and 3. Swap 10/40 → `[40,20,30,10]`. Then swap indexes 1 and 2 → `[40,30,20,10]`. No extra array is needed.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
int[] a = {10, 20, 30, 40};

System.out.println(a[2]); // 30

// In-place reverse
int left = 0, right = a.length - 1;
while (left < right) {
    int temp = a[left];
    a[left] = a[right];
    a[right] = temp;
    left++;
    right--;
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

**Access:** O(1). **Search:** O(n) unless sorted and a suitable search algorithm is used. **Traversal:** O(n). **In-place reverse:** O(n) time, O(1) auxiliary space.

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Confusing length `n` with last index `n-1`.
- Accessing `a[n]`.
- Forgetting that Java arrays have fixed length.
- Using O(n) extra arrays when an in-place solution is expected.

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

- Sensor readings indexed by time.
- Marks stored by student index.
- Image pixels represented in rows/columns.
- Lookup tables where an integer index identifies an item.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Be able to explain why `a[i]` is O(1), reverse an array in-place, and choose an array whenever indexed access dominates.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Array vs Linked List:** arrays give O(1) index access; linked lists require traversal.
- **Array vs HashMap:** arrays use numeric indexes; maps use keys.
- **Array vs ArrayList:** ArrayList is a resizable Java collection built around array-like storage.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Array solve?
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

**Array Fundamentals, Two Pointer, Sliding Window, Intervals, Prefix/Suffix, Kadane. Problems: Two Sum, Maximum Subarray, Product of Array Except Self, Merge Intervals.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
