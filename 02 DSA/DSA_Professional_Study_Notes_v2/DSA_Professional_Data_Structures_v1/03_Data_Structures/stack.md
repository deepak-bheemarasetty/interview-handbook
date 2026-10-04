# Stack

> **Classification:** Data Structure  
> **Category:** Linear / LIFO  
> **Roadmap source:** DSA Professional Striver Roadmap — Data Structure topics

---

## 1. Learn this first — in one minute

### What is Stack?

A stack is a Last-In-First-Out structure. The most recently inserted item is the first item removed.

### The one sentence to remember

**Stack. Problems: Valid Parentheses, Next Greater Element, Daily Temperatures, Largest Rectangle in Histogram.**

### Why do we need it?

The choice of data structure changes what operations are cheap. In DSA, the goal is not to memorize every structure; it is to recognize **what information must be stored and which operation must be fast**.

---

## 2. Visual picture

```text
        TOP
         |
       +---+
       | C | <- pop first
       +---+
       | B |
       +---+
       | A |
       +---+
```

Read the picture slowly. The arrows, indexes, links, priorities, or hierarchy are the important part of the structure.

---

## 3. Real-world analogy

**Think of it like this:** A stack of plates. You normally put a plate on top and take the top plate first.

The analogy is useful because it maps the abstract structure to something you already understand. When solving a problem, ask: **"What real-world storage behavior does this problem resemble?"**

---

## 4. When should I think of this?

Use it for nested structures, undo behavior, expression parsing, bracket matching, DFS implementations, and monotonic-stack problems.

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

LIFO naturally models 'most recent unresolved item'. Nested brackets are a classic example: the latest opening bracket must be matched first.

### Core invariant / rule

Only the top is directly accessible. Valid stack operations preserve the top-based access rule.

If an operation would break this rule, the implementation must restore the invariant before continuing.

---

## 6. Main operations

- push → O(1)
- pop → O(1)
- peek → O(1)
- isEmpty → O(1)
- search arbitrary element → O(n)

When learning a data structure, do not only memorize operation names. Know **what happens internally** and **why the complexity has that value**.

---

## 7. Step-by-step example

### Example

Push 10, then 20, then 30. The top is 30. Pop removes 30 first, then 20, then 10.

### What happened?

The important lesson is that the structure did not magically make the operation fast. Its organization of data is what allowed the operation to avoid unnecessary work.

---

## 8. Java implementation

```java
import java.util.ArrayDeque;
import java.util.Deque;

Deque<Integer> stack = new ArrayDeque<>();

stack.push(10);
stack.push(20);
stack.push(30);

System.out.println(stack.pop());  // 30
System.out.println(stack.peek()); // 20
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

**Push/pop/peek:** O(1). **Space:** O(n).

### Complexity intuition

A complexity number is more useful when you know **what causes it**. For example, direct array indexing is fast because the address can be calculated immediately; linked-list indexing is slow because nodes must be followed one by one.

---

## 10. Common mistakes and edge cases

- Popping an empty stack.
- Using the wrong end of a Deque.
- Confusing LIFO with FIFO.
- Using `Stack` without understanding that `ArrayDeque` is generally preferred for stack behavior in modern Java.

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

- Undo operations.
- Function-call/call-stack behavior.
- Browser navigation history conceptually.
- Parsing nested expressions.

A data structure is useful in real software only when its operation model matches the application's needs.

---

## 12. Data-structure comparison

- Implement bracket matching and explain why the latest opening bracket must be handled first.

### Interview rule

Do not answer **"HashMap is always better"**, **"ArrayList is always better"**, etc. The correct choice depends on the operations and constraints.

---

## 13. Problems from your roadmap that connect to this

- **Stack vs Queue:** LIFO vs FIFO.
- **Stack vs Deque:** a deque supports both ends; it can implement a stack.

These are the places in your workbook where this data structure is directly or indirectly relevant.

---

## 14. How to know you actually learned it

You should be able to answer all of these **without looking at the document**:

1. What problem does Stack solve?
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

**Stack. Problems: Valid Parentheses, Next Greater Element, Daily Temperatures, Largest Rectangle in Histogram.**

If you cannot explain the answer in your own words, mark this topic **Learning**, not **Mastered**.
