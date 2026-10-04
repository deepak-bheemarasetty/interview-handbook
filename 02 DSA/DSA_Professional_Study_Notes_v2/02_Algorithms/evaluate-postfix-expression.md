# Evaluate Postfix Expression

> **Classification:** Algorithm  
> **Purpose:** Evaluates an expression where each operator comes after its operands using a stack.

---

## 1. Learn this first — in one minute

### What is Evaluate Postfix Expression?

Evaluates an expression where each operator comes after its operands using a stack.

### Real-world analogy

A calculator that stores numbers until an operator tells you to combine the most recent two.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
tokens: 2  3  +  4  *
stack:  [2]
        [2,3]
+ -> [5]
        [5,4]
* -> [20]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Reverse Polish/postfix notation; expression evaluation.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

Operators always apply to the two most recent operands, so LIFO is exactly what is needed.

---

## 5. Step-by-step method

Push numbers. On operator, pop right operand then left operand, compute, push result. Final stack value is answer.

---

## 6. Small example / dry run

`2 3 + 4 *`: push 2,3; + gives 5; push 4; * gives 20.

---

## 7. Java implementation

```java
Deque<Integer> st = new ArrayDeque<>();

for (String token : tokens) {
    if (!isOperator(token)) {
        st.push(Integer.parseInt(token));
    } else {
        int b = st.pop();
        int a = st.pop();

        int value = switch (token) {
            case "+" -> a + b;
            case "-" -> a - b;
            case "*" -> a * b;
            default -> a / b;
        };
        st.push(value);
    }
}
return st.pop();
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

- Reversing operands for subtraction/division.\n- Parsing operators as numbers.

---

## 10. Real interview / real-world examples

- Compiler/interpreter expression evaluation.\n- Stack-machine calculators.

---

## 11. Problems from your roadmap that connect to this

Roadmap Stack expression problems.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Evaluate Postfix Expression**?

Write your answer here:

> 

