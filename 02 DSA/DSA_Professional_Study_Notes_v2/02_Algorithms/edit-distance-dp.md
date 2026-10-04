# Edit Distance DP

> **Classification:** Algorithm  
> **Purpose:** Computes the minimum insertions, deletions, and substitutions needed to transform one string into another.

---

## 1. Learn this first — in one minute

### What is Edit Distance DP?

Computes the minimum insertions, deletions, and substitutions needed to transform one string into another.

### Real-world analogy

Editing a document: at each character mismatch, either delete, insert, or replace one character.

If the analogy makes sense, the code becomes much easier to remember: **the code is only implementing the same idea on data.**

---

## 2. Visual picture

```text
        "" C A T
     0  1 2 3
 ""  0  1 2 3
 C   1  0 1 2
 C A 2  1 0 1
 C T 3  2 1 1

dp[i][j] = min edit operations
```

Read the picture from left to right / top to bottom before reading the code.

---

## 3. When should I think of this?

Convert one string to another; minimum edits; spelling correction.

### Recognition questions

- What structure does the input have?
- What information is being repeated unnecessarily?
- Is the problem asking for a **minimum, maximum, count, existence, ordering, connectivity, or shortest path**?
- Can I maintain an invariant while scanning instead of recomputing everything?
- What are the constraints? A correct idea can still time out if its complexity is too high.

---

## 4. Intuition — why does it work?

For prefixes ending at i,j: if characters match, no new edit is needed; otherwise choose the cheapest of delete, insert, replace.

---

## 5. Step-by-step method

Initialize empty-prefix distances. Fill table. Match → diagonal; mismatch → 1 + min(top, left, diagonal).

---

## 6. Small example / dry run

Transform `cat` to `cut`: c matches, a→u is one replacement, t matches → distance 1.

---

## 7. Java implementation

```java
int n=a.length(), m=b.length();
int[][] dp=new int[n+1][m+1];

for(int i=0;i<=n;i++) dp[i][0]=i;
for(int j=0;j<=m;j++) dp[0][j]=j;

for(int i=1;i<=n;i++){
    for(int j=1;j<=m;j++){
        if(a.charAt(i-1)==b.charAt(j-1))
            dp[i][j]=dp[i-1][j-1];
        else
            dp[i][j]=1+Math.min(
                dp[i-1][j-1],
                Math.min(dp[i-1][j], dp[i][j-1])
            );
    }
}
return dp[n][m];
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
| Time | O(nm) |
| Extra space | O(nm), reducible to O(m) |

Do not memorize the complexity alone. Know **where that complexity comes from**.

---

## 9. Common mistakes

- Wrong base rows/columns.\n- Confusing insertion/deletion direction.

---

## 10. Real interview / real-world examples

- Spell correction.\n- Comparing versions of text.\n- Approximate string matching.

---

## 11. Problems from your roadmap that connect to this

Problem Bank: Edit Distance.

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

**Without looking above:** If you were given a new problem tomorrow, what exact words or structure would make you consider **Edit Distance DP**?

Write your answer here:

> 

