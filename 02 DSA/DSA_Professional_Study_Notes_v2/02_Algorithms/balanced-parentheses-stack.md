# Balanced Parentheses Stack

> **Classification:** Algorithm  
> **Purpose:** Uses a stack to verify that closing brackets match the most recent unmatched opening bracket.

---

## 1. Learn this first — in one minute

### What is Balanced Parentheses Stack?

Uses a stack to verify that closing brackets match the most recent unmatched opening bracket.

### Real-world analogy

Nested boxes: the last box opened must be the first box closed.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
Input: {[()]}
stack:
{ 
{[
{[( 
{[
{
empty ✓
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Parentheses/brackets; nested structure; matching open/close symbols.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Nesting is last-in-first-out, exactly the behavior of a stack.

---

## 5. Step-by-step method

Push opening brackets. On closing bracket, stack must be nonempty and top must match. At end stack must be empty.

---

## 6. Small example / dry run

For `{[()]}`, every closing bracket matches the latest opener. For `{[(])}`, `]` expects `[` but top is `(` → invalid.

---

## 7. Java implementation

```java
Deque<Character> st = new ArrayDeque<>();

for (char c : s.toCharArray()) {
    if (c == '(' || c == '[' || c == '{') {
        st.push(c);
    } else {
        if (st.isEmpty()) return false;
        char open = st.pop();
        if ((c == ')' && open != '(') ||
            (c == ']' && open != '[') ||
            (c == '}' && open != '{'))
            return false;
    }
}
return st.isEmpty();
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
| Time | O(n) |
| Extra space | O(n) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Not checking empty stack before pop.\n- Forgetting final emptiness.

---

## 10. Real interview / real-world examples

- Compiler syntax checking.\n- HTML/XML nesting conceptually.\n- Expression parsing.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Valid Parentheses.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Balanced Parentheses Stack**?

Write your answer here:

> 

