# Palindrome DP

> **Classification:** Algorithm  
> **Purpose:** Determines whether substrings are palindromes by using smaller inner substrings.

---

## 1. Learn this first — in one minute

### What is Palindrome DP?

Determines whether substrings are palindromes by using smaller inner substrings.

### Real-world analogy

A word is a mirror: the first and last characters must match, and the inside must also mirror.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
b a n a n a
^         ^ match
  ^     ^   match
    ^ ^     match

dp[l][r] = a[l]==a[r] && dp[l+1][r-1]
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Longest palindromic substring; count palindromic substrings; interval/string DP.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

A substring is a palindrome if its endpoints match and the substring inside them is also a palindrome.

---

## 5. Step-by-step method

Initialize length 1 as true. For increasing lengths, compare endpoints and consult inner interval. Length 2 needs special handling.

---

## 6. Small example / dry run

`aba`: endpoints a=a and inner `b` is a palindrome → true.

---

## 7. Java implementation

```java
boolean[][] dp = new boolean[n][n];
int best = 1;

for (int i=0;i<n;i++) dp[i][i]=true;

for (int len=2; len<=n; len++) {
    for (int l=0; l+len<=n; l++) {
        int r=l+len-1;
        dp[l][r] = s.charAt(l)==s.charAt(r)
                && (len==2 || dp[l+1][r-1]);
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
| Time | O(n²) |
| Extra space | O(n²) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Wrong length-2 base case.\n- Confusing substring with subsequence.

---

## 10. Real interview / real-world examples

- DNA palindrome segments.\n- Detecting mirrored identifiers.

---

## 11. Problems from your roadmap that connect to this

Roadmap Advanced DP: palindrome DP overview.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Palindrome DP**?

Write your answer here:

> 

