
## Overview

`HashMap` is a hash-table based implementation of the `Map` interface. It permits `null` keys and values and does not guarantee insertion order.

## Why It Exists

It provides fast key-based lookup, insertion, and removal when keys are well distributed across buckets.

## Internal Structure

`HashMap` stores entries in an internal bucket array.

| Property | Detail |
|----------|--------|
| Buckets | Array of table slots |
| Entry | `hash`, `key`, `value`, `next` |
| Collision handling | Linked list, then Red-Black Tree in Java 8+ |
| Ordering | None guaranteed |

## How Bucket Selection Works

The bucket index is computed with:

```java
index = (n - 1) & hash
```

where `n` is the table capacity.

## Resize vs Rehash

### Resizing

When the load factor threshold is exceeded, the table grows, typically by doubling the capacity.

### Rehashing

Entries are redistributed into the new bucket array because the bucket index changes with the new capacity.

## Collision Handling

When multiple keys map to the same bucket, `HashMap` chains entries together. In Java 8+, heavily contended buckets can treeify into a Red-Black Tree.

## Key Contract

`hashCode()` narrows the search to the correct bucket, while `equals()` determines actual key equality.

## Trade-offs

- Pros: fast average-case lookup, flexible key-value storage
- Cons: no ordering guarantee, worst-case behavior can degrade under heavy collisions

## When to Use

- Fast lookup tables
- Caches
- Configuration maps
- Any case where ordering is not required

## Interview Takeaway

If asked how `HashMap` works internally, explain bucket placement, collision handling, resizing, and the `hashCode()` / `equals()` contract.

## Common Mistakes [[Mistakes Log#HashMap]]

- Hashing converts an object into a hash code
- Buckets store hash codes
- Bucket index is simply based on the hash code
- `hashCode()` decides equality
- Rehashing recalculates every key's hash code

