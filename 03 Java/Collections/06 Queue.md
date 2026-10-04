# Queue

## Overview

`Queue` is a collection used to store elements before processing them in a defined sequence.

## Why It Exists

It models ordered processing, where elements are added and removed according to a policy such as FIFO, priority order, or double-ended access.

## Internal Structure

The `Queue` interface is implemented differently depending on the required behavior.

| Variant | Behavior | Typical Implementations |
|---------|----------|-------------------------|
| FIFO Queue | First in, first out | `ArrayDeque`, `LinkedList` |
| Deque | Add/remove from both ends | `ArrayDeque`, `LinkedList` |
| Priority Queue | Process by priority | `PriorityQueue` |

## Queue Operations

`Queue` provides specialized methods that often return special values instead of throwing exceptions.

| Operation | Common Method | Meaning |
|----------|---------------|---------|
| Insert | `offer()` | Add element if possible |
| Remove | `poll()` | Remove head, or return `null` if empty |
| Inspect | `peek()` | View head, or return `null` if empty |

## Queue vs Deque

`Queue` models one-directional processing. `Deque` extends that idea to both ends.

## Common Implementations

### `ArrayDeque`

`ArrayDeque` is a resizable array-based deque. It is usually the best default choice for queue and stack style operations.

### `LinkedList`

`LinkedList` also implements `Deque`, but it uses node-based storage and pointer links.

### `PriorityQueue`

`PriorityQueue` processes elements according to priority rather than insertion order.

## ArrayDeque vs LinkedList

| Aspect | ArrayDeque | LinkedList |
|--------|------------|------------|
| Storage | Circular / resizable array | Doubly linked nodes |
| Cache locality | Better | Worse |
| Queue operations | Very efficient | Efficient |
| Stack operations | Very efficient | Possible, but not ideal |
| Middle insert/remove | Not the focus | Better suited if you already have node references |

`ArrayDeque` is usually preferred for queue and deque use cases because it has better cache locality and fewer allocation overheads.

## PriorityQueue and Heaps

`PriorityQueue` is backed by a binary heap.

### Heap Basics

- A heap is a complete binary tree
- The parent is ordered relative to its children according to the heap rule
- Java’s `PriorityQueue` uses a min-heap by default

### Important Point

`PriorityQueue` does **not** guarantee FIFO ordering for equal priorities.

## Trade-offs

- Pros: clear processing order, flexible implementation choices
- Cons: the right implementation depends on the exact access pattern

## When to Use

- Use `Queue` when elements should be processed in a defined sequence
- Use `Deque` when you need both ends
- Use `ArrayDeque` as the default for queue/deque style use cases
- Use `PriorityQueue` when priority matters more than arrival order

## Choosing the Right Queue Implementation

### `ArrayDeque`

Use when:

- FIFO or LIFO processing
- High throughput
- Single-threaded
- Fast operations at both ends

Backed by a circular, resizable array.

### `PriorityQueue`

Use when:

- Elements must be processed by priority rather than insertion order
- Frequent `peek()` and `poll()` of the highest or lowest priority element

Backed by a binary heap.

Iteration order is **not** sorted.

### `Deque`

Preferred interface for stack behavior.

Use:

- `push()`
- `pop()`
- `peek()`

instead of the legacy `Stack` class.

## Interview Takeaway

If asked how to choose between `Queue`, `Deque`, `ArrayDeque`, `LinkedList`, and `PriorityQueue`, start with the processing rule: FIFO, both ends, or priority order.

## Common Mistakes [[Mistakes Log#Queue]]

- Assuming every queue is FIFO
- Assuming `PriorityQueue` preserves insertion order for equal priorities
- Treating `ArrayDeque` and `LinkedList` as equivalent defaults
- Confusing queue order with heap order

