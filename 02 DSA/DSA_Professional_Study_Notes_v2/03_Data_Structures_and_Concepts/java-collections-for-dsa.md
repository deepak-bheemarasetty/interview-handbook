# Java Collections for DSA

> **Classification:** Data structure / supporting concept (not a pattern or algorithm)  
> **Purpose:** A practical map of common Java collection choices for DSA: ArrayList, LinkedList, HashMap, HashSet, ArrayDeque, PriorityQueue, TreeMap, TreeSet.

---

## 1. Learn this first — in one minute

### What is Java Collections for DSA?

A practical map of common Java collection choices for DSA: ArrayList, LinkedList, HashMap, HashSet, ArrayDeque, PriorityQueue, TreeMap, TreeSet.

### Real-world analogy

Different containers in a kitchen: choose a tray for indexed access, a basket for fast lookup, a priority tray for the next most urgent item.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Need...                Choose...
index access            ArrayList
key -> value             HashMap
membership               HashSet
LIFO/FIFO                ArrayDeque
min/max priority         PriorityQueue
sorted keys              TreeMap/TreeSet
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Choosing the right Java structure is part of solving the algorithm, not an afterthought.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The data structure determines which operations are cheap. Match the required operation to the structure rather than choosing one container for everything.

---

## 5. Step-by-step method

Ask: need index? key lookup? sorted order? FIFO/LIFO? min/max? Then choose the narrowest suitable structure.

---

## 6. Small example / dry run

Two Sum needs key lookup → HashMap. BFS needs FIFO → Queue/ArrayDeque. Dijkstra needs minimum distance → PriorityQueue.

---

## 7. Java implementation

```java
List<Integer> list = new ArrayList<>();
Map<Integer,Integer> map = new HashMap<>();
Set<Integer> set = new HashSet<>();
Deque<Integer> deque = new ArrayDeque<>();
PriorityQueue<Integer> heap = new PriorityQueue<>();
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
| Time | Depends on collection |
| Extra space | Depends on collection |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Using LinkedList for random access.\n- Using TreeMap when hashing is sufficient.\n- Forgetting PriorityQueue's default min-heap behavior.

---

## 10. Real interview / real-world examples

- Selecting tools based on required operations in real software systems.

---

## 11. Problems from your roadmap that connect to this

Roadmap Foundations: Java collections.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Java Collections for DSA**?

Write your answer here:

> 

