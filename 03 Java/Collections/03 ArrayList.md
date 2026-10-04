
## Overview

`ArrayList` is a resizable-array implementation of the `List` interface.

## Why It Exists

It provides fast indexed access while still letting the list grow dynamically as elements are added.

## Internal Structure

`ArrayList` stores elements in a contiguous internal array.

| Property | Detail |
|----------|--------|
| Access | Fast random access by index |
| Insertion | Efficient at the end, slower in the middle |
| Removal | Can require shifting elements |
| Memory layout | Contiguous |

## Why It Feels Fast in Practice

Contiguous storage gives strong CPU cache locality, so iteration is usually very fast compared to node-based structures.

## Trade-offs

- Pros: fast indexed reads, simple structure, cache-friendly iteration
- Cons: insertions and removals in the middle require shifting

## When to Use

- When you need frequent random access
- When iteration is common
- When insertion/removal mostly happens at the end

## Interview Takeaway

If asked why `ArrayList` often outperforms `LinkedList`, say that it stores elements contiguously in memory, which improves cache locality and makes iteration cheaper in practice.

## Common Mistakes [[Mistakes Log#ArrayList]]

- Assuming `LinkedList` is faster for general use because insertions are O(1)
- Ignoring the cost of shifting elements in the middle of the list
