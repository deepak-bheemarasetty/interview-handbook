
## Overview

`HashSet` is a `Set` implementation backed by a `HashMap`.

## Why It Exists

It provides fast membership checks and enforces uniqueness without requiring you to manage the backing structure directly.

## Internal Structure

Each set element is stored as a key in an internal `HashMap`, and the value is a private sentinel object.

| Property | Detail |
|----------|--------|
| Backing store | `HashMap` |
| Stored as | Key only |
| Value used | Private sentinel (`PRESENT`) |
| Ordering | None guaranteed |

## How `add()` Works

Internally, `HashSet.add(e)` behaves like:

```java
map.put(e, PRESENT) == null
```

The sentinel value allows `HashSet` to distinguish a new insertion from an element that already existed.

## Why the Sentinel Is Needed

`HashMap` allows `null` values, so using `null` as the backing value would make it impossible to tell whether:

- the element was newly inserted
- the element already existed with a `null` value
---
## Design Note: `HashSet` vs `Map.keySet()`

Although `HashSet` is internally backed by a `HashMap`, it should **not** be replaced by `HashMap.keySet()`.

### Why?

`HashMap.keySet()` returns a **live view** of an existing map's keys. It does not represent an independent `Set`; any modifications to the map are immediately reflected in the returned set and vice versa.

Using `HashMap<String, Boolean>` (or a dummy value) also exposes an implementation detail and forces callers to work with meaningless values when the business requirement is simply to store unique elements.

```java
// ❌ Avoid
Map<String, Boolean> map = new HashMap<>();
Set<String> set = map.keySet();
```

Instead, use the abstraction that matches the business requirement.

```java
// ✅ Preferred
Set<String> set = new HashSet<>();
```

### Concurrent Alternative

For thread-safe scenarios, prefer:

```java
Set<String> set = ConcurrentHashMap.newKeySet();
```

This creates a true concurrent `Set` backed internally by a `ConcurrentHashMap` without exposing the underlying map or requiring dummy values.

### Interview Insight

**Program to the abstraction, not the implementation.**

- Use **`HashSet`** when the requirement is to store unique elements.
- Use **`ConcurrentHashMap.newKeySet()`** when you need a thread-safe set.
- Avoid exposing a `Map` when the domain model is conceptually a `Set`.

## Collection Selection Insight

Choose `HashSet` based on the query pattern, not just because it is O(1) on paper.

Use it when:

- uniqueness matters
- ordering does not matter
- membership checks dominate

If the requirement changes, the abstraction may need to change too.

For example:

- `HashSet` for unique elements
- `ConcurrentHashMap.newKeySet()` for a concurrent unique set
- `TreeSet` when sorted uniqueness is required

## Trade-offs

- Pros: fast membership checks, simple uniqueness enforcement
- Cons: no ordering guarantee, depends on `HashMap` behavior

## When to Use

- When you need unique elements
- When order does not matter
- When fast `contains()` checks are important

## Interview Takeaway

If asked why `HashSet` uses a dummy object, say it relies on `HashMap` as the backing store and needs a non-null sentinel so it can tell whether an element was newly added.

## Common Mistakes [[Mistakes Log#HashSet]]

- `HashSet` stores elements directly
- `HashSet` can safely use `null` as the backing value
- `HashSet.add()` just inserts a value
- `HashSet` cannot distinguish duplicates without extra state
