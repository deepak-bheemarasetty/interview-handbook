
## Overview

`TreeMap` is a Red-Black Tree based `NavigableMap` implementation. It sorts keys according to their natural ordering or a supplied `Comparator`.

## Why It Exists

It provides ordered key storage when sorted traversal, range queries, or navigation helpers are required.

## Internal Structure

`TreeMap` stores entries in a self-balancing Red-Black Tree.

| Property | Detail |
|----------|--------|
| Backing structure | Red-Black Tree |
| Ordering | Natural order or `Comparator` |
| Key uniqueness | Determined by comparison, not `equals()` |
| Complexity | `O(log n)` for core operations |

## How Ordering Works

Insertion follows BST ordering rules:

```text
left < root < right
```

Then the tree rebalances to preserve Red-Black Tree properties.

## BST vs Red-Black Tree

### Binary Search Tree

Maintains ordering using the `left < root < right` rule.

### Red-Black Tree

A self-balancing Binary Search Tree that adds balancing rules to keep the height close to `O(log n)`.

## Why It Is Slower Than HashMap

`TreeMap` performs tree traversal on each core operation, so `put()`, `get()`, `remove()`, and `containsKey()` are all `O(log n)` instead of average-case `O(1)`.

## Trade-offs

- Pros: sorted keys, range queries, ceiling/floor lookups, ordered navigation
- Cons: slower than `HashMap` for basic key lookup

## When to Use

- When sorted order matters
- When range-based queries are needed
- When you need navigation helpers like `ceilingKey()` or `floorKey()`

## Interview Takeaway

If asked how `TreeMap` keeps keys sorted, explain that each insertion follows BST rules and the tree rebalances afterward. If asked why it is slower than `HashMap`, point to the `O(log n)` tree traversal.

## Common Mistakes [[Mistakes Log#TreeMap]]

- TreeMap inserts keys into a sorted position
- Red-Black Tree ordering is the same thing as BST ordering
- TreeMap is just a sorted HashMap
- TreeMap uses `equals()` to determine uniqueness

## Modeling Insight

`TreeMap` orders by **keys**, so the key should represent the field you want to sort or range-query on.

If the business question is based on expiry time, expiry should be the key:

```java
TreeMap<ExpiryTime, Set<Token>>
```

If the key is wrong, the data structure may still store the data, but it will not answer the query efficiently.

## Collection Selection Insight

Choose `TreeMap` when the requirement is ordered access over the primary query key.

Typical signals:

- range queries
- ceiling/floor lookups
- sorted traversal
- nearest-key behavior

If the main query dimension is not the key, consider using a different structure or maintaining an additional index.
