# Top K Frequent Elements

> **Classification:** Algorithm  
> **Purpose:** Finds the K most frequent values using a frequency map plus heap or bucket technique.

---

## 1. Learn this first — in one minute

### What is Top K Frequent Elements?

Finds the K most frequent values using a frequency map plus heap or bucket technique.

### Real-world analogy

A music app wants the 10 most played songs. Count plays, then keep only the strongest 10 candidates.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
values: 1 1 1 2 2 3
freq:
1 -> 3
2 -> 2
3 -> 1

top 2 => 1,2
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Frequency + top K.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Separate the problem into two tasks: count occurrences, then select the K largest frequencies.

---

## 5. Step-by-step method

Build frequency map. Use size-K min-heap or buckets indexed by frequency.

---

## 6. Small example / dry run

Counts 1=3, 2=2, 3=1. For K=2, select 1 and 2.

---

## 7. Java implementation

```java
Map<Integer,Integer> freq = new HashMap<>();
for (int x : nums)
    freq.put(x, freq.getOrDefault(x,0)+1);

PriorityQueue<Integer> pq =
    new PriorityQueue<>(Comparator.comparingInt(freq::get));

for (int x : freq.keySet()) {
    pq.offer(x);
    if (pq.size() > k) pq.poll();
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
| Time | O(n log k) with heap; O(n) average with bucket approach |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Sorting the whole map unnecessarily when K is small.\n- Forgetting ties may have multiple valid outputs depending on problem.

---

## 10. Real interview / real-world examples

- Most searched queries.\n- Most frequent error codes.\n- Most popular products.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Top K Frequent Elements.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Top K Frequent Elements**?

Write your answer here:

> 

