# Backtracking

> **Classification:** Pattern / problem-solving strategy  
> **Purpose:** A controlled search pattern that builds a solution one decision at a time, recursively explores it, and undoes the decision before trying another.

---

## 1. Learn this first — in one minute

### What is Backtracking?

A controlled search pattern that builds a solution one decision at a time, recursively explores it, and undoes the decision before trying another.

### Real-world analogy

Trying keys on a keyring: test one key, if it fails continue; if it opens one door but leads to a dead end, come back and try another branch.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
                []
          /       |       \
        [1]      [2]      [3]
       /   \      ...
    [1,2] [1,3]

choose -> explore -> undo -> next choice
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Generate all subsets/permutations/combinations; maze paths; N-Queens; constraint satisfaction.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

The answer space is a decision tree. Backtracking makes one choice, recursively solves the smaller decision problem, then restores the state so the next branch starts cleanly.

---

## 5. Step-by-step method

1. Define the current partial solution. 2. Choose a candidate. 3. Apply it. 4. Recurse. 5. Undo it. 6. Prune immediately when constraints are violated.

---

## 6. Small example / dry run

For subsets `[1,2]`: start `[]`; choose 1 → `[1]`; choose 2 → `[1,2]`; undo 2 → `[1]`; undo 1 → `[]`; then choose 2 → `[2]`.

---

## 7. Java implementation

```java
void dfs(int start, List<Integer> path) {
    result.add(new ArrayList<>(path));

    for (int i = start; i < nums.length; i++) {
        path.add(nums[i]);       // choose
        dfs(i + 1, path);        // explore
        path.remove(path.size()-1); // undo
    }
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
| Time | Usually exponential; depends on number of generated states |
| Extra space | O(depth) recursion plus output |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Forgetting the undo step.\n- Sharing mutable lists in the answer.\n- Missing pruning.\n- Reusing elements when the problem says each can be used once.

---

## 10. Real interview / real-world examples

- Choosing seats for a group under restrictions.\n- Generating passwords from allowed characters.\n- Finding routes through a maze.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Subsets, Permutations, Combination Sum.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Backtracking**?

Write your answer here:

> 

